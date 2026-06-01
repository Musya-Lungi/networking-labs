# IPv6 Addressing Plan - Horizon Bank Network

## Overview
This document defines the IPv6 addressing strategy for the Horizon Bank Westlands Branch network. Although IPv6 is not fully implemented in the current Packet Tracer simulation, it is included to demonstrate enterprise-ready dual-stack design thinking.

---

## IPv6 Addressing Scheme

### Global Prefix Allocation
- Bank Enterprise Prefix: `2001:DB8:HB::/48`

This prefix is reserved for internal enterprise simulation and follows IPv6 documentation standards.

---

## VLAN IPv6 Allocation Plan

| VLAN ID | Department         | IPv6 Subnet Prefix        |
|----------|------------------|---------------------------|
| 10       | Retail Banking    | 2001:DB8:HB:10::/64       |
| 20       | Corporate Banking | 2001:DB8:HB:20::/64       |
| 30       | IT Operations     | 2001:DB8:HB:30::/64       |
| 40       | Management        | 2001:DB8:HB:40::/64       |
| 50       | Server Farm       | 2001:DB8:HB:50::/64       |
| 60       | Wireless Network  | 2001:DB8:HB:60::/64       |

---

## WAN IPv6 Design (Planned)

Point-to-point links are allocated /127 subnets for efficiency:

- Branch ↔ Head Office: `2001:DB8:HB:1::/127`
- Branch ↔ DR Site: `2001:DB8:HB:2::/127`
- Branch ↔ ATM Network: `2001:DB8:HB:3::/127`
- Branch ↔ Internet/Cloud: `2001:DB8:HB:4::/127`

---

## Design Principles

- /64 per VLAN for standard IPv6 LAN segmentation
- /127 for WAN point-to-point links (RFC 6164 best practice)
- Clear separation between LAN and WAN IPv6 space
- Structured hierarchical addressing for scalability

---

## Summary
This IPv6 design prepares the network for future dual-stack deployment while maintaining compatibility with enterprise banking network standards.