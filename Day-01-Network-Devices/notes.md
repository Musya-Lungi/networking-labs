# Day 1 - Notes (Raw Understanding)

## 🧠 Initial Understanding

- Switch uses MAC addresses to forward frames
- Router uses IP addresses to route between networks
- Access Point connects wireless devices to the network
- Modem connects the local network to the ISP
- Firewall filters traffic based on rules
- Hub broadcasts data to all ports (not used in modern networks)

---

## 🤔 Things I Had to Think About

- Difference between switch and router
- When a router is actually used (only between networks)
- Role of modem vs router
- Understanding that devices do not all "decide" equally in the flow

---

## ⚠️ Corrections / Clarifications

- Switch operates at Layer 2 (not Layer 3)
- Router does NOT handle communication within the same LAN
- Device sends traffic to router only when destination is outside the network (default gateway concept)
- Switch does not decide to send to router — the host does

---

## 🔁 Mental Model

- Switch = inside network (MAC-based)
- Router = between networks (IP-based)
- Modem = ISP boundary
- AP = wireless bridge
- Firewall = security control

---

## 📌 Things to Reinforce Later

- OSI model (to avoid confusion between layers)
- How MAC and IP work together
- Default gateway behavior
