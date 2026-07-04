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

## IP Addressing Scheme

### LAN 1

| Device | Interface | IP Address | Subnet Mask |
|---------|-----------|------------|-------------|
| R1 | G0/0 | 192.168.1.1 | 255.255.255.0 |
| PC1 | NIC | 192.168.1.10 | 255.255.255.0 |
| PC2 | NIC | 192.168.1.11 | 255.255.255.0 |

Default Gateway:

```
192.168.1.1
```

---

### LAN 2

| Device | Interface | IP Address | Subnet Mask |
|---------|-----------|------------|-------------|
| R2 | G0/0 | 192.168.2.1 | 255.255.255.0 |
| PC3 | NIC | 192.168.2.10 | 255.255.255.0 |
| PC4 | NIC | 192.168.2.11 | 255.255.255.0 |

Default Gateway:

```
192.168.2.1
```

---

### LAN 3

| Device | Interface | IP Address | Subnet Mask |
|---------|-----------|------------|-------------|
| R3 | G0/0 | 192.168.3.1 | 255.255.255.0 |
| PC5 | NIC | 192.168.3.10 | 255.255.255.0 |
| PC6 | NIC | 192.168.3.11 | 255.255.255.0 |

Default Gateway:

```
192.168.3.1
```

---

### Router-to-Router Links

| Link | Network | Router Interface | IP Address |
|------|---------|------------------|------------|
| R1 ↔ R2 | 10.0.12.0/30 | R1 G0/1 | 10.0.12.1 |
| | | R2 G0/1 | 10.0.12.2 |
| R2 ↔ R3 | 10.0.23.0/30 | R2 G0/2 | 10.0.23.1 |
| | | R3 G0/1 | 10.0.23.2 |

------

# PC Configuration

## LAN 1

| PC | IP Address | Subnet Mask | Default Gateway |
|----|------------|-------------|-----------------|
| PC1 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC2 | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 |

---

## LAN 2

| PC | IP Address | Subnet Mask | Default Gateway |
|----|------------|-------------|-----------------|
| PC3 | 192.168.2.10 | 255.255.255.0 | 192.168.2.1 |
| PC4 | 192.168.2.11 | 255.255.255.0 | 192.168.2.1 |

---

## LAN 3

| PC | IP Address | Subnet Mask | Default Gateway |
|----|------------|-------------|-----------------|
| PC5 | 192.168.3.10 | 255.255.255.0 | 192.168.3.1 |
| PC6 | 192.168.3.11 | 255.255.255.0 | 192.168.3.1 |

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

## Connectivity Test

From **PC1**:

```plaintext
ping 192.168.2.10
```

```plaintext
ping 192.168.3.10
```

```plaintext
tracert 192.168.3.10
```

Expected result:

- All pings should succeed.
- Traceroute should pass through R2 before reaching R3.

---

# Learning Objectives

After completing this lab, you should be able to:

- Configure IP addresses on routers.
- Configure IP settings on PCs.
- Understand directly connected networks.
- Configure static routes.
- Verify routing tables.
- Test end-to-end connectivity.
- Troubleshoot routing issues using `show ip route`, `show ip interface brief`, `ping`, and `tracert`.

---

# Project Summary

- **Routing Protocol:** Static Routing
- **Routers:** 3
- **Switches:** 3
- **PCs:** 6
- **VLANs:** None
- **Routing Method:** Manual Static Routes
- **Goal:** Enable communication between three different LANs through manually configured routes.
