# IPv4 Addressing & Subnetting Fundamentals

## Overview
This module focuses on IPv4 addressing structure, binary representation, and subnetting logic used in enterprise networks for segmentation and routing decisions.

---

## Core Concepts

### IPv4 Address Structure
- 32-bit logical addressing system
- Divided into 4 octets
- Represented in dotted decimal format

### Binary Fundamentals
- IP addresses are processed in binary at the network level
- Each octet = 8 bits
- Understanding binary is essential for subnetting

### Subnetting Concept
- Used to divide large networks into smaller logical segments
- Improves performance, security, and routing efficiency
- Defined using subnet masks (CIDR notation)

---

## Network Decision Logic

A device determines packet forwarding based on:

- Same subnet → direct delivery via switch
- Different subnet → forwarded to default gateway (router)

---

## Practical Focus

- IPv4 to binary conversion
- Network vs host portion identification
- Basic subnet calculations (/24, /16, /8 understanding)
- Determining valid host ranges

---

## Lab Reference

All practical implementations are located in:

- `/lab` → Packet Tracer topology and configurations

---

## Key Takeaway

Subnetting is a **network design and traffic control mechanism** that defines how modern enterprise networks are structured.