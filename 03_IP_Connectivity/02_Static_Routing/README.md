# Static Routing Lab — IPv4, Next-Hop, Exit Interface & Floating Static Routes

## Overview

This lab demonstrates advanced static routing concepts in a multi-router topology. It focuses on route selection, recursive lookup, default routing, floating static routes, and route summarization in an enterprise-style network.

The goal is to understand how routers make forwarding decisions using static routes and how redundancy is achieved without dynamic routing protocols.

---

## Key Concepts Covered

* Static route configuration using next-hop and exit interface
* Recursive lookup process
* Default static route (gateway of last resort)
* Floating static routes (backup routes with higher AD)
* Summary static routing (route aggregation)
* Longest prefix match behavior
* Administrative Distance (AD) influence on route selection

---

## Lab Topology

* 3 Routers (R1, R2, R3)
* 3 LANs
* 1 WAN backbone (R1 ↔ R2 ↔ R3)
* Redundant backup link between R1 and R3

---

## IP Addressing Scheme

* LAN1 (R1): 192.168.10.0/24
* LAN2 (R2): 192.168.20.0/24
* LAN3 (R3): 192.168.30.0/24
* WAN links: 10.0.0.0/30, 10.0.0.4/30
* Backup link (R1–R3): 10.0.0.8/30

---

## Learning Outcomes

By completing this lab, you will be able to:

* Build static routing tables across multiple routers
* Understand how recursive lookup determines exit interfaces
* Implement backup routing using floating static routes
* Configure default routes for external traffic handling
* Verify routing decisions using Cisco IOS commands
* Interpret routing table entries (C, S, S*, L routes)

---

## Verification Commands

```bash
show ip route
show ip arp
show ip cef
show running-config
```

---

## Expected Behavior

* Primary path: R1 → R2 → R3
* Backup path: R1 → R3 (only activates if R2 fails)
* Internet traffic (simulated): uses default route
* Specific routes always override default routes

---


