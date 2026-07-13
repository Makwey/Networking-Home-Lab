# Cisco Packet Tracer - Static NAT and Dynamic NAT Configuration

## Overview

This project demonstrates the implementation of both **Static NAT** and **Dynamic NAT (PAT/Overload)** using Cisco Packet Tracer.

The topology consists of two private LANs connected to a router that performs Network Address Translation (NAT). A second router connects the internal network to a remote server hosted on a different network.

The objective of this lab is to allow hosts from two private networks to communicate with a server using a public IP address while showcasing the differences between Static NAT and Dynamic NAT.

---

### Network Addressing

| Network | Purpose |
|----------|---------|
| **192.168.1.0/24** | Static NAT LAN |
| **192.168.2.0/24** | Dynamic NAT (PAT) LAN |
| **200.1.1.0/24** | Public WAN Network |
| **172.16.1.0/24** | Server Network |

---

## Topology Description

### Router 1

Router1 performs both NAT functions.

- **GigabitEthernet0/0**
  - IP: `192.168.1.1/24`
  - NAT Inside
  - Connected to Static NAT LAN

- **GigabitEthernet0/1**
  - IP: `192.168.2.1/24`
  - NAT Inside
  - Connected to Dynamic NAT LAN

- **Serial0/3/0**
  - IP: `200.1.1.1/24`
  - NAT Outside
  - Connected to Router2

---

### Router 2

- Serial Link
  - `200.1.1.2/24`

- LAN Interface
  - `172.16.1.1/24`

Connected to the server network.

---

### End Devices

#### Static NAT Network

- PC1
- PC2

Network:

```
192.168.1.0/24
```

#### Dynamic NAT Network

- PC3
- PC4

Network:

```
192.168.2.0/24
```

#### Server

```
172.16.1.100/24
```

---

# NAT Configuration

## Static NAT

The **192.168.1.0/24** network uses **Static NAT**.

A private IP address is permanently mapped to a public IP address.

Example:

```
Inside Local:
192.168.1.x

↓

Inside Global:
200.1.1.100
```

This allows hosts on the Static NAT network to be reachable through the same public IP address.

---

## Dynamic NAT (PAT)

The **192.168.2.0/24** network uses **Dynamic NAT with Overload (PAT)**.

Router1 translates multiple private addresses to public addresses using:

```
ip nat inside source list 1 interface Serial0/3/0 overload
```

The overload feature allows multiple hosts to share a single public interface IP by using different TCP/UDP port numbers.

---

## NAT Configuration Used

### NAT Inside Interfaces

```
interface GigabitEthernet0/0
 ip nat inside

interface GigabitEthernet0/1
 ip nat inside
```

### NAT Outside Interface

```
interface Serial0/3/0
 ip nat outside
```

### Dynamic NAT Pool

```
ip nat pool DYNAMIC 200.1.1.50 200.1.1.60 netmask 255.255.255.0
```

### PAT Configuration

```
ip nat inside source list 1 interface Serial0/3/0 overload
```

### Static NAT

```
ip nat inside source static 192.168.1.x 200.1.1.100
```

### Access Lists

```
access-list 1 permit 192.168.2.0 0.0.0.255
access-list 2 permit 192.168.1.0 0.0.0.255
```

---

# Connectivity Test

The following connectivity tests were successfully performed.

### Static NAT

- PC (192.168.1.0/24)
- Pinged the server using:

```
200.1.1.100
```

Result:

✅ Successful

---

### Dynamic NAT (PAT)

- PC (192.168.2.0/24)

Successfully accessed the remote network through PAT translation.

Result:

✅ Successful

---

# Verification Commands

Useful Cisco IOS commands used to verify NAT:

```
show ip nat translations
```

```
show ip nat statistics
```

```
show running-config
```

```
show access-lists
```

---

# Project Objectives

- Configure Static NAT
- Configure Dynamic NAT
- Configure PAT (NAT Overload)
- Understand Inside Local and Inside Global addresses
- Verify NAT translations
- Test end-to-end connectivity
- Implement basic enterprise-style network routing

---

# Skills Demonstrated

- Cisco IOS CLI
- Static NAT
- Dynamic NAT
- PAT (Port Address Translation)
- IPv4 Addressing
- Access Control Lists (ACL)
- Router Configuration
- Network Troubleshooting
- Cisco Packet Tracer

---

# Files Included

```
📁 Static-Dynamic-NAT-Lab
│
├── README.md
├── topology.png
├── router1-config.txt
├── router2-config.txt
└── Static_Dynamic_NAT.pkt
```

---

## Conclusion

This project demonstrates the successful implementation of both **Static NAT** and **Dynamic NAT (PAT)** in Cisco Packet Tracer. Two separate private networks (`192.168.1.0/24` and `192.168.2.0/24`) were translated to public addresses, enabling communication with a remote server across a WAN connection. The lab highlights how Static NAT provides a fixed public mapping, while PAT allows multiple internal hosts to share a single public IP efficiently, illustrating common NAT deployments used in enterprise networks.
