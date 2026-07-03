# DHCP Pooling Topology in Cisco Packet Tracer

## Overview

This project demonstrates the configuration of a DHCP server on a Cisco router using three separate DHCP pools. Each pool serves a different network, allowing client devices to automatically obtain their IP addresses, subnet masks, and default gateways.

---

## Network Topology

text
                 Router (R1)
      G0/0      G0/1      G0/2
        |          |          |
      Switch1    Switch2    Switch3
        |          |          |
      PC1-PC3    PC4-PC6    PC7-PC9


---

## Network Addressing

| Network | Interface | Network Address | Default Gateway | Subnet Mask |
|---------|-----------|-----------------|-----------------|-------------|
| Network 1 | G0/0 | 192.168.10.0/24 | 192.168.10.1 | 255.255.255.0 |
| Network 2 | G0/1 | 192.168.20.0/24 | 192.168.20.1 | 255.255.255.0 |
| Network 3 | G0/2 | 192.168.30.0/24 | 192.168.30.1 | 255.255.255.0 |

---

## PC Configuration

Configure each PC to obtain its IP address automatically:

1. Open **Desktop**.
2. Select **IP Configuration**.
3. Click **DHCP**.

Each PC will automatically receive:
- IP Address
- Subnet Mask
- Default Gateway

---

## Verification Commands

Check DHCP leases:
show ip dhcp binding

View DHCP pool information:
show ip dhcp pool

Display the router configuration:
plaintext
show running-config

---

## Expected Results

- PCs connected to **Switch1** receive addresses from the **192.168.10.0/24** network.
- PCs connected to **Switch2** receive addresses from the **192.168.20.0/24** network.
- PCs connected to **Switch3** receive addresses from the **192.168.30.0/24** network.
- All client devices receive their network configuration dynamically through DHCP.

------
