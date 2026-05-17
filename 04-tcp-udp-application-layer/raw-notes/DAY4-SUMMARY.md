# Day 4 Summary — TCP vs UDP + Application Layer

## What I Built
- DNS Server (UDP 53)
- HTTP Server (TCP 80)
- Client PCs accessing services via hostname

---

## What I Observed

### DNS (UDP)
- Fast request/response
- No handshake
- Stateless communication

### HTTP (TCP)
- 3-way handshake observed
- Reliable session setup
- Ordered data transfer

---

## Key Concepts Learned

- TCP = connection-oriented, reliable
- UDP = connectionless, fast
- DNS uses UDP for speed
- HTTP uses TCP for reliability
- Socket = IP + Port

---

## Real Network Flow

1. DNS Query (UDP 53)
2. DNS Response
3. TCP 3-way handshake
4. HTTP GET request
5. Web page delivered