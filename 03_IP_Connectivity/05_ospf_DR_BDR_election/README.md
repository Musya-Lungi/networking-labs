# OSPF DR/BDR Election Lab

## Overview
This lab demonstrates OSPF Designated Router (DR) and Backup Designated Router (BDR) election on a broadcast multi-access network, along with OSPF cost calculation and route selection behavior.

---

## Objectives
- Understand OSPF DR/BDR election process
- Observe OSPF adjacency reduction on broadcast networks
- Analyze router ID and priority influence on elections
- Study OSPF cost calculation and path selection
- Identify OSPF route types (O, O IA, E1, E2)

---

## Topology
- 4 routers connected via a switch (broadcast segment)
- OSPF area 0 configured on all interfaces
- Default and modified priorities tested

(See `/topology/topology.png`)

---

## Key Concepts Covered
- DR/BDR Election Rules
- OSPF Interface Priority
- Router ID Selection
- OSPF Cost Calculation
- Route Type Interpretation

---

## Files Included
- `/configs` → Router configurations
- `/lab-guide` → Step-by-step setup instructions
- `/notes` → Theory breakdown
- `/results` → Verification outputs
- `/topology` → Network design files

---

## Expected Learning Outcome
By completing this lab, you will understand how OSPF reduces network overhead and how engineers influence routing behavior in enterprise networks.