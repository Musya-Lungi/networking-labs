# OSPF Verification Commands

This document contains important verification and troubleshooting commands used when working with OSPF.

---

# 1. Verify OSPF Neighbor Relationships

```bash id="xj8k2n"
show ip ospf neighbor
```

Purpose:

* verifies OSPF adjacency formation
* displays neighboring routers
* confirms neighbor states

Expected Output:

```plaintext id="9vfdtr"
Neighbor ID     Pri   State           Dead Time   Address      Interface
2.2.2.2           1   FULL/DR         00:00:33    10.1.12.2    Gig0/1
```

Important States:

| State | Meaning                          |
| ----- | -------------------------------- |
| FULL  | OSPF adjacency fully established |
| INIT  | Hello packet received            |
| DOWN  | No hello packets received        |

---

# 2. Verify OSPF Routes

```bash id="qf1jmx"
show ip route ospf
```

Purpose:

* displays routes learned via OSPF
* confirms successful route exchange

Expected Route Indicator:

```plaintext id="l6v7od"
O
```

Example:

```plaintext id="58t4v5"
O    192.168.3.0/24 [110/2] via 10.1.12.2
```

Explanation:

| Value | Meaning                 |
| ----- | ----------------------- |
| O     | OSPF-learned route      |
| 110   | Administrative distance |
| 2     | OSPF metric (cost)      |

---

# 3. Verify OSPF Interfaces

```bash id="h98vl4"
show ip ospf interface brief
```

Purpose:

* displays interfaces participating in OSPF
* confirms interface states
* verifies area assignments

Useful For:

* identifying passive interfaces
* checking interface status
* troubleshooting adjacency issues

---

# 4. Verify OSPF Database

```bash id="1kq6ah"
show ip ospf database
```

Purpose:

* displays the Link-State Database (LSDB)
* shows received LSAs
* confirms topology information exchange

This command helps verify that routers share the same topology information.

---

# 5. Verify Running Configuration

```bash id="m8v9yb"
show running-config | section ospf
```

Purpose:

* displays OSPF-related configuration only
* quickly verifies router-id, networks, and passive interfaces

---

# 6. Verify Passive Interfaces

```bash id="n3ctsm"
show ip protocols
```

Purpose:

* verifies which interfaces are passive
* confirms routing protocol information
* displays OSPF timers and networks

---

# 7. Verify Interface IP Addresses

```bash id="4gr8tv"
show ip interface brief
```

Purpose:

* confirms interface addressing
* verifies interface operational state

Expected Status:

```plaintext id="u0g0b6"
up/up
```

---

# Common OSPF Troubleshooting Checks

If neighbors do not form, verify:

* interfaces are up
* correct IP addressing
* matching subnet masks
* matching area IDs
* matching hello/dead timers
* OSPF enabled on correct interfaces
* no interface shutdown
* proper network statements

---

# Key Takeaways

* OSPF neighbors must reach FULL state
* OSPF routes appear with the code "O"
* LSDB consistency is critical in OSPF
* Verification commands are essential for troubleshooting
* Most OSPF issues involve mismatched parameters

---
