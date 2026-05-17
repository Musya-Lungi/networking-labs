# IPv6 Deep Dive — Address Types & Fundamentals

## Overview

IPv6 is a 128-bit addressing system designed to replace IPv4. It provides a vastly larger address space and improved network efficiency.

---

## IPv6 Address Types

### Global Unicast
- Internet-routable addresses
- Example: 2001:db8::/32

---

### Link-Local
- Used for local network communication only
- Automatically assigned
- Prefix: FE80::/10

---

### Loopback
- Self-reference address
- ::1

---

### Unspecified Address
- :: (all zeros)
- Used when no address is assigned

---

### Multicast
- Replaces broadcast in IPv6
- Starts with FF00::/8

---

### Anycast
- Same address assigned to multiple devices
- Traffic goes to nearest device

---

## Key IPv6 Concept

- IPv6 does NOT use broadcast
- Uses multicast instead