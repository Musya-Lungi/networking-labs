# ApexTrust Bank Enterprise Campus Network Lab

## Project Overview
This project simulates a real-world enterprise campus network for ApexTrust Bank with three Nairobi branches:

- Upper Hill HQ (Core Campus – 200 users)
- Westlands Branch (80 users)
- Kilimani Branch (60 users)

The design follows Cisco CCNA Enterprise Campus principles and focuses on scalable switching, redundancy, security, and wireless integration.

---

## Business Requirements

ApexTrust Bank requires a secure, segmented, and highly available network infrastructure that supports:

- Department-based VLAN segmentation
- Redundant switching at HQ
- Secure inter-switch communication
- Wireless access for staff and guests
- Secure remote device management
- WAN connectivity between branches

---

## Branch Design

### Upper Hill HQ (Core Campus)
- 2 Core/Distribution switches (Core1, Core2)
- Multiple access switches
- Redundant inter-core connectivity (EtherChannel)
- STP root control per VLAN
- Wireless infrastructure (Staff + Guest SSIDs)

### Westlands Branch
- 2-tier switching design
- VLAN segmentation identical to HQ
- WAN router connectivity

### Kilimani Branch
- 2-tier switching design
- Smaller access layer
- WAN router connectivity

---

## VLAN Architecture

All branches use the same VLAN scheme:

| VLAN | Department |
|------|------------|
| VLAN 10 | Customer Service |
| VLAN 20 | Credit & Risk |
| VLAN 30 | Operations & IT |
| VLAN 40 | Management |

---

## Core Technologies Implemented

### 1. VLANs
- Creation and assignment per department
- Port-based VLAN segmentation
- VLAN verification using show commands

---

### 2. 802.1Q Trunking
- Inter-switch trunk links
- Native VLAN configuration
- VLAN propagation across switches

---

### 3. Spanning Tree Protocol (PVST+)
- VLAN-based STP instances
- Root bridge design:

| VLAN Group | Root Switch |
|------------|-------------|
| VLAN 10 & 20 | Core1 |
| VLAN 30 & 40 | Core2 |

- Port roles and redundancy validation

---

### 4. EtherChannel (LACP)
- Layer 2 trunk EtherChannels between Core switches
- Optional Layer 3 EtherChannel links
- Load balancing across member links

---

### 5. Device Discovery
- CDP enabled for internal topology discovery
- LLDP enabled for vendor-neutral discovery
- CDP disabled on WAN-facing interfaces

---

### 6. Secure Device Management
- SSH-only access enforced
- Telnet disabled completely
- Local user authentication
- Console and VTY line security
- Basic AAA/TACACS+ concept simulation

---

### 7. Wireless LAN
- 802.11ac Access Points deployed
- STAFF SSID:
  - WPA2-PSK secured
  - Internal network access
- GUEST SSID:
  - Isolated access
  - Restricted network segmentation

---

### 8. WAN Connectivity
- Router-based inter-branch connectivity
- Static routing or simplified dynamic routing (CCNA level)
- CDP disabled on WAN interfaces

---

## Security Policies

- SSH-only management access
- Strong password enforcement
- Disabled unused services
- Secure trunk configurations
- WAN interface hardening

---

## Packet Tracer Implementation Scope

This lab will be built in phases:

### Phase 1: HQ Campus Build
- Core switches
- Access layer switches
- VLAN configuration
- Trunking setup

### Phase 2: STP + Redundancy
- PVST+ configuration
- Root bridge election per VLAN
- Loop prevention validation

### Phase 3: EtherChannel
- LACP configuration between Core switches
- Verification of bundled links

### Phase 4: Security Baseline
- SSH configuration
- Disable Telnet
- Secure VTY lines

### Phase 5: Wireless Setup
- AP deployment
- SSID configuration
- WPA2-PSK setup

### Phase 6: WAN Integration
- Branch router connectivity
- Inter-branch communication testing

---

## Verification Commands

- `show vlan brief`
- `show interfaces trunk`
- `show spanning-tree`
- `show etherchannel summary`
- `show cdp neighbors`
- `show lldp neighbors`
- `show ip interface brief`
- `show running-config`

---

## Deliverables

- Full Packet Tracer topology (.pkt)
- Complete working configuration
- README documentation (this file)
- Verified network functionality

---

