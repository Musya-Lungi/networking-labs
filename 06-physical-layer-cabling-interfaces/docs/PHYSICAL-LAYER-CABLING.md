# Physical Layer — Cabling Types & Standards

## Overview

The physical layer defines how bits are transmitted over physical media such as copper, fiber, and wireless.

---

## Copper Cabling Types

### UTP (Unshielded Twisted Pair)
- Most common Ethernet cable type
- Affordable and widely used
- Susceptible to interference

### STP (Shielded Twisted Pair)
- Has shielding to reduce interference
- Used in noisy environments

### Coaxial Cable
- Older networking standard
- Still used in broadband and CCTV systems

---

## Ethernet Cable Categories

| Category | Speed | Distance |
|----------|-------|----------|
| Cat5e | 1 Gbps | 100m |
| Cat6 | 10 Gbps | ~55m |
| Cat6a | 10 Gbps | 100m |

---

## Straight-through vs Crossover

### Straight-through
- Different device types
- PC → Switch
- Switch → Router

### Crossover
- Same device types (older standard)
- Switch → Switch
- PC → PC

Modern switches support Auto-MDIX so cable type is automatically detected.

---

## Fiber Optic Cables

### Single-mode fiber
- Long distance communication
- Uses laser light
- Yellow color

### Multimode fiber
- Shorter distances
- Uses LED light
- Orange or aqua color

---

## SFP Modules

Small Form-factor Pluggable modules:
- Allow fiber connections on switches/routers
- Can be replaced without changing hardware

---

## Key Physical Layer Idea

Physical layer issues often appear as:
- Packet loss
- CRC errors
- Interface instability
- Slow or inconsistent performance