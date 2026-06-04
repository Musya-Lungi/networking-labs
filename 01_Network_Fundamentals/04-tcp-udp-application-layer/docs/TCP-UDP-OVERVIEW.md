# TCP vs UDP Overview

## TCP (Transmission Control Protocol)

TCP is a connection-oriented protocol used when reliability is required.

### Key Features:
- 3-way handshake (SYN → SYN-ACK → ACK)
- Guarantees delivery of packets
- Orders data correctly using sequence numbers
- Uses acknowledgements (ACKs)
- Supports retransmission of lost packets
- Uses flow control (windowing)

### Use Cases:
- HTTP / HTTPS (web browsing)
- FTP (file transfer)
- SSH (remote login)
- Email (SMTP, IMAP)

---

## UDP (User Datagram Protocol)

UDP is a connectionless protocol focused on speed rather than reliability.

### Key Features:
- No connection setup
- No guarantee of delivery
- No sequencing or acknowledgements
- Very low overhead

### Use Cases:
- DNS (fast queries)
- DHCP (IP assignment)
- VoIP (calls)
- Video streaming
- Online gaming

---

## Key Difference

TCP = Reliable, slower, connection-based  
UDP = Fast, lightweight, no guarantee