# Day 5 Runbook — Switching, MAC Learning, Wireless & Virtualization

## Objective

Understand how switches learn MAC addresses, forward frames, handle flooding, and how basic wireless and virtualization concepts fit into enterprise networks.

---

# Switching Concepts

## MAC Address Learning

Switches learn MAC addresses dynamically by reading the source MAC of incoming frames.

- Source MAC + ingress port = MAC table entry
- Entries are stored per interface

---

## MAC Forwarding Behavior

### Known Unicast
- Frame forwarded only to correct port

### Unknown Unicast
- Switch floods frame to all ports except source

### Broadcast
- Sent to all ports in VLAN/domain

---

## MAC Aging

- Default timer: 300 seconds
- Removes inactive entries
- Prevents stale forwarding paths

---

## Collision vs Broadcast Domains

- Switch creates separate collision domains per port
- Broadcast domain remains shared (unless VLANs are used)

---

## Duplex Operation

### Full Duplex
- Simultaneous send/receive
- No collisions

### Half Duplex
- One direction at a time
- CSMA/CD required
- Collisions possible

---

# Wireless Concepts

## Frequency Bands

### 2.4 GHz
- Longer range
- More interference

### 5 GHz
- Faster
- Shorter range

---

## Channels

- 1, 6, 11 are non-overlapping in 2.4 GHz
- Reduces interference between APs

---

## Wireless Architecture

- SSID: Network name
- BSS: Single AP + clients
- ESS: Multiple APs under same SSID
- BSSID: AP MAC address

---

# Virtualization Concepts

## Virtual Machines (VMs)
- Full OS virtualization
- Requires hypervisor

## Type 1 Hypervisor
- Runs on hardware
- Example: ESXi

## Type 2 Hypervisor
- Runs on OS
- Example: VirtualBox

## Containers
- Share host OS kernel
- Lightweight and fast

## VRF
- Multiple routing tables on one device
- Used in enterprise segmentation

---

# Key Lab Observations

- MAC table populates after traffic is generated
- Unknown unicast frames are flooded initially
- Broadcast frames reach all devices
- Full duplex eliminates collisions