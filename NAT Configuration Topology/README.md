# Cisco Packet Tracer - Static NAT and Dynamic NAT (PAT) Configuration

##  Overview

This project demonstrates the implementation of both **Static Network Address Translation (Static NAT)** and **Dynamic Network Address Translation (Dynamic NAT with PAT/Overload)** using Cisco Packet Tracer.

The topology consists of two private LANs connected through a router to a remote network hosting a server. The project shows how different NAT techniques allow internal private hosts to communicate with external networks using public IP addresses.

---

### Networks

| Network | Purpose |
|----------|---------|
| 192.168.1.0/24 | Static NAT LAN |
| 192.168.2.0/24 | Dynamic NAT (PAT) LAN |
| 200.1.1.0/24 | Public WAN Network |
| 172.16.1.0/24 | Remote Server Network |

---

##  Addressing Scheme

### Router 1

| Interface | IP Address | Description |
|------------|------------|-------------|
| G0/0 | 192.168.1.1/24 | Static NAT LAN |
| G0/1 | 192.168.2.1/24 | Dynamic NAT LAN |
| S0/3/0 | 200.1.1.1/24 | WAN (Outside Interface) |

### Router 2

| Interface | IP Address |
|------------|------------|
| S0/3/0 | 200.1.1.2/24 |
| G0/0 | 172.16.1.1/24 |

### Server

| Device | IP Address |
|---------|------------|
| Server1 | 172.16.1.x |

---

# NAT Configuration

## PAT (NAT Overload)

The **192.168.1.0/24** network is configured to use **Port Address Translation (PAT)**.

PAT allows multiple internal devices to share a single public IP address by translating both the source IP address and the source port number.

Router1 uses the public IP address assigned to its Serial0/3/0 interface for outbound traffic.

Configuration:

```cisco
access-list 1 permit 192.168.1.0 0.0.0.255

ip nat inside source list 1 interface Serial0/3/0 overload
```

---

## Dynamic NAT

The **192.168.2.0/24** network uses **Dynamic NAT**.

A pool of public IP addresses is configured, and each internal host is assigned an available address from the pool while communicating with external networks.

Public NAT Pool:

- 200.1.1.50
- 200.1.1.51
- ...
- 200.1.1.60

Configuration:

```cisco
ip nat pool DYNAMIC 200.1.1.50 200.1.1.60 netmask 255.255.255.0

access-list 2 permit 192.168.2.0 0.0.0.255

ip nat inside source list 2 pool DYNAMIC
```
---

## Public IP Usage

The public IP address

```
200.1.1.100
```

was used to successfully reach the remote server from both internal networks:

- 192.168.1.0/24 
- 192.168.2.0/24 

This demonstrates that:

- Static NAT provides a fixed one-to-one mapping.
- PAT allows multiple clients to share the same public IP.

---

## Verification

The following commands were used to verify the NAT configuration:

```
show ip nat translations

show running-config

```

---

## ✅ Results

- Successfully configured Static NAT using PAT.
- Successfully configured Dynamic NAT.
- Verified connectivity between internal hosts and the remote server.
- Confirmed NAT translations using Cisco IOS verification commands.
- Demonstrated one-to-one and many-to-one NAT translation.

---
