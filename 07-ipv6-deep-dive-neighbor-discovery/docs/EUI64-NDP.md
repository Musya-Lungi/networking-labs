# IPv6 EUI-64 & Interface ID Formation

## What is EUI-64?

EUI-64 is a method used to automatically generate the 64-bit Interface ID portion of an IPv6 address from a device’s 48-bit MAC address.

---

## Why EUI-64 exists

It allows:
- automatic IPv6 configuration
- unique interface identification
- reduced manual configuration

---

## How EUI-64 Works (Step-by-Step)

Given a MAC address:

AA:BB:CC:DD:EE:FF

### Step 1 — Split MAC into two halves
AA:BB:CC  |  DD:EE:FF

---

### Step 2 — Insert FFFE in the middle

AA:BB:CC:FF:FE:DD:EE:FF

---

### Step 3 — Flip the 7th bit (Universal/Local bit)

This modifies the first byte:
- If 0 → becomes 1
- If 1 → becomes 0

---

## Result

You now have a 64-bit Interface ID.

---

## Example IPv6 Address Formation

Network Prefix:
2001:DB8:ACAD:1::/64

Interface ID (from EUI-64):
AA:BB:CC:FF:FE:DD:EE:FF

Final IPv6 Address:
2001:DB8:ACAD:1:A8BB:CCFF:FEDD:EEFF

---

## Key Takeaway

- IPv6 splits address into:
  - 64-bit network prefix
  - 64-bit interface ID

- EUI-64 automates interface ID creation