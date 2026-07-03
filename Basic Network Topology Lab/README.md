# Basic Network Topology - Cisco Packet Tracer

## Overview

This project demonstrates a basic LAN topology created using Cisco Packet Tracer. The purpose of this lab is to practice fundamental networking concepts such as IP addressing, switch communication, router configuration, and end-to-end connectivity.

---

## Objectives

- Build a basic network topology
- Configure IP addressing
- Configure router interfaces
- Verify device connectivity using ping
- Understand packet flow within a LAN

## Devices Used

| Device | Quantity |
|---------|---------:|
| Router | 1 |
| Switch | 1 |
| PCs | 5 |

## IP Addressing

| Device | IP Address | Subnet Mask | Default Gateway |
|---------|------------|-------------|-----------------|
| PC1 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC2 | 192.168.1.20 | 255.255.255.0 | 192.168.1.1 |
| PC3 | 192.168.1.30 | 255.255.255.0 | 192.168.1.1 |
| Router G0/0 | 192.168.1.1 | 255.255.255.0 | N/A |

## Verification

The following tests were performed:

- PC1 successfully pinged PC2
- PC2 successfully pinged PC3
- PCs successfully reached the router interface
- End-to-end connectivity verified

------
