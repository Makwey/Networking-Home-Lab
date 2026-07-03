# Networking-Home-Lab
This lab was created as part of my self-learning journey toward becoming a Network Engineer.

------

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

# Inter-VLAN Routing using Router-on-a-Stick

## Overview

This project demonstrates inter-VLAN routing using a Cisco router configured with Router-on-a-Stick.

## Network Devices

- 1 Cisco Router
- 1 Core Switch
- 6 Access Switches
- 12 PCs

## VLANs

| VLAN | Department | Network |
|------|------------|--------------|
|10|Sales|192.168.10.0/24|
|20|HR|192.168.20.0/24|
|30|IT|192.168.30.0/24|
|40|Finance|192.168.40.0/24|
|50|Marketing|192.168.50.0/24|
|60|Admin|192.168.60.0/24|

## Features

- Router-on-a-Stick configuration
- IEEE 802.1Q trunking
- Inter-VLAN routing
- End-to-end connectivity across six VLANs

## Verification

- Successful ping from VLAN 10 to VLAN 60
- Trunk links verified using `show interfaces trunk`
- VLAN assignments verified using `show vlan brief`
- Router subinterfaces verified using `show ip interface brief`

------
