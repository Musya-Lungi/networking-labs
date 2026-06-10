# OSPF Fundamentals Lab

## Overview

This lab introduces Open Shortest Path First (OSPF), a dynamic link-state routing protocol widely used in enterprise networks.

The lab demonstrates:

* OSPF neighbor formation
* Router ID selection
* Network advertisements
* Link-state routing concepts
* Passive interfaces
* OSPF verification and troubleshooting

---

# Objectives

By completing this lab, I learned how to:

* Configure single-area OSPF
* Configure Router IDs
* Use OSPF network statements
* Configure passive interfaces
* Verify OSPF neighbors
* Analyze OSPF routes
* Understand OSPF hello/dead timers

---

# Technologies Used

* Cisco Packet Tracer
* Cisco IOS CLI
* OSPFv2
* IPv4 Addressing

---

# Lab Topology

```plaintext
       R1 -------- R2 -------- R3
        |                       |
      LAN1                    LAN2
```

---

# IP Addressing Table

| Device | Interface | IP Address     |
| ------ | --------- | -------------- |
| R1     | G0/0      | 192.168.1.1/24 |
| R1     | G0/1      | 10.1.12.1/24   |
| R2     | G0/0      | 10.1.12.2/24   |
| R2     | G0/1      | 10.1.23.1/24   |
| R3     | G0/0      | 10.1.23.2/24   |
| R3     | G0/1      | 192.168.3.1/24 |

---

# Key OSPF Concepts

## OSPF

OSPF (Open Shortest Path First) is a link-state routing protocol that uses the Dijkstra SPF algorithm to calculate best paths.

---

## Router ID

Every OSPF router requires a unique Router ID.

Selection priority:

1. Manually configured router-id
2. Highest loopback IP
3. Highest physical interface IP

---

## LSAs and LSDB

OSPF routers exchange Link-State Advertisements (LSAs).

These LSAs build the Link-State Database (LSDB), which represents the network topology.

---

## Passive Interfaces

Passive interfaces advertise networks without sending OSPF hello packets.

Benefits:

* reduced unnecessary traffic
* improved security
* lower CPU utilization

---

## Hello and Dead Timers

Default broadcast timers:

| Timer | Value      |
| ----- | ---------- |
| Hello | 10 seconds |
| Dead  | 40 seconds |

---

# Verification Commands

```bash
show ip ospf neighbor
show ip route ospf
show ip ospf interface brief
show ip ospf database
```

---

# Skills Practiced

* Dynamic routing
* OSPF configuration
* Route verification
* Neighbor troubleshooting
* Enterprise routing fundamentals

---
