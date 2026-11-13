# JCPZ Network – Redundancy and High Availability

## 1. Overview

The Johannesburg City Parks and Zoo (JCPZ) enterprise network infrastructure is designed with redundancy and high availability in mind. Redundancy is implemented to minimise single points of failure, improve network availability and maintain communication between network devices and users.

The proposed network design incorporates redundant multilayer switches, redundant network links, Spanning Tree Protocol (STP), Hot Standby Router Protocol (HSRP), redundant server connectivity and dual Internet Service Provider (ISP) connections.

## 2. Multilayer Switch Redundancy

The network uses two multilayer switches:

- Primary Multilayer Switch
- Secondary Multilayer Switch

Both switches provide Layer 3 routing functionality and serve as gateways for the departmental, server and voice VLANs.

The switches are configured to provide gateway redundancy using Hot Standby Router Protocol (HSRP).

This ensures that if the active multilayer switch becomes unavailable, the standby switch can take over the gateway responsibility.

## 3. Hot Standby Router Protocol (HSRP)

HSRP is implemented to provide default gateway redundancy for the network VLANs.

The protocol allows two multilayer switches to share a virtual IP address that is used as the default gateway by connected devices.

The primary multilayer switch is configured with a higher HSRP priority to become the active gateway under normal operating conditions, while the secondary multilayer switch operates as the standby gateway.

The configured HSRP virtual gateways include:

| VLAN | Virtual Gateway |
|---|---|
| 10 – IT | 192.168.10.1 |
| 20 – Finance | 192.168.20.1 |
| 30 – Procurement | 192.168.30.1 |
| 40 – HR | 192.168.40.1 |
| 50 – Marketing | 192.168.50.1 |
| 60 – Servers | 192.168.60.1 |
| 100 – Voice | 192.168.100.1 |

### Benefits of HSRP

- Provides default gateway redundancy.
- Reduces network downtime during gateway failures.
- Allows automatic failover to the standby multilayer switch.
- Improves network availability.

## 4. Spanning Tree Protocol (STP)

Spanning Tree Protocol is configured to prevent Layer 2 switching loops caused by redundant connections between switches.

The network uses redundant connections between multilayer switches and departmental access switches. STP manages these redundant paths by placing selected ports into a blocking state while maintaining alternative paths for recovery.

The implementation supports:

- Loop prevention in the switched network.
- Redundant Layer 2 connectivity.
- Automatic topology reconvergence when an active link fails.
- Improved network stability.

STP root bridge placement is configured to support the intended network topology.

## 5. Redundant Access Switch Connectivity

Departmental access switches have redundant uplinks to the primary and secondary multilayer switches.

This design reduces dependence on a single uplink or distribution switch.

If an uplink or multilayer switch becomes unavailable, an alternative path can be used to maintain network connectivity, subject to STP and gateway convergence.

## 6. Server Room Redundancy

The server environment incorporates two Layer 2 switches to provide redundant network connectivity.

Servers are connected to the redundant switching infrastructure to reduce the risk of losing server connectivity due to a single switch failure.

This design improves the availability of centralised network services, including:

- DNS services.
- DHCP services.
- Web services.
- File services.
- Backup services.

The redundant switching infrastructure is designed to support continued server connectivity during network component failures.

## 7. Dual ISP Connectivity

The proposed network infrastructure incorporates two Internet Service Providers:

- ISP 1
- ISP 2

Both providers connect to the edge routing infrastructure to provide alternative Internet connectivity paths.

The dual ISP design reduces dependence on a single Internet provider and supports improved Internet availability.

The edge routers provide connectivity between the internal enterprise network and the external ISP networks.

Actual Internet failover depends on the configured routing protocols, route selection and successful operation of the alternative ISP path.

## 8. Redundancy and High Availability Benefits

The redundancy mechanisms provide several advantages:

- Improved network availability.
- Reduced single points of failure.
- Gateway failover through HSRP.
- Loop prevention through STP.
- Alternative paths through redundant network links.
- Improved server network connectivity.
- Alternative Internet connectivity through dual ISP connections.
- Improved network resilience and reliability.

## 9. Testing and Verification

The following tests can be performed in Cisco Packet Tracer to verify the redundancy implementation:

| Test | Expected Result |
|---|---|
| Shut down the active HSRP multilayer switch | Standby switch takes over the virtual gateway role |
| Disconnect an active redundant uplink | Network reconverges using an available alternative path |
| Verify STP status | Redundant Layer 2 paths are managed without switching loops |
| Disconnect one ISP connection | Alternative Internet path remains available if routing failover is configured |
| Disconnect one server-room switch | Server connectivity is maintained through an alternative connection where supported |

Useful Cisco IOS verification commands include:

```cisco
show standby brief
show spanning-tree
show interfaces trunk
show ip route
show ip interface brief
```

## 10. Conclusion

The JCPZ network infrastructure design incorporates multiple redundancy mechanisms to improve availability and reduce the impact of network component failures.

By combining HSRP, STP, redundant switching, alternative network links and dual ISP connectivity, the proposed infrastructure provides a more resilient enterprise network architecture.

This project is designed and simulated in Cisco Packet Tracer for educational and demonstration purposes. Actual failover performance should be verified through controlled testing.
