# OSPF Lab Topology Design Notes

## 1. Purpose of the Topology

This topology is designed to demonstrate:

* OSPF neighbor formation
* multi-router link-state routing
* route propagation across transit networks
* LAN segmentation with passive interfaces

It simulates a small enterprise WAN connecting two branch LANs through a core router.

---

## 2. Physical Topology Design

The network consists of 3 routers:

* R1 (Left Branch Router)
* R2 (Core/Transit Router)
* R3 (Right Branch Router)

### Logical Layout

```plaintext id="t1n9kq"
   LAN 1                         LAN 2
192.168.1.0/24              192.168.3.0/24
      |                           |
      R1 -------- R2 -------- R3
          10.1.12.0/24  10.1.23.0/24
```

---

## 3. Device Roles

### R1 – Branch Router (Left Site)

* Connects to LAN 1
* Connects to R2
* Advertises LAN 1 into OSPF
* Uses passive interface on LAN side

---

### R2 – Core Router (Transit Backbone)

* Central routing point
* Connects R1 and R3
* Fully participates in OSPF
* No passive interfaces

---

### R3 – Branch Router (Right Site)

* Connects to LAN 2
* Connects to R2
* Advertises LAN 2 into OSPF
* Uses passive interface on LAN side

---

## 4. OSPF Area Design

This lab uses a **single-area design**:

```plaintext id="v6m2pd"
Area 0 (Backbone)
```

All routers reside in Area 0 for simplicity.

This represents a flat OSPF design suitable for small to medium networks.

---

## 5. Packet Tracer Build Steps

### Step 1 — Add Devices

Add:

* 3 routers (e.g. 2911 or 1941)
* 2 switches (optional for LAN simulation)
* 2 PCs (optional for end-device testing)

---

### Step 2 — Cable the Network

Use copper straight-through or appropriate interfaces:

* R1 G0/1 ↔ R2 G0/0
* R2 G0/1 ↔ R3 G0/0
* R1 G0/0 ↔ LAN 1 switch/PC
* R3 G0/1 ↔ LAN 2 switch/PC

---

### Step 3 — Configure IP Addresses

Apply IP addressing as defined in `README.md`.

Ensure:

* correct subnet masks
* interfaces are not shut down
* correct interface mapping

---

### Step 4 — Configure OSPF

Apply configurations from:

```
configs/R1.txt
configs/R2.txt
configs/R3.txt
```

---

## 6. Expected Behavior

After configuration:

### Neighbor Formation

* R1 ↔ R2 → FULL state
* R2 ↔ R3 → FULL state

---

### Routing Table

Each router should learn:

* 192.168.1.0/24 (via OSPF)
* 192.168.3.0/24 (via OSPF)

---

### Connectivity

You should be able to:

* Ping PC in LAN 1 from LAN 2
* Ping PC in LAN 2 from LAN 1
* Ping across all router interfaces

---

## 7. Key Learning Outcome

This topology demonstrates:

* how routing intelligence replaces static routes
* how routers build a shared topology map
* how enterprise networks scale using a backbone design

---

## 8. Engineering Insight

This design is a simplified version of real enterprise networks where:

* edge routers connect users
* core routers handle transit traffic
* OSPF ensures automatic route distribution

---
