# Wireless WLAN Configuration Lab

# Lab Overview

This lab demonstrates foundational wireless LAN concepts including:

* WLAN setup
* SSID configuration
* WPA2-PSK security
* QoS prioritization
* BSS and ESS architecture
* Wireless client association process

---

# Lab Objectives

By the end of this lab, you should be able to:

* Understand wireless network architecture
* Configure wireless SSIDs
* Apply WPA2-PSK security
* Explain QoS in wireless environments
* Differentiate between BSS and ESS
* Describe the WPA2 authentication process

---

# Network Topology

```text
                INTERNET
                    |
                 ROUTER
                    |
                 SWITCH
                    |
         ---------------------
         |                   |
       AP1                 AP2
         |                   |
   Wireless Clients    Wireless Clients

SSID: CorpWiFi
Security: WPA2-PSK
Band: 5 GHz
```

---

# WLAN Configuration

## SSID Configuration

```text
SSID Name: CorpWiFi
Band: 5 GHz
Broadcast: Enabled
```

Purpose:

* Allows wireless clients to identify and connect to the network.

---

# WPA2-PSK Security

## Security Settings

```text
Security Mode: WPA2-Personal
Encryption: AES/CCMP
Password: SecurePass@2026
```

Purpose:

* Encrypt wireless communication
* Prevent unauthorized access

---

# QoS Configuration Concepts

Wireless QoS prioritizes traffic into categories:

| Queue       | Traffic Type         |
| ----------- | -------------------- |
| Voice       | VoIP calls           |
| Video       | Video conferencing   |
| Best Effort | Standard traffic     |
| Background  | Low priority traffic |

---

# BSS Example

Single access point deployment:

```text
      AP1
    /  |  \
 Client Client Client
```

Characteristics:

* Single wireless cell
* Small coverage area

---

# ESS Example

Multiple access points with same SSID:

```text
AP1 -------- AP2 -------- AP3
      SSID: CorpWiFi
```

Characteristics:

* Large coverage area
* Wireless roaming support

---

# Wireless Client Connection Process

## Step 1 — Scanning

The wireless client searches for available SSIDs.

---

## Step 2 — Authentication

The client provides WPA2 credentials.

---

## Step 3 — Association

The access point accepts the wireless client.

---

## Step 4 — WPA2 4-Way Handshake

Encryption keys are securely generated.

---

## Step 5 — Secure Communication

Encrypted wireless traffic begins.

---

# Verification Tasks

Verify the following:

* SSID visibility
* Successful wireless authentication
* Client IP address assignment
* Internet connectivity
* QoS traffic prioritization
* Roaming between access points

---

# Troubleshooting Checks

| Issue                  | Possible Cause             |
| ---------------------- | -------------------------- |
| Cannot connect         | Incorrect PSK              |
| Slow wireless          | Interference or congestion |
| Authentication failure | WPA mismatch               |
| Poor roaming           | Weak AP coverage           |

---

# Conclusion

This lab demonstrates core enterprise wireless networking concepts including WLAN deployment, WPA2 security, QoS implementation, and wireless client connectivity behavior.

These concepts form an important foundation for CCNA wireless networking studies.
