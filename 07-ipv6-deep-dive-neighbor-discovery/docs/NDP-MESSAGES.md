# IPv6 Neighbor Discovery Protocol (NDP)

## Overview

NDP replaces ARP in IPv6 networks. It operates using ICMPv6 messages and is responsible for address resolution, router discovery, and neighbor reachability.

---

## Why NDP exists

In IPv4:
- ARP resolves IP → MAC addresses

In IPv6:
- NDP performs this role using ICMPv6
- More secure and scalable

---

## NDP Message Types

### 1. Router Solicitation (RS)
- Sent by hosts
- Requests router information

---

### 2. Router Advertisement (RA)
- Sent by routers
- Provides:
  - network prefix
  - gateway
  - SLAAC info

---

### 3. Neighbor Solicitation (NS)
- Used to discover MAC address of a neighbor
- Similar to ARP request

---

### 4. Neighbor Advertisement (NA)
- Response to NS
- Contains MAC address of requested device

---

## NDP Workflow Example

1. PC sends NS request
2. Target device replies with NA
3. MAC address learned
4. Communication begins

---

## Key Idea

NDP uses multicast instead of broadcast:
- More efficient
- Less network noise
- Better scalability

---

## Summary

NDP is responsible for:
- Address resolution
- Router discovery
- Duplicate address detection
- Neighbor reachability tracking