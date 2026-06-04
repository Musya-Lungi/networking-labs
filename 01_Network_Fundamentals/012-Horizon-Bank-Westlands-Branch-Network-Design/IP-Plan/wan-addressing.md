# WAN Addressing Plan - Horizon Bank Kenya Network

## Overview
This document defines the WAN IP addressing scheme used to interconnect the Horizon Bank Westlands Branch network with Head Office, Disaster Recovery site, ATM network, and external cloud/internet services.

The WAN design uses point-to-point /30 subnetting for router links to ensure efficient IP utilization and scalability.

---

## WAN Topology Links

### 1. Branch Router ↔ Head Office Router
- Purpose: Main enterprise connectivity
- Network: 10.50.1.0/30
- Branch IP: 10.50.1.1
- HO IP: 10.50.1.2

---

### 2. Branch Router ↔ Disaster Recovery (DR) Router
- Purpose: Backup and redundancy link
- Network: 10.50.1.4/30
- Branch IP: 10.50.1.5
- DR IP: 10.50.1.6

---

### 3. Branch Router ↔ ATM Network Router
- Purpose: ATM transaction network
- Network: 10.50.1.8/30
- Branch IP: 10.50.1.9
- ATM IP: 10.50.1.10

---

### 4. Branch Router ↔ Cloud / Internet (Simulated)
- Purpose: External connectivity
- Network: 10.50.1.12/30
- Branch IP: 10.50.1.13
- Cloud Gateway: 10.50.1.14

---

## Design Principles Used

- Point-to-point /30 subnetting for WAN efficiency
- Separation of internal LAN (10.50.0.0/24 range) and WAN (10.50.1.0/24 range)
- Scalability for future branch expansion
- Logical segmentation for security and traffic control

---

## Summary
This WAN design ensures secure, scalable, and efficient connectivity between all enterprise components while maintaining clear separation between LAN and WAN environments.