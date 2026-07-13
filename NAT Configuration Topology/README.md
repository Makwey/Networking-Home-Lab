# Cisco Packet Tracer - Static NAT and Dynamic NAT Configuration

## 📌 Project Overview

This project demonstrates the implementation of both **Static NAT** and **Dynamic NAT** using Cisco Packet Tracer. The topology consists of two separate internal LANs connected to an external network through a Cisco router. One LAN uses Static NAT for a dedicated internal host, while the other LAN uses Dynamic NAT with a configured address pool.

This project showcases practical knowledge of:
- Static Network Address Translation (Static NAT)
- Dynamic Network Address Translation (Dynamic NAT)
- NAT Overload (PAT)
- Access Control Lists (ACLs)
- Basic Routing
- Cisco IOS Configuration

---

## 🖥️ Network Topology

```
                    External Network
               172.16.1.0/24 (Server)

                        |
                   Router2
                        |
              200.1.1.0/24 WAN
                        |
                   Router1
                  /        \
                 /          \
      Static NAT LAN     Dynamic NAT LAN
     192.168.1.0/24      192.168.2.0/24
```

### Network Devices

| Device | Network | Purpose |
|---------|----------|---------|
| Router1 | Edge Router | NAT Configuration |
| Router2 | WAN Router | Connects to Server |
| Switch1 | 192.168.1.0/24 | Static NAT LAN |
| Switch2 | 192.168.2.0/24 | Dynamic NAT LAN |
| PC1 & PC2 | 192.168.1.0/24 | Static NAT Clients |
| PC3 & PC4 | 192.168.2.0/24 | Dynamic NAT Clients |
| Server | 172.16.1.0/24 | External Network |

---

# IP Addressing

| Interface | IP Address |
|-----------|------------|
| Router1 G0/0 | 192.168.1.1/24 |
| Router1 G0/1 | 192.168.2.1/24 |
| Router1 S0/3/0 | 200.1.1.1/24 |
| Router2 S0/3/0 | 200.1.1.100/24 |
| Server | 172.16.1.x/24 |

---

# NAT Configuration

## Static NAT

The **192.168.1.0/24** network is configured for Static NAT.

A private IP address is permanently mapped to a public IP address, allowing consistent external access.

Example:

```text
Inside Local: 192.168.1.x
        ↓
Inside Global: Public IP
```

Use Cases:
- Web Servers
- Mail Servers
- DNS Servers

---

## Dynamic NAT

The **192.168.2.0/24** network uses Dynamic NAT.

Router1 is configured with the following NAT pool:

```text
Pool Name: DYNAMIC

Start:
200.1.1.50

End:
200.1.1.60
```

The router assigns an available public IP from the pool whenever an internal device initiates outbound communication.

Configuration:

```cisco
ip nat pool DYNAMIC 200.1.1.50 200.1.1.60 netmask 255.255.255.0
ip nat inside source list 2 pool DYNAMIC
```

---

## NAT Overload (PAT)

The Static NAT network also demonstrates Port Address Translation (PAT), allowing multiple devices to share a single public interface.

```cisco
ip nat inside source list 1 interface Serial0/3/0 overload
```

PAT conserves public IP addresses by distinguishing traffic using TCP/UDP port numbers.

---

# Access Control Lists

ACLs define which internal networks are eligible for NAT translation.

```cisco
access-list 1 permit 192.168.1.0 0.0.0.255
access-list 2 permit 192.168.2.0 0.0.0.255
```

---

# Router1 Configuration Summary

### Inside Interfaces

```text
GigabitEthernet0/0
192.168.1.1

GigabitEthernet0/1
192.168.2.1
```

Marked as:

```cisco
ip nat inside
```

### Outside Interface

```text
Serial0/3/0
200.1.1.1
```

Marked as:

```cisco
ip nat outside
```

---

# Routing

Static route configured on Router1:

```cisco
ip route 172.16.1.0 255.255.255.0 200.1.1.2
```

This enables communication with the external server network.

---

# Verification Commands

Useful IOS commands for testing:

```cisco
show ip nat translations

show ip nat statistics

show running-config

show ip route

ping

traceroute
```

---

# Learning Objectives

Through this project, I learned how to:

- Configure Static NAT
- Configure Dynamic NAT
- Configure PAT (NAT Overload)
- Create NAT Pools
- Configure ACLs for NAT
- Assign Inside and Outside NAT Interfaces
- Configure Static Routes
- Verify NAT translations
- Test end-to-end connectivity

---

# Skills Demonstrated

- Cisco Packet Tracer
- Cisco IOS CLI
- Network Address Translation (NAT)
- Dynamic NAT
- Static NAT
- PAT (Port Address Translation)
- IPv4 Routing
- ACL Configuration
- Network Troubleshooting

---

# Project Files

```
📁 Static-Dynamic-NAT
│
├── README.md
├── Static_Dynamic_NAT.pkt
├── topology.png
├── router1-config.png
└── screenshots/
```

---

# Author

**Your Name**

Networking Student | Cisco Packet Tracer | CCNA Practice Labs

GitHub: https://github.com/yourusername
