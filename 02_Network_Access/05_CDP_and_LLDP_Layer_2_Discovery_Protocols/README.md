# 05 — CDP & LLDP: Layer 2 Discovery Protocols

> **Track:** CCNA 200-301 | **Domain:** Network Access | **Date:** 2026-05-20  
> **Exam weight:** ~20% of exam covers Network Access — discovery protocols appear in scenario questions

---

## Protocol Reference

### CDP (Cisco Discovery Protocol)

| Parameter | Value |
|---|---|
| Standard | Cisco proprietary |
| Layer | L2 (does not require IP) |
| Multicast MAC | `01:00:0C:CC:CC:CC` |
| Advertisement interval | **60 sec** |
| Hold time | **180 sec** (3× interval) |
| Default state on IOS | **Enabled globally** |
| PDU type | CDP frames (EtherType `0x2000`) |
| Version | CDPv2 (current) — backward-compatible with v1 |

CDP runs directly over the data link layer. It has no dependency on IP addressing, which makes it functional even on unconfigured or misconfigured devices — useful for OOB troubleshooting.

### LLDP (Link Layer Discovery Protocol)

| Parameter | Value |
|---|---|
| Standard | IEEE 802.1AB-2016 |
| Layer | L2 |
| Multicast MAC | `01:80:C2:00:00:0E` |
| Advertisement interval | **30 sec** |
| Hold time | **120 sec** |
| Default state on IOS | **Disabled** — requires `lldp run` |
| PDU type | LLDPDU (EtherType `0x88CC`) |
| Info format | TLVs (Type-Length-Value) |

LLDP TX and RX are independently configurable per interface — a useful asymmetry when you need to receive neighbor info without advertising your own device details.

### What CDP Advertises (TLV fields)

```
Device ID         → hostname of the neighbor
IP Address        → Layer 3 management address
Platform          → hardware model string  e.g. cisco WS-C2960X-48FPD-L
Capabilities      → bitmask: R=Router S=Switch H=Host T=Trans Bridge
Interface         → local port + remote port
Hold Time         → TTL before entry expires
IOS Version       → full version string
Native VLAN       → 802.1Q native VLAN (critical — mismatch causes CDP log spam)
Duplex            → half / full
VTP Domain        → if VTP is running
Power (PoE)       → power draw/availability for CDP-capable phones
```

> **Native VLAN mismatch** is one of the most common issues surfaced by `show cdp neighbors detail`. If neighbors have mismatched native VLANs, CDP logs `%CDP-4-NATIVE_VLAN_MISMATCH` — fix with `switchport trunk native vlan <id>` on both ends.

---

## Operational Commands

### CDP

```ios
! Verify CDP is running and get global timers
show cdp

! One-line summary of all directly connected neighbors
show cdp neighbors

! Full TLV dump for all neighbors — gets you IOS version, IP, native VLAN, duplex
show cdp neighbors detail

! Per-interface CDP state and timer values
show cdp interface

! Detail for a single interface
show cdp interface GigabitEthernet0/1

! CDP entry for a specific neighbor by hostname
show cdp entry <device-id>

! CDP traffic counters — useful when neighbors aren't appearing
show cdp traffic
```

### LLDP

```ios
! Verify LLDP global state
show lldp

! Summary table — works across any 802.1AB-speaking vendor
show lldp neighbors

! Full TLV detail — chassis ID, management IP, port description, system capabilities
show lldp neighbors detail

! Per-interface LLDP TX/RX state
show lldp interface

! Traffic counters
show lldp traffic
```

### Reading `show cdp neighbors` output

```
Device ID    Local Intrfce  Holdtme   Capability  Platform     Port ID
R1           Gig 0/1         150         R         cisco ISR    Gig 0/0
SW2          Gig 0/2         132         S         WS-C2960X    Gig 0/1
```

Columns in order: **who they are → my port → seconds remaining → role → hardware → their port**

Hold time counts down from 180. A neighbor stuck at a static value means it's actively refreshing. A neighbor counting down to zero and disappearing means the link or CDP on that side is going down.

---

## Configuration

### CDP — enable / disable

```ios
! Global (affects all interfaces)
cdp run            ← default state, usually no need to configure
no cdp run         ← disables everywhere — use with caution in production

! Per-interface (preferred for security hardening)
interface GigabitEthernet0/5
 no cdp enable     ← disables on this port only
 cdp enable        ← re-enable if needed
```

### LLDP — enable and tune

```ios
! Enable globally (required — disabled by default)
lldp run

! Per-interface TX/RX control
interface GigabitEthernet0/1
 lldp transmit     ← send LLDP frames
 lldp receive      ← process received LLDP frames
 no lldp transmit  ← stop advertising (still listen)
 no lldp receive   ← stop processing (still send)

! Tune timers (global)
lldp timer 30          ← advertisement interval in seconds
lldp holdtime 120      ← TTL sent to neighbors
lldp reinit 2          ← delay before LLDP initializes on a newly enabled interface
```

### Adjust CDP timers (non-default)

```ios
cdp timer 60          ← advertisement interval (default 60)
cdp holdtime 180      ← hold time sent in frames (default 180)
```

---

## Security

Discovery protocols are **reconnaissance vectors**. A single CDP frame from an access port reveals:

- Exact hardware model → maps to CVE databases
- IOS version → confirms exploitable versions
- IP address → direct attack target
- Native VLAN → enables 802.1Q double-tagging / VLAN hopping

### Hardening policy

| Port type | CDP | LLDP |
|---|---|---|
| Trunk (switch–switch uplink) | ✅ Enabled | ✅ Enabled |
| Routed uplink (switch–router) | ✅ Enabled | ✅ Enabled |
| Access port (user-facing) | ❌ Disabled | ❌ Disabled |
| Internet-facing / DMZ | ❌ Disabled | ❌ Disabled |
| Server ports | ❌ Disabled | Consider RX-only |

Apply globally then carve out exceptions, or disable per-interface on access ports while leaving infrastructure ports untouched:

```ios
! Recommended approach: disable per-interface on access ports
interface range GigabitEthernet0/1 - 24
 no cdp enable
 no lldp transmit
 no lldp receive

! Trunk/uplink ports — leave CDP/LLDP on (default)
interface GigabitEthernet0/25
 cdp enable
 lldp transmit
 lldp receive
```

---

## Troubleshooting Patterns

**No neighbors shown after connecting a cable**
1. Check physical: `show interfaces Gig0/1` — is the line protocol up?
2. Check CDP on local device: `show cdp interface Gig0/1` — is CDP active on this port?
3. Check CDP on neighbor: `show cdp` on the remote device — is it running globally?
4. Check hold time: if it was recently disabled, wait one interval (60 sec) for refresh
5. Verify same L2 — CDP does not cross routers

**Neighbor appears then disappears**
- Hold time expiring without refresh → intermittent physical link or CRC errors
- Run `show cdp traffic` and look for increasing `checksum errors`
- Check `show interfaces` for input errors / CRC

**Native VLAN mismatch warning**
```
%CDP-4-NATIVE_VLAN_MISMATCH: Native VLAN mismatch discovered on GigabitEthernet0/1 (1)
```
Both ends of the trunk must have the same native VLAN. Fix: `switchport trunk native vlan <n>` on both sides.

**LLDP neighbor not showing after `lldp run`**
- LLDP has a `reinit` timer (default 2 sec) — wait for first advertisement cycle
- Verify with `show lldp interface` that TX and RX are both enabled
- Remote device may not support LLDP (very old IOS, or non-802.1AB device)

---

## Key Distinctions for the Exam

```
CDP  → Cisco only, always-on by default, 60/180 timers
LLDP → vendor-neutral, off by default, 30/120 timers, TX/RX independent
Both → L2 only, one hop only, never cross a router
Both → disable on untrusted/user-facing ports
```

The exam will give you a scenario where a neighbor is not discovered — trace through: is it the right protocol? Is it enabled on both ends? Is it the right type of port?

---

## Lab

**File:** `CDP_LLDP_Lab.pkt`

See the Packet Tracer lab for hands-on verification of all commands above. The topology includes:
- Cisco–Cisco links (CDP + LLDP)
- Cisco–non-Cisco link (LLDP only simulation)
- Access ports with CDP/LLDP disabled
- A native VLAN mismatch to trigger and resolve

---

