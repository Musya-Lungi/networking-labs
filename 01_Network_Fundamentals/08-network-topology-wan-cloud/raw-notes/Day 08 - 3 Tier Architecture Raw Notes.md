Day 08 — Network Topology Architectures (3-Tier Enterprise Design)
1. Overview

This lab implements a simplified enterprise 3-tier campus network architecture using Cisco Packet Tracer. The design includes Access, Distribution, and Core layers with redundant routing paths and VLAN segmentation.

2. Topology Design
Architecture Summary
Access Layer: End devices (PCs) connected to switches
Distribution Layer: Layer 3 switches handling VLAN gateways
Core Layer: Dual-router backbone providing redundant transit paths
Physical Layout
2 Distribution Switches (Dist1, Dist2)
2 Core Routers (Router1, Router2)
Multiple Access Switches
End devices (PCs) per VLAN
Logical Topology
VLAN 10 → 192.168.10.0/24
VLAN 20 → 192.168.20.0/24
3. VLAN Design
VLAN	Name	Subnet	Gateway
10	VLAN10	192.168.10.0/24	192.168.10.1
20	VLAN20	192.168.20.0/24	192.168.20.1
4. Distribution Layer Configuration
Dist1
VLAN 10 SVI: 192.168.10.1
Uplink Interfaces (Core-facing):
10.0.0.1/30
10.0.0.5/30
Dist2
VLAN 20 SVI: 192.168.20.1
Uplink Interfaces (Core-facing):
10.0.0.9/30
10.0.0.13/30
Key Function
Inter-VLAN routing via SVIs
Default gateway for end devices
5. Core Layer Design
Core Devices
Router1
Router2
Core Links
Router1 ↔ Router2 (redundant backbone)
Function
Acts as transit layer between distribution switches
Provides redundancy and path diversity
6. Routing Overview
Routing Method
Static routing used for inter-network communication
Traffic Flow
PC → Access Switch → Distribution Switch → Core Router → Other Distribution Switch → Destination PC
7. Layer 2 Configuration
Access Layer
VLAN assignment per access switch
End devices placed per subnet
Trunking
Distribution to Access: trunk links enabled
VLAN 10 and VLAN 20 allowed on trunks
8. Key Verification Results
Successful Tests
Intra-VLAN communication: OK
VLAN 10 internal ping: Successful
VLAN 20 internal ping: Successful
Inter-subnet communication: Functional after routing convergence
Observations
Initial packet loss observed due to ARP and routing convergence
Stable connectivity achieved after table population
9. Engineering Notes
Each link uses point-to-point /30 addressing for core connectivity
Redundant paths exist between distribution and core layers
Network exhibits asymmetric routing potential (expected in static multi-path design)
Convergence behavior observed during first packet transmission
10. Conclusion

This lab successfully demonstrates a functional 3-tier enterprise topology with VLAN segmentation, Layer 3 distribution switching, and redundant core routing. The design serves as a foundation for advanced routing protocols such as OSPF in future labs.

11. File Reference

Saved as: Day08-3Tier-Architecture.pkt