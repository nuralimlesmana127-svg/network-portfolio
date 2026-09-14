# Enterprise Network Lab

A network simulation project built using PNETLab to practice
enterprise network configuration and troubleshooting.

## Technologies

- Cisco IOL L2/L3
- PNETLab
- VLAN
- 802.1Q Trunking
- Router-on-a-Stick
- OSPF
- OSPF MD5 Authentication
- IPv4 Subnetting

## Network Topology

[Topology Image]

## Network Architecture

The topology consists of:

- 6 routers
- 6 Layer-2 switches
- 12 end devices
- OSPF-based core network
- Multiple VLAN segments

## Routing

OSPF is implemented on the router core using:

- Area 0 for the core network
- Area 1 for LAN networks
- OSPF MD5 authentication on core links
- Passive interfaces for LAN-facing interfaces

## Core Links

| Link | Network |
|---|---|
| R1-R2 | 12.12.12.0/30 |
| R2-R3 | 23.23.23.0/30 |
| R3-R4 | 34.34.34.0/30 |
| R4-R6 | 46.46.46.0/30 |
| R6-R5 | 56.56.56.0/30 |
| R5-R1 | 51.51.51.0/30 |

## VLANs

| VLAN | Network | Gateway |
|---|---|---|
| 11 | 192.168.11.0/24 | 192.168.11.1 |
| 12 | 192.168.12.0/24 | 192.168.12.1 |
| 13 | 192.168.13.0/24 | 192.168.13.1 |
| ... | ... | ... |

## Verification

OSPF neighbor relationships were successfully established
between all routers.

Example:

`show ip ospf neighbor`

All core neighbors reached the `FULL` state.

Connectivity was verified using ICMP ping between router
interfaces and network segments.

## Troubleshooting

During implementation, several issues were identified and resolved,
including:

- Incorrect physical Ethernet mapping
- OSPF authentication mismatch
- Case-sensitive MD5 authentication key
- Incorrect VLAN subinterface placement

## Learning Outcomes

This project demonstrates practical skills in:

- Network topology design
- IPv4 addressing
- VLAN configuration
- Trunk configuration
- Inter-VLAN routing
- OSPF configuration
- OSPF authentication
- Network troubleshooting
