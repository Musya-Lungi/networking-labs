# Day 8 – IP Addressing Design (3-Tier Architecture)

## 1. Addressing Strategy

This design uses a structured IPv4 plan aligned with a 3-tier enterprise campus architecture. Each VLAN represents a separate broadcast domain, while the core uses point-to-point /30 networks for routing efficiency and redundancy.

---

## 2. VLAN Subnet Plan (Access Layer)

* **VLAN 10 (Dist1 Gateway Domain)**

  * Network: 192.168.10.0/24
  * Default Gateway: 192.168.10.1 (Dist1 SVI)

* **VLAN 20 (Dist2 Gateway Domain)**

  * Network: 192.168.20.0/24
  * Default Gateway: 192.168.20.1 (Dist2 SVI)

---

## 3. Distribution Layer Addressing

### Dist1 (VLAN 10 Root)

* VLAN 10 SVI: 192.168.10.1/24
* Core-facing interfaces:

  * 10.0.0.1/30 (to Router1)
  * 10.0.0.5/30 (to Router2)

### Dist2 (VLAN 20 Root)

* VLAN 20 SVI: 192.168.20.1/24
* Core-facing interfaces:

  * 10.0.0.9/30 (to Router1)
  * 10.0.0.13/30 (to Router2)

---

## 4. Core Layer Addressing (Backbone)

The core layer uses point-to-point /30 networks for deterministic routing and redundancy.

* Dist1 ↔ Router1: 10.0.0.0/30
* Dist1 ↔ Router2: 10.0.0.4/30
* Dist2 ↔ Router1: 10.0.0.8/30
* Dist2 ↔ Router2: 10.0.0.12/30
* Router1 ↔ Router2 (core backbone): 10.0.0.16/30

---

## 5. Core Layer Role

* Provides redundant transport paths between distribution switches
* Acts as backbone for inter-subnet routing
* Ensures failover capability between Router1 and Router2

---

## 6. Design Principles

* Each VLAN = isolated broadcast domain
* Each core link = unique /30 subnet (no overlap)
* Distribution layer performs Layer 3 gateway role
* Core layer provides redundancy and transit routing
* Dual-homed design ensures fault tolerance

---

## 7. Engineering Summary

This addressing scheme implements a scalable enterprise model:

* Clear separation of access, distribution, and core layers
* Structured VLAN segmentation
* Redundant routed backbone
* Point-to-point addressing for predictable routing behavior

---

## 8. Outcome

This IP plan supports full inter-VLAN communication, redundant routing paths, and prepares the network for advanced dynamic routing protocols (e.g., OSPF) in future expansion stages.
