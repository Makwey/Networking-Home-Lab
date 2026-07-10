# Cisco Extended ACL Network Topology

## 📖 Overview

This project demonstrates the implementation of **Extended Access Control Lists (ACLs)** in a Cisco Packet Tracer network. The topology simulates a small enterprise environment consisting of multiple departments with different security requirements.

The objective is to control communication between VLANs/subnets while allowing access to essential network services such as the web server.

---

## 🖥️ Network Topology

![ACL Topology](topology.png)

### Network Layout

| Department | Network |
|------------|---------|
| Guest Network | `192.168.10.0/24` |
| HR Department | `192.168.20.0/24` |
| IT Department | `192.168.30.0/24` |
| Server Network | `192.168.40.0/24` |
| Router-to-Router WAN | `10.10.10.0/30` |

---

## 🎯 Objectives

- Configure Extended ACLs on Cisco routers.
- Restrict communication between departments.
- Protect critical servers.
- Allow only authorized traffic.
- Demonstrate best practices for ACL placement.

---

## 🛠 Devices Used

- Cisco Routers (2)
- Cisco Switches
- PCs
- DHCP Server
- Web Server
- Cisco Packet Tracer

---

## 🌐 IP Addressing

| Network | Purpose |
|----------|----------|
| 192.168.10.0/24 | Guest Users |
| 192.168.20.0/24 | HR Department |
| 192.168.30.0/24 | IT Department |
| 192.168.40.0/24 | Servers |
| 10.10.10.0/30 | WAN Link |

---

# ACL Policies

## Guest ACL

Guests are **not allowed** to communicate with the IT network or access the DHCP server.

Allowed:

- Internet/other permitted destinations
- Web Server (HTTP)
- Web Server (HTTPS)

Denied:

- IT Network
- DHCP Server

Configuration

```cisco
ip access-list extended Guest_ACL
 permit icmp 192.168.10.0 0.0.0.255 192.168.30.0 0.0.0.255 echo-reply
 deny ip 192.168.10.0 0.0.0.255 192.168.20.0 0.0.0.255
 deny ip 192.168.10.0 0.0.0.255 192.168.30.0 0.0.0.255
 deny ip 192.168.10.0 0.0.0.255 host 192.168.40.10
 permit tcp 192.168.10.0 0.0.0.255 host 192.168.40.20 eq 80
 permit tcp 192.168.10.0 0.0.0.255 host 192.168.40.20 eq 443
 permit ip 192.168.10.0 0.0.0.255 any
```

---

## HR ACL

HR users are restricted from accessing the IT network and the DHCP server while maintaining web access.

Allowed:

- Web Server (HTTP)
- Web Server (HTTPS)

Denied:

- IT Network
- DHCP Server

Configuration

```cisco
ip access-list extended HR_ACL
 permit icmp 192.168.20.0 0.0.0.255 192.168.30.0 0.0.0.255 echo-reply
 deny ip 192.168.20.0 0.0.0.255 192.168.30.0 0.0.0.255
 deny ip 192.168.20.0 0.0.0.255 host 192.168.40.10
 permit tcp 192.168.20.0 0.0.0.255 host 192.168.40.20 eq 80
 permit tcp 192.168.20.0 0.0.0.255 host 192.168.40.20 eq 443
 permit ip 192.168.20.0 0.0.0.255 any
```

---

## IT ACL

The IT department has unrestricted access for administration and troubleshooting.

```cisco
ip access-list extended IT_ACL
 permit ip 192.168.30.0 0.0.0.255 any
```

---

# Security Summary

| Source | HR | IT | DHCP | Web |
|---------|----|----|------|-----|
| Guest | ❌ | ❌ | ❌ | ✅ |
| HR | — | ❌ | ❌ | ✅ |
| IT | ✅ | ✅ | ✅ | ✅ |

---

## Verification Commands

Display configured ACLs

```cisco
show access-lists
```

View interface ACL assignments

```cisco
show ip interface
```

View routing table

```cisco
show ip route
```

Test connectivity

```text
ping
tracert
web browser (HTTP/HTTPS)
```

---

## Expected Results

✔ Guests cannot access HR or IT resources.

✔ Guests cannot access the DHCP server.

✔ Guests can browse the Web Server.

✔ HR cannot access the IT network.

✔ HR can access the Web Server.

✔ IT has full network access.

---

## Project Structure

```
Cisco-ACL-Topology/
│
├── ACL-Topology.pkt
├── topology.png
├── README.md
└── screenshots/
    ├── topology.png
    ├── guest-acl.png
    ├── hr-acl.png
    ├── verification.png
```

---

## Skills Demonstrated

- Cisco IOS CLI
- Extended ACL Configuration
- Router Configuration
- IP Addressing
- Network Segmentation
- Enterprise Network Security
- Packet Tracer
- Network Troubleshooting

---

## Author

**Your Name**

GitHub: https://github.com/yourusername
