# Cisco Extended ACL Network Topology

## Overview

This project demonstrates the implementation of **Extended Access Control Lists (ACLs)** in a Cisco Packet Tracer network. The topology simulates a small enterprise environment consisting of multiple departments with different security requirements.

The objective is to control communication between VLANs/subnets while allowing access to essential network services such as the web server.

---

### Network Layout

| Department | Network |
|------------|---------|
| Guest Network | `192.168.10.0/24` |
| HR Department | `192.168.20.0/24` |
| IT Department | `192.168.30.0/24` |
| Server Network | `192.168.40.0/24` |
| Router-to-Router WAN | `10.10.10.0/30` |

---

# Security Summary

| Source | HR | IT | DHCP | Web |
|---------|----|----|------|-----|
| Guest | ❌ | ❌ | ❌ | ✅ |
| HR | ✅ | ❌ | ❌ | ✅ |
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
