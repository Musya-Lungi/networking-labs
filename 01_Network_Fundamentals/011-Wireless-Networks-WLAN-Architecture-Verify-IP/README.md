# Day 11 — Wireless Networks · WLAN Architecture · Verify IP Parameters

## Project Overview

This lab focuses on basic enterprise wireless networking concepts using Cisco Packet Tracer.

The objective is to design and verify a small wireless LAN (WLAN) environment that includes:
- wired infrastructure
- wireless connectivity
- DHCP addressing
- DNS resolution
- IP verification
- basic troubleshooting

The lab simulates a small enterprise office wireless deployment where wireless clients must successfully connect to the network and communicate with internal services.

---

# Objectives

- Build a basic WLAN topology in Packet Tracer
- Configure wired and wireless devices
- Configure wireless clients
- Verify DHCP IP assignment
- Verify DNS name resolution
- Test end-to-end connectivity
- Practice IP verification commands
- Observe MAC address learning on switches
- Document troubleshooting observations

---

# Technologies Covered

- WLAN fundamentals
- SSID configuration
- WPA2 wireless security
- DHCP
- DNS
- HTTP
- IPv4 addressing
- MAC address tables
- TCP/IP verification utilities

---

# Devices To Be Used

| Device | Purpose |
|---|---|
| Router | Default gateway |
| Switch | Layer 2 connectivity |
| Access Point / Wireless Router | Wireless connectivity |
| PCs | Wired clients |
| Laptops | Wireless clients |
| Server | DNS + HTTP services |

---

# Verification Commands

```bash
ipconfig
ping
tracert
arp
nslookup
show ip interface brief
show mac address-table


---

# Network Topology Design

## Logical Topology

The network is designed as a simple hierarchical LAN structure:

- A central router acts as the default gateway
- A switch provides Layer 2 connectivity for wired devices
- An access point provides wireless connectivity for laptops and mobile devices
- A server provides DHCP, DNS, and HTTP services



---

## Physical Topology

- All wired devices connect to the switch using Ethernet cables
- The Access Point connects to the switch using a straight-through cable
- Wireless devices connect via SSID broadcast
- The router connects to the switch via Ethernet

---

## Design Logic

- Switch is used for Layer 2 switching and MAC learning
- Router provides IP routing and default gateway functionality
- Access Point extends network access wirelessly
- DHCP simplifies IP assignment for clients



---

# IP Addressing Plan (Revised)

## IPv4 Network

The WLAN lab uses a private enterprise addressing scheme.

### Network Block
- Network: 192.168.10.0/24
- Subnet Mask: 255.255.255.0

This single subnet is used to simulate a small enterprise wireless LAN.

---

## Network Segmentation Logic

Even though this is one subnet, logical separation exists:

- Wired devices (PCs, server, router)
- Wireless devices (laptops, mobile devices)
- Infrastructure devices (AP, switch)

---

## Device IP Allocation

| Device | IP Address | Purpose |
|--------|------------|----------|
| Router | 192.168.10.1 | Default Gateway |
| Switch | N/A | Layer 2 switching |
| Access Point | 192.168.10.2 | Wireless connectivity |
| DHCP Server | 192.168.10.10 | Automatic IP assignment |
| DNS Server | 192.168.10.11 | Name resolution |
| HTTP Server | 192.168.10.12 | Web services |

---

## DHCP Address Pool (Wireless Clients)

- Start IP: 192.168.10.100  
- End IP: 192.168.10.200  
- Subnet Mask: 255.255.255.0  
- Default Gateway: 192.168.10.1  
- DNS Server: 192.168.10.11  

---

## Design Rationale

- Single subnet keeps lab simple for WLAN focus
- DHCP automates wireless client configuration
- Gateway centralizes traffic routing
- DNS enables name resolution testing
- AP acts as bridge between wireless and wired network

---

# Lab Verification Results

## Connectivity Tests

- Wireless client successfully connected to SSID
- DHCP assigned IP address automatically
- Gateway connectivity confirmed via ping
- DNS resolution successful using equity.local
- HTTP service accessible via browser

---

# Troubleshooting Notes

- DHCP must be active before wireless connection
- Incorrect WPA2 password prevents association
- Missing gateway blocks external communication
- DNS misconfiguration prevents name resolution

---

# Conclusion

This lab successfully demonstrates:
- WLAN architecture (autonomous vs lightweight AP concepts)
- Basic enterprise wireless connectivity
- DHCP and DNS integration
- IP verification and troubleshooting workflow
- CAPWAP and WLC conceptual understanding