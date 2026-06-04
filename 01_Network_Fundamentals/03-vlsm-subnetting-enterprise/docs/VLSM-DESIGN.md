# Day 3 - VLSM Subnet Design

## Objective
Design an efficient IPv4 addressing scheme using VLSM (Variable Length Subnet Masking) for an enterprise network with uneven department sizes.

---

## Base Network
192.168.0.0/24

---

## Department Requirements

| Department   | Hosts Needed |
|--------------|-------------|
| IT           | 100 hosts   |
| HR           | 50 hosts    |
| Sales        | 25 hosts    |
| Management   | 10 hosts    |

---

## VLSM Allocation Strategy

We allocate from largest to smallest:

###1. IT Department
Network: 192.168.0.0/25
Usable Hosts: 192.168.0.1 – 192.168.0.126
Broadcast: 192.168.0.127
Default Gateway: 192.168.0.1


###2. HR Department
Network: 192.168.0.128/26
Usable Hosts: 192.168.0.129 – 192.168.0.190
Broadcast: 192.168.0.191
Default Gateway: 192.168.0.129


###3. Sales Department
Network: 192.168.0.192/27
Usable Hosts: 192.168.0.193 – 192.168.0.222
Broadcast: 192.168.0.223
Default Gateway: 192.168.0.193


###4. Management
Network: 192.168.0.224/28
Usable Hosts: 192.168.0.225 – 192.168.0.238
Broadcast: 192.168.0.239
Default Gateway: 192.168.0.225
---

## Key Learning

- VLSM reduces IP wastage
- Larger subnets must be allocated first
- Efficient planning is critical in enterprise networks