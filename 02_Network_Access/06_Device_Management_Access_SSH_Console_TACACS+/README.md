# 06 — Device Management Access: SSH · Console · TACACS+

**Date:** Wednesday 21 May 2026
**Track:** Networking Fundamentals
**Path:** Learning Track → May-June → networking-labs → 02_Network_Access
**Duration:** 60 min theory + lab

---

## 📚 What I Learned Today

### Management Access Methods

Three ways to access a network device's management plane:

| Method | Type | Encrypted | Requires Physical Access | Use Case |
|--------|------|-----------|--------------------------|----------|
| Console | Direct cable (RJ-45) | N/A — direct wire | YES | Initial setup, emergency recovery |
| Telnet | Remote (TCP port 23) | ❌ NEVER — clear text | No | **Never use in production** |
| SSH v2 | Remote (TCP port 22) | ✅ Full encryption | No | Standard secure remote access |

**Key rule:** Telnet sends everything — including passwords — in plain readable text across the network. It must never be used in production environments.

---

### SSH Configuration Requirements (All 4 Mandatory)

```bash
# 1. Set hostname
Router(config)# hostname R1

# 2. Set domain name
R1(config)# ip domain-name company.com

# 3. Generate RSA crypto key (minimum 2048 bits)
R1(config)# crypto key generate rsa modulus 2048

# 4. Force SSH version 2
R1(config)# ip ssh version 2

# 5. Lock VTY lines to SSH only (block Telnet entirely)
R1(config)# line vty 0 15
R1(config-line)# transport input ssh
R1(config-line)# login local

# 6. Create a local user account
R1(config)# username admin privilege 15 secret StrongPassword123!

# Verify
R1# show ip ssh
```

> The crypto key is generated from `hostname + domain-name` combined.
> Without both set first, the key generation command fails.
> Never use modulus below 2048 — 512/1024 are crackable.

---

### AAA Framework

AAA is the framework that controls who gets in, what they can do, and logs everything they did.

| Letter | Question | Example |
|--------|----------|---------|
| **Authentication** | Who are you? | Verify username + password |
| **Authorisation** | What are you allowed to do? | Junior engineer: show commands only |
| **Accounting** | What did you do and when? | Full audit log of every command |

---

### TACACS+ vs RADIUS

| Feature | TACACS+ | RADIUS |
|---------|---------|--------|
| Transport | TCP port 49 | UDP port 1812/1813 |
| Encryption | Full packet | Password only |
| AAA separation | Yes — separate processes | No — auth + authz combined |
| Command authorisation | Yes — per command | Limited |
| Best for | **Device administration** | **Network access (WiFi, VPN)** |
| Cisco preferred? | ✅ Yes — for device admin | For 802.1X / network access |

**Rule of thumb:**
- Managing a router or switch → **TACACS+**
- Authenticating to WiFi or VPN → **RADIUS**

---

### Local Authentication vs Centralised AAA

| | Local | Centralised (TACACS+/RADIUS) |
|--|-------|-------------------------------|
| Setup complexity | Simple | More complex |
| Scales to 1000s of devices? | ❌ No | ✅ Yes |
| Central audit logs? | ❌ No | ✅ Yes |
| Instant account changes? | ❌ No | ✅ Yes |
| Works if AAA server is down? | ✅ Yes | ❌ Not without fallback |

**Enterprise best practice — use both:**

```bash
aaa new-model
aaa authentication login default group tacacs+ local
```

This tries TACACS+ first. If the server is unreachable, falls back to local accounts.
You get centralised management without the risk of being locked out.

---

## 🔑 Key Takeaways

- Console = physical lifeline, always works, use for initial config and emergencies
- Telnet = never use, passwords sent in clear text, must be blocked in production
- SSH = always use, encrypted, requires hostname + domain + crypto key + version 2
- AAA = Authentication (who) + Authorisation (what) + Accounting (log)
- TACACS+ = Cisco preferred for device administration, full encryption, per-command control
- RADIUS = industry standard for network access (WiFi, VPN, 802.1X)
- Local auth = fine for fallback, not scalable for enterprise
- Centralised AAA = enterprise standard, always configure local as fallback

---

## 🧪 Lab


### Lab Objectives
- [ ] Configure SSH on a Cisco router from scratch (all 4 steps)
- [ ] Block Telnet on VTY lines — SSH only
- [ ] Verify SSH with `show ip ssh`
- [ ] Capture Telnet vs SSH in Wireshark — observe clear text vs encrypted
- [ ] Configure local username with privilege 15
- [ ] (Stretch) Configure TACACS+ server and point a router to it

markdown### Lab Results — Completed 21 May 2026

#### Notes from the lab:
- Router model 4331 uses `crypto key generate rsa` then prompts separately
  for bit size — cannot pass `modulus 2048` inline on this model
- Interface naming on 4331 is `GigabitEthernet0/0/0` (three levels), not `g0/0`
- SSH `-l` flag is lowercase L (login), not the number 1
- `show users` shows live sessions on VTY lines — useful for monitoring who is connected

#### Verification outputs:

**show ip ssh**
SSH Enabled - version 2.0
Authentication timeout: 120 secs; Authentication retries: 3

**show users**

0 con 0   admin   idle   00:00:00
4 vty 0   admin   idle   00:00:25


**show running-config | section line vty**
line vty 0 4
login local
transport input ssh
line vty 5 15
login local
transport input ssh

#### Lab objectives:
- [x] Configure SSH on a Cisco router from scratch (all 4 steps)
- [x] Block Telnet on VTY lines — SSH only
- [x] Verify SSH with `show ip ssh`
- [x] Configure local username with privilege 15
- [x] Successfully SSH from PC to router
- [ ] Capture Telnet vs SSH in Wireshark — (not available in Packet Tracer)
- [ ] (Stretch) Configure TACACS+ server