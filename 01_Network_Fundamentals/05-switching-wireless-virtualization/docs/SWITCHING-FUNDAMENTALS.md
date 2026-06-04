# Switching Fundamentals

## MAC Address Learning

A switch learns MAC addresses by examining the source MAC address of incoming Ethernet frames.

The switch stores learned MAC addresses inside the MAC address table together with the associated port.

Example:
- PC1 frame enters Fa0/1
- Switch learns:
  - MAC Address → Fa0/1

---

## Forwarding Decisions

### Known Unicast
If destination MAC exists in MAC table:
- Forward only to the correct port

### Unknown Unicast
If destination MAC is unknown:
- Flood frame to all ports except incoming port

### Broadcast
Broadcast frames are flooded to all ports.

Example:
FF:FF:FF:FF:FF:FF

### Multicast
Frames intended for a group of devices.

---

## MAC Address Table Aging

Switches remove stale MAC entries automatically.

Default aging timer:
- 300 seconds

This prevents outdated forwarding information.

---

## Duplex Communication

### Half-Duplex
- Devices cannot send and receive simultaneously
- Uses CSMA/CD
- Collisions possible
- Common with hubs

### Full-Duplex
- Simultaneous send and receive
- No collisions
- Used by modern switches