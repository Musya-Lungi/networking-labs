# Day 4 Lab Topology Design

## Objective
Observe how DNS (UDP) and HTTP (TCP) work in a real network using Packet Tracer simulation mode.

---

## Devices Required

- 1 Router
- 1 Switch
- 2 PCs
- 1 DNS Server
- 1 HTTP Server

---

## IP Addressing Plan

### Network: 192.168.1.0/24

- Router: 192.168.1.1
- PC1: 192.168.1.10
- PC2: 192.168.1.11
- DNS Server: 192.168.1.100
- HTTP Server: 192.168.1.50

---

## Services

### DNS Server
- Domain: server.local
- Maps to: 192.168.1.50

### HTTP Server
- Web service enabled
- Simple homepage active

---

## Traffic Flow to Observe

1. PC → DNS request (UDP port 53)
2. DNS response returns IP
3. PC → HTTP request (TCP port 80)
4. TCP 3-way handshake occurs
5. Web page loads