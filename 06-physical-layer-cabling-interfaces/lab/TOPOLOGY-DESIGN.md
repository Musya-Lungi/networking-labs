# Day 6 Lab Topology — Physical Layer & Interface Errors

## Objective

Learn how physical layer issues and duplex mismatches create interface errors and performance degradation.

---

## Devices

- 2 Switches (SW1, SW2)
- 2 PCs (PC1, PC2)

---

## Network

192.168.1.0/24

---

## IP Plan

| Device | IP Address |
|--------|------------|
| PC1 | 192.168.1.10 |
| PC2 | 192.168.1.11 |

Subnet Mask:
255.255.255.0

---

## Topology Design

- PC1 → SW1 Fa0/1
- SW1 Fa0/24 → SW2 Fa0/24
- PC2 → SW2 Fa0/1

---

## Lab Concept

We will intentionally simulate:
- duplex mismatch
- interface errors (CRC, late collisions)
- cabling/physical layer issues

---

## Learning Goals

- Understand show interfaces output
- Identify physical layer failures
- Fix duplex mismatches
- Observe error counters in real time