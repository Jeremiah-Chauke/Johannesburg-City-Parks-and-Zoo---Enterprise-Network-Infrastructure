# JCPZ Network – Server Configuration and Infrastructure

## 1. Overview

The Johannesburg City Parks and Zoo (JCPZ) enterprise network incorporates a centralised server environment to provide essential network services to users and devices across the organisation.

The server infrastructure is located within the dedicated Server VLAN (VLAN 60), which separates server traffic from departmental network traffic.

The proposed server environment consists of five servers providing DNS, DHCP, Web, File and Backup services.

## 2. Server Infrastructure

The server environment consists of the following servers:

| Server | Function | IP Address |
|---|---|---|
| DNS Server | Domain Name System services | 192.168.60.2 |
| DHCP Server | Dynamic Host Configuration Protocol services | 192.168.60.3 |
| Web Server | Hosts internal web services | 192.168.60.4 |
| File Server | Centralised file storage and sharing | 192.168.60.5 |
| Backup Server | Stores backup copies of important data | 192.168.60.6 |

**Note:** Confirm these IP addresses against the final Cisco Packet Tracer configuration before treating them as the definitive server addressing plan.

## 3. DNS Server

The Domain Name System (DNS) server provides name resolution services within the network.

DNS translates human-readable hostnames and domain names into IP addresses, allowing users and network devices to access services without having to remember numerical IP addresses.

### Responsibilities

- Resolves hostnames to IP addresses.
- Supports access to internal network services.
- Simplifies communication between network devices and servers.
- Reduces the need for users to manually enter IP addresses.

## 4. DHCP Server

The Dynamic Host Configuration Protocol (DHCP) server automatically assigns IP configuration information to client devices.

This reduces manual configuration and helps ensure that devices receive appropriate network settings according to their assigned VLAN.

### DHCP Responsibilities

- Automatically assigns IP addresses.
- Provides subnet mask information.
- Supplies default gateway addresses.
- Provides DNS server information.
- Supports DHCP Option 150 for IP telephony and TFTP server discovery.

### DHCP Relay Configuration

Since the DHCP server is located in VLAN 60 while client devices operate in different VLANs, DHCP relay functionality is configured on the multilayer switches.

The `ip helper-address` command forwards DHCP requests from client VLANs to the centralised DHCP server.

Example:

```cisco
interface Vlan100
 ip helper-address 192.168.60.3
```

The relay configuration allows devices in VLAN 100 (Voice) to obtain their IP configuration from the DHCP server in VLAN 60.

## 5. Web Server

The Web Server provides hosting capabilities for web-based services within the simulated enterprise network.

It allows users to access hosted web content through a web browser using the server's IP address or configured hostname.

### Responsibilities

- Hosts web pages and internal web content.
- Provides HTTP-based access to hosted resources.
- Demonstrates centralised web hosting within the enterprise network.

## 6. File Server

The File Server provides centralised storage and file-sharing capabilities.

It is intended to allow authorised users to access shared files and organisational resources through the network.

### Responsibilities

- Provides centralised file storage.
- Supports file sharing between authorised users.
- Helps organise shared organisational resources.
- Reduces reliance on individual workstation storage.

## 7. Backup Server

The Backup Server provides storage for backup copies of important files and data.

Its purpose is to support data recovery and reduce the impact of accidental data loss or system failures.

### Responsibilities

- Stores backup copies of important data.
- Supports data recovery procedures.
- Provides an additional location for protected copies of files.
- Contributes to business continuity planning.

## 8. Server Network Connectivity

All five servers are located within VLAN 60 (Servers), using the network:

- Network address: 192.168.60.0/24
- Subnet mask: 255.255.255.0
- Default gateway: 192.168.60.1

The server environment uses two Layer 2 switches to provide alternative network connectivity paths.

The switches connect to the multilayer switching infrastructure, allowing servers to communicate with authorised departmental devices and network services.

## 9. Server Security Considerations

The server environment should be protected through appropriate network security controls.

Recommended measures include:

- Restricting access to servers through Access Control Lists (ACLs).
- Allowing only authorised users to access shared resources.
- Limiting unnecessary services and open ports.
- Using secure administrative credentials.
- Maintaining regular backups.
- Monitoring server availability and network traffic.
- Separating server traffic from departmental user traffic through VLAN segmentation.

## 10. Testing and Verification

The following tests can be performed in Cisco Packet Tracer to verify server connectivity and functionality:

| Test | Expected Result |
|---|---|
| Ping the DNS server | Server responds to network connectivity tests |
| Request an IP address through DHCP | Client receives valid network configuration |
| Test DHCP relay from another VLAN | Client receives an address from the central DHCP server |
| Access the Web Server | Hosted web content is accessible |
| Test file server connectivity | File server is reachable |
| Test Backup Server connectivity | Backup server is reachable |

Useful verification commands include:

```cisco
show ip interface brief
show running-config
show ip route
show vlan brief
```

## 11. Conclusion

The centralised server infrastructure provides essential network services to support communication, resource sharing and service accessibility across the proposed JCPZ enterprise network.

By separating servers into a dedicated VLAN and connecting them through redundant switching infrastructure, the design improves network organisation, manageability and resilience.

This infrastructure is designed and simulated in Cisco Packet Tracer for educational and demonstration purposes.
