# Horizon Bank Westlands Branch - IPv4 Subnetting Plan

## 1. Address Space
- Base Network: 10.50.0.0/22
- Total usable range: 10.50.0.0 – 10.50.3.255

---

## 2. Department Requirements

| Department        | Hosts Required |
|------------------|---------------|
| Retail Banking   | 30            |
| Corporate Banking| 20            |
| IT & Operations  | 15            |
| Management       | 10            |

---

## 3. WAN Links
- WAN to Head Office (Point-to-Point)
- WAN to Disaster Recovery Site
- WAN to ATM Network

(Each WAN link will use /30 subnets)

---

## 4. Design Approach
- Use VLSM (Variable Length Subnet Masking)
- Allocate largest networks first
- Reserve space for future growth

---
## 5. VLSM Subnet Allocation

### 5.1 Retail Banking (30 Hosts)
- Network: 10.50.0.0/27
- Usable: 10.50.0.1 – 10.50.0.30
- Broadcast: 10.50.0.31

---

### 5.2 Corporate Banking (20 Hosts)
- Network: 10.50.0.32/27
- Usable: 10.50.0.33 – 10.50.0.62
- Broadcast: 10.50.0.63

---

### 5.3 IT & Operations (15 Hosts)
- Network: 10.50.0.64/28
- Usable: 10.50.0.65 – 10.50.0.78
- Broadcast: 10.50.0.79

---

### 5.4 Management (10 Hosts)
- Network: 10.50.0.80/28
- Usable: 10.50.0.81 – 10.50.0.94
- Broadcast: 10.50.0.95
