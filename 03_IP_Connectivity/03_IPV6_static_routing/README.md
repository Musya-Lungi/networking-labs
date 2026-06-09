Here’s a clean professional `README.md` you can copy directly into your GitHub repo for today’s IPv6 lab.

# IPv6 Static Routing Lab

## Overview

This lab introduces the fundamentals of **IPv6 Static Routing** in Cisco networking environments using Packet Tracer.

The objective is to understand how routers forward IPv6 traffic manually using static routes, how link-local addresses function as next-hop addresses, and how IPv6 default routes are configured and verified.

The lab also demonstrates how IPv4 and IPv6 can coexist simultaneously in a dual-stack environment.

---

# Learning Objectives

By completing this lab, I was able to:

* Configure IPv6 addressing on Cisco router interfaces
* Enable IPv6 routing using `ipv6 unicast-routing`
* Configure IPv6 static routes
* Configure IPv6 static routes using link-local next hops
* Configure IPv6 default routes
* Verify IPv6 connectivity using Cisco IOS commands
* Understand the importance of exit interfaces when using link-local addresses
* Explore IPv4 and IPv6 dual-stack operation

---

# Technologies Used

* Cisco Packet Tracer
* IPv6 Addressing
* Static Routing
* Link-Local Addressing
* Dual-Stack Networking
* Cisco IOS CLI

---

# Network Topology

```plaintext
PC1 ---- R1 ---- R2 ---- PC2
```

---

# IPv6 Addressing Scheme

| Device | Interface | IPv6 Address         |
| ------ | --------- | -------------------- |
| R1     | G0/0      | 2001:DB8:1:1::1/64   |
| R1     | G0/1      | 2001:DB8:12:12::1/64 |
| R2     | G0/1      | 2001:DB8:12:12::2/64 |
| R2     | G0/0      | 2001:DB8:2:2::1/64   |

---

# Key Concepts Covered

## 1. IPv6 Unicast Routing

IPv6 routing is disabled by default on Cisco routers.

To enable IPv6 forwarding:

```bash
ipv6 unicast-routing
```

Without this command, routers will not forward IPv6 packets between networks.

---

## 2. IPv6 Static Route Syntax

General syntax:

```bash
ipv6 route prefix/prefix-length next-hop
```

Example:

```bash
ipv6 route 2001:DB8:2:2::/64 2001:DB8:12:12::2
```

---

## 3. Link-Local Next Hop

When using a link-local address as the next-hop, the exit interface must also be specified.

Example:

```bash
ipv6 route 2001:DB8:2:2::/64 g0/1 FE80::2
```

This is required because link-local addresses are only valid on the local link.

---

## 4. IPv6 Default Route

IPv6 default route syntax:

```bash
ipv6 route ::/0 next-hop
```

Example:

```bash
ipv6 route ::/0 2001:DB8:12:12::2
```

Or using a link-local address:

```bash
ipv6 route ::/0 g0/1 FE80::2
```

---

# Verification Commands

## Verify IPv6 Routing Table

```bash
show ipv6 route
```

---

## Verify IPv6 Interfaces

```bash
show ipv6 interface brief
```

---

## Test IPv6 Connectivity

```bash
ping ipv6 2001:DB8:2:2::1
```

---

# Dual-Stack Operation

The lab also demonstrates dual-stack networking where IPv4 and IPv6 operate simultaneously on the same interfaces.

Example:

```bash
interface g0/0
 ip address 192.168.1.1 255.255.255.0
 ipv6 address 2001:DB8:1:1::1/64
```

---

# Key Takeaways

* IPv6 routing must be explicitly enabled
* Static routes manually define packet forwarding paths
* Link-local next hops require exit interfaces
* IPv6 default routes use `::/0`
* Verification commands are critical for troubleshooting
* IPv4 and IPv6 can coexist in modern enterprise networks

---

# Files Included

* `README.md`
* `ipv6-static-routing.pkt`

---

# Author

Stephen Musya Lungi

Focused on building strong foundations in:

* CCNA
* Linux Administration
* Azure Administration
* Enterprise Networking
