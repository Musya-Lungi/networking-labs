# Day 5 Lab Topology Design

## Objective

Observe how switches learn MAC addresses and make forwarding decisions inside a LAN.

---

## Devices Required

- 2 Switches
- 4 PCs

---

## Network Design

### Subnet
192.168.1.0/24

---

## PC Addressing

| Device | IP Address |
|--------|-------------|
| PC1 | 192.168.1.10 |
| PC2 | 192.168.1.11 |
| PC3 | 192.168.1.12 |
| PC4 | 192.168.1.13 |

Subnet Mask:
255.255.255.0

---

## Switch Topology

- SW1 connected to SW2
- All PCs connected to SW1

---

## Learning Objectives

### MAC Learning
Observe MAC table population after traffic is generated.

### Unknown Unicast Flooding
Observe switch flooding behavior when destination MAC is unknown.

### Broadcast Behavior
Observe broadcast traffic sent to all ports.

### Duplex Verification
Use switch CLI to inspect duplex and speed settings.