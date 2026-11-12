# Johannesburg-City-Parks-and-Zoo---Enterprise-Network-Infrastructure

## 1. Project Overview

This project involves the design, implementation and simulation of a proposed enterprise network infrastructure for **Johannesburg City Parks and Zoo (JCPZ)** using Cisco Packet Tracer.

The project aims to establish a secure, reliable, scalable and highly available network infrastructure that supports communication between different organisational departments, provides access to centralised network services and maintains connectivity through redundant network components.

The infrastructure follows a hierarchical network architecture consisting of Core, Distribution and Access layers. It incorporates network segmentation, inter-VLAN routing, redundancy, WAN connectivity and centralised server resources.

## 2. Project Objectives

The main objectives of this project are to:

- Design a structured enterprise network infrastructure.
- Implement VLANs to logically segment departmental networks.
- Enable communication between departments through inter-VLAN routing.
- Improve network availability through redundant multilayer switches and network links.
- Implement First Hop Redundancy Protocol (HSRP) to provide gateway redundancy.
- Configure Spanning Tree Protocol (STP) to prevent switching loops.
- Establish redundant WAN connectivity through two Internet Service Providers (ISPs).
- Provide centralised network services through a dedicated server environment.
- Implement network security through segmentation, access control and controlled network access.
- Improve network scalability and simplify network administration.

## 3. Network Architecture

The proposed infrastructure follows a hierarchical network design consisting of three main layers.

### 3.1 Core and Distribution Layer

The core/distribution layer provides the central connectivity point for the enterprise network.

It consists of two Multilayer Switches (MLS):

- Primary Multilayer Switch
- Secondary Multilayer Switch

Responsibilities include:

- Inter-VLAN routing.
- Communication between departmental networks.
- Providing redundant default gateways using HSRP.
- Connecting departmental access switches.
- Connecting the central server environment.
- Providing redundant paths towards the network edge.

HSRP is implemented to maintain gateway availability if the active multilayer switch experiences a failure.

### 3.2 Access Layer

The access layer connects end-user devices and departmental resources to the enterprise network.

Each department has a dedicated Layer 2 access switch connecting devices such as:

- Desktop computers.
- IP phones.
- Laptops.
- Network printers.
- Wireless access points.

Redundant uplinks connect departmental switches to the primary and secondary multilayer switches.

### 3.3 WAN and Internet Connectivity

The WAN infrastructure provides external network connectivity through two Internet Service Providers.

The design incorporates multiple edge routers and redundant ISP connections to improve availability and reduce dependency on a single external connection.

The WAN infrastructure provides alternative connectivity paths in the event of a router, ISP or network-link failure.

## 4. VLAN and IP Addressing Scheme

Departmental networks are logically separated using Virtual Local Area Networks (VLANs).

| VLAN ID | Department | Network Address |
|---|---|---|
| 10 | IT | 192.168.10.0/24 |
| 20 | Finance | 192.168.20.0/24 |
| 30 | Procurement | 192.168.30.0/24 |
| 40 | Human Resources | 192.168.40.0/24 |
| 50 | Marketing | 192.168.50.0/24 |
| 60 | Server Environment | 192.168.60.0/24 |
| 70 | WAN / ISP Connectivity | As configured |
| 100 | Voice Network | 192.168.100.0/24 |

Each departmental VLAN operates within its own broadcast domain. Inter-VLAN communication is facilitated by the multilayer switches.

The VLAN 100 voice network provides a separate network segment for IP telephony.

## 5. Server Infrastructure

A dedicated server environment is incorporated into the network to provide centralised services.

The server environment includes:

- **DNS Server:** Provides name resolution for network resources.
- **DHCP Server:** Automatically assigns IP addresses and network configuration to client devices.
- **Web Server:** Hosts web-based services.
- **File Server:** Provides centralised file storage and sharing.
- **Backup Server:** Supports backup and recovery operations.

The server environment is connected through dedicated Layer 2 switches with redundant connectivity towards the core network.

## 6. Network Redundancy and High Availability

Network redundancy is a major component of the proposed infrastructure.

The following technologies and design principles are incorporated:

### HSRP (Hot Standby Router Protocol)
Provides default gateway redundancy between the primary and secondary multilayer switches.

### STP (Spanning Tree Protocol)
Prevents Layer 2 switching loops while maintaining redundant network paths.

### Redundant Uplinks
Departmental access switches have connections to both multilayer switches, reducing reliance on a single uplink.

### Redundant Server Connectivity
The server environment incorporates two Layer 2 switches to provide alternative connectivity paths.

### Dual ISP Connectivity
Two Internet Service Providers provide alternative external connectivity paths through the edge router infrastructure.

## 7. IP Telephony

The infrastructure also incorporates an IP telephony environment using Cisco IP Phones.

The voice network uses a dedicated Voice VLAN (VLAN 100), separating voice traffic from normal departmental data traffic.

The implementation includes:

- Dedicated voice VLAN configuration.
- DHCP address allocation for IP phones.
- DHCP Option 150 for TFTP server discovery.
- Cisco Call Manager Express (CME) configuration on an edge router.
- Ephone and ephone-dn configuration for assigning telephone extensions.
- IP phone registration and internal calling.

This allows users within the organisation to communicate using IP-based telephone services.

## 8. Network Technologies and Protocols

The project incorporates the following networking technologies:

| Technology | Purpose |
|---|---|
| VLANs | Departmental network segmentation |
| IPv4 | Network addressing |
| Subnetting | Efficient IP address allocation |
| Inter-VLAN Routing | Communication between VLANs |
| HSRP | Default gateway redundancy |
| STP | Prevention of Layer 2 switching loops |
| DHCP | Automatic IP address allocation |
| DHCP Relay | Forwarding DHCP requests between VLANs |
| DNS | Network name resolution |
| Trunking | Carrying multiple VLANs across links |
| WAN Routing | External network connectivity |
| IP Telephony | Internal voice communication |
| CME | IP phone registration and call management |

## 9. Security Considerations

The proposed infrastructure incorporates network security principles to improve the protection of organisational resources.

Security considerations include:

- Departmental network segmentation through VLANs.
- Controlled communication between network segments.
- Access Control Lists (ACLs) for restricting unauthorised traffic.
- Firewall integration at the network perimeter.
- Separation of server and user environments.
- Controlled access to network infrastructure devices.
- Redundant network components to improve service availability.

## 10. Tools and Technologies

The project uses the following tools and technologies:

- Cisco Packet Tracer – Network design, configuration and simulation.
- Cisco IOS – Router and switch configuration.
- IPv4 Addressing and Subnetting.
- VLAN and Trunk Configuration.
- HSRP and STP.
- DHCP and DNS.
- Routing and WAN Technologies.
- Cisco Call Manager Express (CME).

## 11. Expected Project Outcomes

The proposed network infrastructure is designed to achieve the following:

1. Improved communication between organisational departments.
2. Reduced broadcast traffic through VLAN segmentation.
3. Improved network availability through redundant infrastructure.
4. Centralised access to essential network services.
5. Improved management of departmental network resources.
6. Reliable internal IP-based communication.
7. Alternative Internet connectivity through dual ISP integration.
8. A scalable infrastructure capable of accommodating future network expansion.

## 12. Project Scope and Limitations

This project focuses specifically on the design, configuration and simulation of the JCPZ network infrastructure.

It covers network devices, connectivity, IP addressing, VLANs, routing, redundancy, server connectivity and network security considerations.

The project does not cover the development of business applications, database systems or other non-network business information systems.

The implementation is a simulated network environment developed using Cisco Packet Tracer. Actual production deployment would require physical infrastructure, security validation, testing and approval.

## 13. Author

**Jeremiah Chauke**

Diploma in Information Technology – Final Year  
Tshwane University of Technology

**Areas of Interest:**
- Network Infrastructure
- Cybersecurity
- Cloud Computing
- Network Administration
- IT Support

**GitHub:** https://github.com/Jeremiah-Chauke

---

*This project demonstrates practical knowledge of enterprise network architecture, Cisco networking technologies, network redundancy, infrastructure design and network administration.*

## License

Copyright (c) 2026 Jeremiah Chauke.

All rights reserved.

This repository is published for educational and
professional portfolio purposes.

No permission is granted to reproduce, distribute,
modify or commercially use this project's materials
without prior written permission from the copyright
holder.
