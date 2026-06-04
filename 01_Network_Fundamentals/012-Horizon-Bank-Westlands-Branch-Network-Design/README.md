# Horizon Bank Kenya - Westlands Branch Network Design

## Project Overview
This project simulates the design and implementation of an enterprise branch network for Horizon Bank Kenya (Westlands Branch). The network supports multiple departments, VLAN segmentation, inter-VLAN routing, DHCP services, and WAN connectivity planning.

The design follows CCNA-level enterprise networking principles including subnetting, VLAN configuration, router-on-a-stick, DHCP relay, and structured IP addressing.

---

## Objectives
- Design a scalable enterprise LAN for a bank branch
- Implement VLAN segmentation for departments
- Configure inter-VLAN routing using router-on-a-stick
- Deploy DHCP services for dynamic IP assignment
- Implement trunking between switch and router
- Validate end-to-end connectivity across all networks


## Network Topology Design

The network is structured using a hierarchical enterprise model:

### 1. Core Components
- Branch Router (Router-on-a-Stick configuration)
- Distribution Switch (Layer 2 VLAN aggregation)
- Multiple Access Switches (Department segmentation)
- DHCP Server (Centralized IP assignment)
- Wireless Access Point (Wireless VLAN access)

---

### 2. VLAN Design

| VLAN ID | Department         | Subnet             | Default Gateway     |
|----------|------------------|--------------------|---------------------|
| 10       | Retail Banking    | 10.50.0.0/27       | 10.50.0.1           |
| 20       | Corporate Banking | 10.50.0.32/27      | 10.50.0.33          |
| 30       | IT Operations     | 10.50.0.64/27      | 10.50.0.65          |
| 40       | Management        | 10.50.0.128/27     | 10.50.0.129         |
| 50       | Server Farm       | 10.50.0.160/27     | 10.50.0.161         |
| 60       | Wireless Network  | 10.50.0.192/27     | 10.50.0.193         |

---

### 3. WAN Design (Planned)
- Head Office Link
- Disaster Recovery Site Link
- ATM Network Link
- IPv6 WAN Prefix: 2001:DB8:HB::/48

---

### 4. Key Technologies Used
- VLAN Segmentation (802.1Q Trunking)
- Inter-VLAN Routing (Router-on-a-Stick)
- DHCP Relay (ip helper-address)
- Static IP addressing for servers
- Cisco Packet Tracer simulation


## Configuration Summary

### 1. Inter-VLAN Routing (Router-on-a-Stick)
The branch router was configured with subinterfaces to support VLAN routing:

- G0/0.10 → VLAN 10 (Retail Banking)
- G0/0.20 → VLAN 20 (Corporate Banking)
- G0/0.30 → VLAN 30 (IT Operations)
- G0/0.40 → VLAN 40 (Management)
- G0/0.50 → VLAN 50 (Server Farm)
- G0/0.60 → VLAN 60 (Wireless Network)

All subinterfaces use 802.1Q encapsulation.

---

### 2. DHCP Configuration
A centralized DHCP server was deployed in VLAN 50.

- Server IP: 10.50.0.162
- DHCP pools configured per VLAN subnet
- Default gateways assigned per VLAN
- DNS set to internal server

DHCP relay was enabled on router subinterfaces using:
- `ip helper-address 10.50.0.162`

---

### 3. Switching Configuration
- VLANs 10–60 created on distribution switch
- Access ports assigned per department
- Trunk link configured between:
  - Distribution Switch ↔ Branch Router
- Trunk allows VLANs 10,20,30,40,50,60

---

### 4. Verification Results
- Inter-VLAN routing: Successful
- DHCP assignment: Successful
- Trunk link: Operational (802.1Q)
- End-device connectivity: Verified across VLANs


## Conclusion

This project successfully demonstrates the design and implementation of an enterprise branch network for a banking environment using Cisco Packet Tracer.

The network supports departmental segmentation, inter-VLAN routing, centralized DHCP services, and scalable IP addressing within a structured enterprise architecture.

All core services were tested and verified, ensuring full end-to-end connectivity across all VLANs.

---

## Skills Demonstrated

- Enterprise network design (banking scenario)
- VLAN creation and segmentation
- Router-on-a-stick inter-VLAN routing
- DHCP server configuration and relay (ip helper-address)
- Subnetting using VLSM principles
- Cisco switch trunk configuration (802.1Q)
- Troubleshooting Layer 2 and Layer 3 connectivity issues
- Network verification and testing in Packet Tracer