# Day 2 IP Addressing Plan — Enterprise Subnetting Lab

## Objective
Design and implement a structured IPv4 addressing scheme for a small enterprise network segmented into HR, IT, and Sales departments.

---

## Base Network
192.168.0.0/24 (Private Address Space)

This network is subdivided into departmental subnets.

---

## Subnet Allocation

### HR Department
- Network: 192.168.10.0/24
- Subnet Mask: 255.255.255.0
- Default Gateway: 192.168.10.1
- Usable Range: 192.168.10.1 – 192.168.10.254
- Broadcast: 192.168.10.255

---

### IT Department
- Network: 192.168.20.0/24
- Subnet Mask: 255.255.255.0
- Default Gateway: 192.168.20.1
- Usable Range: 192.168.20.1 – 192.168.20.254
- Broadcast: 192.168.20.255

---

### Sales Department
- Network: 192.168.30.0/24
- Subnet Mask: 255.255.255.0
- Default Gateway: 192.168.30.1
- Usable Range: 192.168.30.1 – 192.168.30.254
- Broadcast: 192.168.30.255

---

## Design Logic

- Each department is isolated in its own subnet
- Router will act as the default gateway for all subnets
- Switches operate at Layer 2 and do not require IP for forwarding
- PCs must be assigned static IPs within their subnet range

---

## Key Learning Outcome

This design demonstrates:
- Logical segmentation of enterprise networks
- Efficient IP utilization
- Foundation of routing between subnets