# Domain 3 — How Routers Work: Routing Table Components & Forwarding Decisions

## Overview

Day 1 of Domain 3 focuses on understanding how routers make forwarding decisions and how routing information is stored and processed internally. This lab explores router architecture, routing table components, administrative distance, longest prefix match, and packet forwarding behavior in enterprise networks.

---

# Objectives

By the end of this lab, I was able to:

* Understand router architecture and forwarding logic
* Explore the Routing Information Base (RIB)
* Understand Cisco Express Forwarding (CEF) and the Forwarding Information Base (FIB)
* Learn the purpose of the ARP table
* Interpret routing table components
* Identify route source codes
* Understand Administrative Distance (AD)
* Compare routing metrics
* Understand longest prefix match
* Understand how routers behave when no matching route exists

---

# Router Architecture

## 1. Routing Information Base (RIB)

The Routing Information Base (RIB) is the router’s master routing table. It stores all learned routes from:

* Connected networks
* Static routes
* Dynamic routing protocols

The router uses the RIB to determine the best available path to a destination network.

### Command Used

```bash
show ip route
```

---

## 2. Forwarding Information Base (FIB)

The Forwarding Information Base (FIB) is built from the routing table and is used for high-speed packet forwarding.

Cisco routers use Cisco Express Forwarding (CEF) to optimize forwarding performance.

### Key Function

* Fast packet lookup
* Efficient forwarding decisions

### Command Used

```bash
show ip cef
```

---

## 3. ARP Table

The ARP table maps IPv4 addresses to MAC addresses on local Ethernet networks.

### Purpose

Before forwarding a packet on an Ethernet network, the router must know:

* Destination IP address
* Destination MAC address

### Command Used

```bash
show arp
```

---

# Routing Table Components

Example Route Entry:

```bash
O 192.168.10.0/24 [110/20] via 10.1.1.2, GigabitEthernet0/0
```

---

## 1. Route Source Code

The route source code identifies where the route was learned from.

| Code | Meaning   |
| ---- | --------- |
| C    | Connected |
| L    | Local     |
| S    | Static    |
| O    | OSPF      |
| R    | RIP       |
| B    | BGP       |
| D    | EIGRP     |

---

## 2. Network / Prefix

Represents the destination network and subnet mask.

Example:

```text
192.168.10.0/24
```

---

## 3. Administrative Distance (AD)

Administrative Distance determines how trustworthy a route source is.

### Rule

Lower AD is preferred.

| Route Type | AD Value |
| ---------- | -------- |
| Connected  | 0        |
| Static     | 1        |
| EIGRP      | 90       |
| OSPF       | 110      |
| RIP        | 120      |

---

## 4. Metric

The metric determines the best path within the same routing protocol.

Examples:

* RIP → Hop count
* OSPF → Cost
* EIGRP → Composite metric

---

## 5. Next-Hop Address

The next router used to reach the destination network.

Example:

```text
via 10.1.1.2
```

---

## 6. Exit Interface

The interface the router uses to forward packets.

Example:

```text
GigabitEthernet0/0
```

---

## 7. Route Uptime

Shows how long the route has been present in the routing table.

Useful for:

* Troubleshooting
* Detecting route instability

---

# Longest Prefix Match

Routers always choose the most specific matching route.

### Example

Available Routes:

```text
192.168.1.0/24
192.168.1.128/28
0.0.0.0/0
```

Destination:

```text
192.168.1.130
```

Selected Route:

```text
192.168.1.128/28
```

Reason:

* /28 is more specific than /24

---

# Default Route

The default route acts as the gateway of last resort.

Example:

```text
0.0.0.0/0
```

Used when no specific route exists.

---

# What Happens When No Route Matches?

If no matching route exists:

1. The packet is dropped
2. The router may send an ICMP Destination Unreachable message

---

# Key Forwarding Decision Process

When a router receives a packet:

1. Reads the destination IP address
2. Searches the FIB/routing table
3. Applies longest prefix match
4. Compares Administrative Distance if necessary
5. Chooses the best metric
6. Determines next-hop and exit interface
7. Uses ARP to resolve MAC address
8. Forwards the packet

---

# Key Commands Practiced

```bash
show ip route
show ip cef
show arp
show ip interface brief
```

---

# Skills Built

This lab strengthened my understanding of:

* Enterprise routing fundamentals
* Packet forwarding logic
* Routing protocol behavior
* Troubleshooting methodology
* Cisco routing table analysis

---

# Progress Log

* Domain: 3
* Day: 1
* Topic: Routing Table Components & Forwarding Decisions
* Status: Completed
