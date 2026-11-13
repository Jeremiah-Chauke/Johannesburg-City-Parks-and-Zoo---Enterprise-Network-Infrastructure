# JCPZ Network – VLAN and IP Addressing

## 1. Overview

The Johannesburg City Parks and Zoo (JCPZ) enterprise network uses Virtual Local Area Networks (VLANs) to logically separate departments, servers and voice traffic.

VLAN segmentation improves network organisation, reduces unnecessary broadcast traffic and provides a foundation for implementing network access controls and security policies.

Each VLAN is assigned a dedicated IPv4 subnet.

## 2. VLAN Allocation

The following VLANs are used in the network design:

| VLAN ID | VLAN Name | Purpose | IP Subnet |
|---|---|---|---|
| 10 | IT | Information Technology Department | 192.168.10.0/24 |
| 20 | Finance | Finance Department | 192.168.20.0/24 |
| 30 | Procurement | Procurement Department | 192.168.30.0/24 |
| 40 | HR | Human Resources Department | 192.168.40.0/24 |
| 50 | Marketing | Marketing Department | 192.168.50.0/24 |
| 60 | Servers | Centralised server environment | 192.168.60.0/24 |
| 70 | WAN | WAN and ISP connectivity | To be confirmed |
| 100 | Voice | IP telephony devices | 192.168.100.0/24 |

## 3. Default Gateway Configuration

The network uses two multilayer switches to provide inter-VLAN routing and gateway redundancy through Hot Standby Router Protocol (HSRP).

The HSRP virtual gateway address for the departmental, server and voice VLANs is configured as follows:

| VLAN | HSRP Virtual Gateway |
|---|---|
| 10 | 192.168.10.1 |
| 20 | 192.168.20.1 |
| 30 | 192.168.30.1 |
| 40 | 192.168.40.1 |
| 50 | 192.168.50.1 |
| 60 | 192.168.60.1 |
| 100 | 192.168.100.1 |

These virtual addresses provide a consistent default gateway for devices, even when the active multilayer switch changes.

## 4. DHCP Address Allocation

Dynamic Host Configuration Protocol (DHCP) is used to automatically assign IP addresses and other network settings to client devices.

The IT VLAN DHCP pool uses the following allocation range:

- Network: 192.168.10.0/24
- Default gateway: 192.168.10.1
- DHCP allocation range: 192.168.10.100 – 192.168.10.199

Other DHCP scopes are managed according to their respective VLAN configurations.

## 5. Inter-VLAN Routing

Inter-VLAN communication is facilitated by the multilayer switches.

Switch Virtual Interfaces (SVIs) provide Layer 3 gateway functionality for the different VLANs. HSRP provides gateway redundancy between the primary and secondary multilayer switches.

## 6. Benefits of VLAN Segmentation

The VLAN implementation provides the following benefits:

- Separates departmental network traffic.
- Reduces broadcast domains.
- Improves network organisation and management.
- Supports the implementation of access control policies.
- Separates server traffic from departmental traffic.
- Provides a dedicated VLAN for IP telephony.
- Supports improved network scalability.

## 7. Scope and Verification

This document describes the VLAN and IP addressing design used in the JCPZ network infrastructure project simulated in Cisco Packet Tracer.

IP addresses, DHCP scopes and gateway configurations should be verified against the final Packet Tracer configuration before deployment or use in a production environment.
