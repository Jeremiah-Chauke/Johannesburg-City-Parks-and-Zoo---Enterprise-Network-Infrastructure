# JCPZ Network – IP Telephony Configuration

## 1. Overview

The Johannesburg City Parks and Zoo (JCPZ) enterprise network incorporates an IP telephony solution to support voice communication between users across the organisation.

The IP telephony infrastructure uses Cisco IP Phones connected to the network through access switches. A dedicated Voice VLAN separates voice traffic from normal departmental data traffic.

Cisco Call Manager Express (CME) is configured on an edge router to provide call processing and telephone extension management.

The implementation was designed and simulated using Cisco Packet Tracer.

## 2. Voice VLAN Configuration

A dedicated Voice VLAN (VLAN 100) is configured for IP telephony devices.

| Parameter | Configuration |
|---|---|
| VLAN ID | 100 |
| VLAN Name | VOICE |
| Network Address | 192.168.100.0/24 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 192.168.100.1 |
| DHCP Server | 192.168.60.3 |

The Voice VLAN provides logical separation between voice communication traffic and departmental data traffic.

## 3. IP Address Assignment

The Dynamic Host Configuration Protocol (DHCP) server automatically assigns IP addresses to IP Phones.

The DHCP pool for VLAN 100 provides the following information:

- IP address from the Voice VLAN subnet.
- Subnet mask.
- Default gateway.
- TFTP server address through DHCP Option 150.

The multilayer switches use DHCP relay configuration to forward DHCP requests from the Voice VLAN to the centralised DHCP server in VLAN 60.

Example configuration:

```cisco
interface Vlan100
 ip helper-address 192.168.60.3
```

## 4. DHCP Option 150 – TFTP Server

DHCP Option 150 provides IP Phones with the address of the TFTP server used to retrieve their configuration information.

In this implementation, Option 150 points to the CME router's TFTP address:

```text
192.168.102.82
```

This allows the IP Phones to obtain the necessary configuration information from the router hosting CME.

The TFTP address must be reachable from the Voice VLAN.

## 5. Cisco Call Manager Express (CME)

Cisco Call Manager Express is configured on Router1 to provide call processing services for the IP Phones.

CME manages telephone extensions and allows registered IP Phones to communicate with one another.

The router acts as the call-processing and TFTP service provider for the simulated IP telephony environment.

### CME Configuration

The router is configured with telephony services to manage the IP Phones.

Example configuration:

```cisco
telephony-service
 max-ephones 10
 max-dn 10
 ip source-address 192.168.102.82 port 2000
 auto assign 1 to 10
 create cnf-files
```

**Note:** The maximum number of phones and directory numbers should match the final router configuration.

## 6. Ephone-DN Configuration

The `ephone-dn` command creates directory numbers (telephone extensions) that can be assigned to IP Phones.

Each directory number represents a telephone extension that users can dial to contact another IP Phone.

Example:

```cisco
ephone-dn 1
 number 1001
```

This configuration creates telephone extension 1001.

Additional directory numbers can be configured for other IP Phones.

## 7. Ephone Configuration

The `ephone` command defines individual IP Phone devices within the CME configuration.

Each phone is identified using its MAC address and assigned a directory number.

Example:

```cisco
ephone 1
 mac-address XXXX.XXXX.XXXX
 type 7960
 button 1:1
```

The MAC address must be replaced with the actual MAC address of the IP Phone.

The `button 1:1` command associates the phone's first line button with directory number 1.

## 8. IP Phone Registration and Communication

After receiving their IP configuration through DHCP, the IP Phones use the TFTP server address supplied through Option 150 to retrieve their configuration files.

The phones then register with the CME service running on Router1.

Once registered and assigned telephone extensions, users can place calls between IP Phones.

The implementation supports communication between configured extensions within the simulated network.

## 9. Voice Network Security and Management

The dedicated Voice VLAN provides separation between voice and departmental data traffic.

Additional security measures that can be considered include:

- Restricting access to voice network resources.
- Applying ACLs to control communication between VLANs.
- Securing router administrative access.
- Monitoring voice network connectivity.
- Protecting network devices against unauthorised access.

## 10. Testing and Verification

The following tests can be performed to verify the IP telephony implementation:

| Test | Expected Result |
|---|---|
| Check Voice VLAN configuration | VLAN 100 exists and is active |
| Check DHCP allocation | IP Phones receive addresses from 192.168.100.0/24 |
| Verify DHCP Option 150 | Phones receive the CME/TFTP router address |
| Verify CME configuration | Telephony service is active |
| Verify phone registration | IP Phones register with CME |
| Test telephone extensions | IP Phones can call one another |

Useful Cisco IOS verification commands include:

```cisco
show running-config
show ephone
show ephone-dn
show telephony-service
show ip interface brief
```

## 11. Conclusion

The IP telephony implementation provides voice communication capabilities within the proposed JCPZ enterprise network.

By using a dedicated Voice VLAN, DHCP address allocation, DHCP Option 150 and Cisco Call Manager Express, the network supports centralised management of IP Phones and communication between configured telephone extensions.

The solution was designed and simulated in Cisco Packet Tracer for educational and demonstration purposes.
