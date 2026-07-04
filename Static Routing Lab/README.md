# Static Routing Topology (Cisco Packet Tracer)

## Overview

This project demonstrates **Static Routing** using Cisco Packet Tracer. Three routers connect three separate Local Area Networks (LANs). Each LAN contains one switch and two PCs. Static routes are manually configured on each router to enable communication between all networks.

---

## Devices Used

| Device | Quantity |
|---------|---------:|
| Cisco 2911 Router | 3 |
| Cisco 2960 Switch | 3 |
| PC | 6 |

---

### Router-to-Router Links

| Link | Network | Router Interface | IP Address |
|------|---------|------------------|------------|
| R1 ↔ R2 | 10.0.12.0/30 | R1 G0/1 | 10.0.12.1 |
| | | R2 G0/1 | 10.0.12.2 |
| R2 ↔ R3 | 10.0.23.0/30 | R2 G0/2 | 10.0.23.1 |
| | | R3 G0/1 | 10.0.23.2 |

------

### PC Configuration

## LAN 1

| PC | IP Address | Subnet Mask | Default Gateway |
|----|------------|-------------|-----------------|
| PC1 | 192.168.1.2 | 255.255.255.0 | 192.168.1.1 |
| PC2 | 192.168.1.3 | 255.255.255.0 | 192.168.1.1 |

---

## LAN 2

| PC | IP Address | Subnet Mask | Default Gateway |
|----|------------|-------------|-----------------|
| PC3 | 192.168.2.2 | 255.255.255.0 | 192.168.2.1 |
| PC4 | 192.168.2.3 | 255.255.255.0 | 192.168.2.1 |

---

## LAN 3

| PC | IP Address | Subnet Mask | Default Gateway |
|----|------------|-------------|-----------------|
| PC5 | 192.168.3.2 | 255.255.255.0 | 192.168.3.1 |
| PC6 | 192.168.3.3 | 255.255.255.0 | 192.168.3.1 |

---

# Verification Commands

## Router

```plaintext
show ip interface brief
```

```plaintext
show ip route
```

---
