🧪 OSPF DR/BDR Election Lab — Execution Guide
🎯 Objective

Understand how OSPF elects DR and BDR on a broadcast network and how routers form adjacencies.

🏗️ Topology Requirements
4 Routers (R1–R4)
1 Switch (Layer 2 broadcast domain)
Single subnet: 192.168.1.0/24
⚙️ Step 1 — Configure IP Addressing

Assign IPs:

R1 → 192.168.1.1
R2 → 192.168.1.2
R3 → 192.168.1.3
R4 → 192.168.1.4
⚙️ Step 2 — Enable OSPF

All routers:

router ospf 1
network 192.168.1.0 0.0.0.255 area 0
⚙️ Step 3 — Verify Neighbor Formation

Run:

show ip ospf neighbor

Expected behavior:

DR → FULL
BDR → FULL
DROTHER → 2-WAY
⚙️ Step 4 — Add Loopbacks

Create loopbacks:

R1 → 10.1.1.1/32
R2 → 10.2.2.2/32
R3 → 10.3.3.3/32
R4 → 10.4.4.4/32
⚙️ Step 5 — Advertise Loopbacks into OSPF
network 10.x.x.x 0.0.0.0 area 0
⚙️ Step 6 — Verify Routing Table
show ip route ospf