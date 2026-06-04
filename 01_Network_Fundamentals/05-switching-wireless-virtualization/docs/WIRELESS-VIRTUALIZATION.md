# Wireless Fundamentals & Virtualization

## Wireless Frequency Bands

### 2.4 GHz
- Longer range
- More interference
- Fewer non-overlapping channels

### 5 GHz
- Faster speeds
- Less interference
- Shorter range

---

## Non-Overlapping Channels

For 2.4 GHz wireless networks, the recommended non-overlapping channels are:

- Channel 1
- Channel 6
- Channel 11

These channels reduce signal interference.

---

## Wireless Terminology

### SSID
Wireless network name visible to users.

### BSS (Basic Service Set)
A single wireless access point and connected clients.

### ESS (Extended Service Set)
Multiple access points sharing the same SSID.

### BSSID
Unique MAC address identifying an access point.

---

# Virtualization

## Virtual Machines (VMs)

Virtual machines allow multiple operating systems to run on one physical machine.

---

## Type 1 Hypervisor

Runs directly on hardware.

Examples:
- VMware ESXi
- Microsoft Hyper-V

---

## Type 2 Hypervisor

Runs on top of an operating system.

Examples:
- VirtualBox
- VMware Workstation

---

## Containers

Containers share the host operating system kernel.

Examples:
- Docker
- Kubernetes

Containers are lightweight compared to VMs.

---

## VRF (Virtual Routing and Forwarding)

VRF allows multiple routing tables to exist on the same router.

Used for network segmentation in enterprise environments.