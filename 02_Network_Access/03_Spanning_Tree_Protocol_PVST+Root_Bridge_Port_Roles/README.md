# Lab 03 — Spanning Tree Protocol: PVST+, Root Bridge & Port Roles

---

## Objectives

- Understand why STP exists: prevent Layer 2 loops and broadcast storms in redundant topologies
- Observe root bridge election based on Bridge ID (priority + MAC address)
- Identify and verify port roles: root port, designated port, non-designated (blocked)
- Trace port state transitions: blocking → listening → learning → forwarding
- Compare classic 802.1D STP convergence time vs Rapid PVST+ (802.1w)
- Understand BPDUs: how switches communicate STP state to each other

---

## Key Concepts

| Concept | Summary |
|---|---|
| Broadcast storm | Frames loop endlessly in a redundant L2 topology — STP prevents this |
| Root bridge | Switch with the lowest Bridge ID (priority + MAC); all paths calculated from here |
| Bridge ID | 2-byte priority (default 32768) + 6-byte MAC address |
| Root port | Best-cost port on a non-root switch pointing toward the root bridge |
| Designated port | Forwarding port on each network segment; root bridge ports are always DP |
| Blocked port | Non-designated port placed in blocking state to break the loop |
| BPDU | Hello message sent every 2s by root; carries Bridge ID, path cost, port ID |
| PVST+ | Cisco extension — separate STP instance per VLAN, enables load balancing |
| Rapid PVST+ | 802.1w-based; converges in 1–2s via proposal/agreement; edge ports forward instantly |

---

## Lab Topology

Three switches in a triangle (redundant links):



- SW1: priority manually set to `4096` (root)
- SW2: priority `32768` (default)
- SW3: priority `32768` (default)
- SW2–SW3 link: non-designated port on SW3 enters **blocking** state

---

## Tasks Completed

- [x] Connected three switches with redundant links in Packet Tracer
- [x] Verified default STP election (random root — undesirable)
- [x] Manually set SW1 as root bridge via `spanning-tree vlan 1 priority 4096`
- [x] Verified port roles using `show spanning-tree`
- [x] Observed port state transitions after unplugging the root uplink on SW2
- [x] Enabled Rapid PVST+ and compared convergence behaviour
- [x] Configured `spanning-tree portfast` on access ports

---

## Commands Used

```bash
# Set root bridge priority
SW1(config)# spanning-tree vlan 1 priority 4096

# Verify STP topology
SW1# show spanning-tree
SW2# show spanning-tree vlan 1

# Check port roles and states
SW2# show spanning-tree detail

# Enable Rapid PVST+
SW1(config)# spanning-tree mode rapid-pvst

# Configure PortFast on access port
SW2(config-if)# spanning-tree portfast
```

---

## Observations

- Without manually setting priority, SW3 won the election due to a lower MAC address — a good example of why automatic root bridge election is risky in production
- Classic STP took ~30s to reconverge after unplugging the SW1–SW2 uplink
- Rapid PVST+ reconverged in under 2 seconds on the same topology
- PortFast on access ports eliminated the 30s delay for end-device connectivity

---

## Files

| File | Description |
|---|---|
| `stp_lab.pkt` | Packet Tracer topology file |
| `README.md` | This file |

---

## Resources

- [Cisco STP Configuration Guide](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst9300/software/release/17-x/configuration_guide/lyr2/b_172_lyr2_9300_cg/configuring_stp.html)
- [IEEE 802.1D — Spanning Tree Protocol](https://standards.ieee.org/ieee/802.1D/3387/)
- [IEEE 802.1w — Rapid STP](https://standards.ieee.org/ieee/802.1w/3378/)