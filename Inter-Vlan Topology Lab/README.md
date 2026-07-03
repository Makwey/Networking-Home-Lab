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
