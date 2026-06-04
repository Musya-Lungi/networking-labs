# Day 7 Lab Topology — IPv6, EUI-64 & Neighbor Discovery

## Objective

Configure IPv6 addressing, observe connectivity, and understand Neighbor Discovery Protocol (NDP) behavior in a routed environment.

---

## Devices

- 1 Router (Router0)
- 2 PCs (PC1, PC2)

---

## Network Design

Router connects two IPv6 subnets:

### Network 1
- 2001:DB8:ACAD:1::/64

### Network 2
- 2001:DB8:ACAD:2::/64

---

## IP Plan

### Router0

- G0/0 → 2001:DB8:ACAD:1::1/64
- G0/1 → 2001:DB8:ACAD:2::1/64

---

### PC1
- IPv6: 2001:DB8:ACAD:1::10/64
- Gateway: 2001:DB8:ACAD:1::1

---

### PC2
- IPv6: 2001:DB8:ACAD:2::10/64
- Gateway: 2001:DB8:ACAD:2::1

---

## Key Learning Goals

### IPv6 Configuration
- Manual addressing
- Prefix /64 usage

### Router Role
- Inter-network routing between IPv6 subnets

### NDP Behavior
- Observe neighbor discovery instead of ARP

---

## Verification Commands

On Router0:
- show ipv6 interface brief
- show ipv6 neighbors

---

## Expected Outcome

- PC1 can ping PC2 using IPv6
- Router forwards traffic between subnets
- NDP entries populate automatically