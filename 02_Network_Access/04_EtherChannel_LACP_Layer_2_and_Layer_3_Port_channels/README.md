# EtherChannel — LACP Layer 2 Port-Channel Lab

## Overview

This lab demonstrates the configuration and verification of EtherChannel using LACP (Link Aggregation Control Protocol) between two Cisco switches.

The objective of the lab is to understand how multiple physical interfaces can be bundled into a single logical interface called a Port-Channel to achieve:

- Increased bandwidth
- Link redundancy
- Better utilization of switch links
- Prevention of unnecessary STP blocking


---

# Technologies Covered

- EtherChannel
- LACP (802.3ad)
- Layer 2 Port-Channels
- Trunking
- Spanning Tree Protocol (STP)
- EtherChannel verification and troubleshooting


---

# Topology

SW1 <==== Port-Channel 1 ====> SW2

Interfaces used:

- Fa0/1
- Fa0/2

Both interfaces are bundled into Port-Channel 1 using LACP.

---

# Objectives

- Configure Layer 2 EtherChannel
- Configure LACP active/passive modes
- Configure trunking on Port-Channel
- Verify EtherChannel functionality
- Understand EtherChannel requirements


---

# Configuration Summary

## Switch 1

```cisco
interface range fa0/1 - 2
 switchport mode trunk
 channel-group 1 mode active

interface port-channel 1
 switchport mode trunk
```

## Switch 2

```cisco
interface range fa0/1 - 2
 switchport mode trunk
 channel-group 1 mode passive

interface port-channel 1
 switchport mode trunk
```

---

# Verification Commands

```cisco
show etherchannel summary
show etherchannel port-channel
show interfaces port-channel 1
show lacp neighbor


---

# Key Lessons Learned

- EtherChannel bundles multiple physical links into one logical link
- LACP is the industry-standard protocol for link aggregation
- Active + Passive mode works; Passive + Passive does not
- All member interfaces must match (speed, duplex, VLANs, trunking)
- EtherChannel prevents STP from blocking redundant links
- Load balancing happens per flow, not per packet

---

# Author

Stephen Musya Lungi  
Infrastructure / Networking Learning Lab