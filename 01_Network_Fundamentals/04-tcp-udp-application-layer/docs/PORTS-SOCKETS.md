# Port Numbers & Sockets

## What is a Port?

A port is a logical identifier used by TCP/UDP to direct traffic to the correct application.

- IP address = identifies a device
- Port number = identifies a service on that device

---

## Common Well-Known Ports

| Service  | Port | Protocol |
|----------|------|----------|
| FTP      | 20/21 | TCP |
| SSH      | 22   | TCP |
| Telnet   | 23   | TCP |
| SMTP     | 25   | TCP |
| DNS      | 53   | UDP/TCP |
| DHCP     | 67/68 | UDP |
| HTTP     | 80   | TCP |
| HTTPS    | 443  | TCP |
| SNMP     | 161  | UDP |

---

## What is a Socket?

A socket is a combination of:

IP Address + Port Number

Example:
192.168.1.10:80

This uniquely identifies a communication endpoint.

---

## How Communication Works

Client → Server connection is defined by:
- Source IP + Source Port
- Destination IP + Destination Port