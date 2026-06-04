# Interface Errors & Physical Layer Troubleshooting

## Overview

Interface errors indicate problems at the physical or data link layer. These are critical for diagnosing cabling, duplex, and hardware issues.

---

## CRC Errors (Cyclic Redundancy Check)

- Indicates corrupted frames
- Usually caused by:
  - bad cable
  - electromagnetic interference
  - faulty NIC or port

---

## Input Errors

- Total count of received errors
- Includes:
  - CRC errors
  - frame errors
  - runts (too small frames)

---

## Output Errors

- Errors occurring when sending frames
- Often caused by:
  - congestion
  - duplex mismatch
  - hardware issues

---

## Collisions

- Occur in half-duplex environments
- Two devices transmit at the same time
- Normal in hubs, not switches

---

## Late Collisions

- Occur when duplex mismatch exists
- One side full-duplex, other half-duplex
- Strong indicator of configuration problem

---

## Duplex Mismatch

### Symptoms:
- high collision count
- late collisions
- poor performance

### Cause:
- one side auto
- other side manually set

---

## Speed & Auto-Negotiation

- Devices negotiate speed and duplex automatically
- Failure leads to mismatches

---

## Key Diagnostic Command
