# Day 6 Runbook — Physical Layer, Cabling & Interface Troubleshooting

## Objective

Understand physical layer cabling types and diagnose interface errors caused by duplex mismatch and misconfiguration.

---

# Cabling Concepts

## Copper Cabling

- UTP (Unshielded Twisted Pair): most common Ethernet cabling
- STP (Shielded Twisted Pair): used in noisy environments
- Coaxial: legacy networking and broadband systems

---

## Ethernet Standards

| Cable Type | Speed | Max Distance |
|------------|-------|--------------|
| Cat5e | 1 Gbps | 100m |
| Cat6 | 10 Gbps | ~55m |
| Cat6a | 10 Gbps | 100m |

---

## Fiber Optic

- Single-mode: long distance, laser-based
- Multimode: short distance, LED-based

---

## SFP Modules

- Allow fiber connectivity on switches/routers
- Modular and replaceable

---

# Interface Errors

## CRC Errors
Indicate corrupted frames due to:
- cable issues
- interference
- duplex mismatch

---

## Input Errors
Includes:
- CRC errors
- frame errors
- runts

---

## Output Errors
Indicates transmission problems:
- congestion
- duplex mismatch

---

## Collisions

- Occur in half-duplex environments
- Caused by simultaneous transmission

---

## Late Collisions

- Strong indicator of duplex mismatch
- Occur when timing mismatch exists between devices

---

# Lab Observations

## Step 1: Baseline
- All interfaces clean
- No errors

## Step 2: Introduced Fault
- Duplex mismatch created between SW1 and SW2
- Errors observed:
  - collisions
  - late collisions
  - CRC errors

## Step 3: Diagnosis
- Used `show interfaces` to identify error types
- Confirmed mismatch as root cause

## Step 4: Fix
- Set both sides to full duplex
- Errors stopped increasing

---

# Key Commands Used
