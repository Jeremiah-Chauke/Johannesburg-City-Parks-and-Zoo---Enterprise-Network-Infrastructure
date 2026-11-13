# Network Security

## 1. Introduction

Network security is an important part of the proposed Johannesburg City Parks and Zoo (JCPZ) enterprise network infrastructure. The network design incorporates security measures intended to protect organisational resources, prevent unauthorised access, and support the confidentiality, integrity, and availability of network services.

The security design focuses on network segmentation, controlled communication between VLANs, perimeter protection, secure network administration, and monitoring.

## 2. Network Segmentation

The network is divided into separate VLANs to isolate departments and server resources. This helps limit unnecessary communication between departments and reduces the impact of potential security incidents.

The following VLANs are used:

| VLAN | Department / Purpose |
|---|---|
| VLAN 10 | IT |
| VLAN 20 | Finance |
| VLAN 30 | Procurement |
| VLAN 40 | Human Resources |
| VLAN 50 | Marketing |
| VLAN 60 | Servers |
| VLAN 70 | WAN / ISP |
| VLAN 100 | Voice |

Inter-VLAN communication is handled by the multilayer switches. Access between VLANs can be controlled using Access Control Lists (ACLs).

## 3. Access Control Lists (ACLs)

ACLs are used to control network traffic according to defined rules. They can permit or deny traffic based on source and destination IP addresses and other supported criteria.

In the proposed design, ACLs can be used to:

- Restrict unauthorised access to departmental VLANs.
- Limit access to servers to authorised network segments.
- Control communication between different departments.
- Restrict access to network management interfaces.
- Allow only required traffic between the voice and data networks.

ACL rules should follow the principle of least privilege, allowing only the communication required for legitimate business operations.

## 4. Firewall Protection

Firewalls are included in the proposed network design to provide perimeter protection between the internal network and external networks.

Their intended functions include:

- Filtering incoming and outgoing network traffic.
- Blocking unauthorised connections.
- Controlling access to internal network resources.
- Reducing exposure to external network threats.
- Supporting controlled communication between network zones.

Firewall rules should be configured according to organisational security requirements.

## 5. Secure Network Administration

Network devices such as routers and switches require controlled administrative access.

Recommended security measures include:

- Using strong passwords for administrative accounts.
- Restricting remote management access to authorised administrators.
- Using SSH instead of Telnet where supported.
- Disabling unused switch ports.
- Assigning unused ports to an unused VLAN and shutting them down.
- Securing console and privileged EXEC access.
- Keeping network device configurations backed up.

These measures help reduce the risk of unauthorised access to network infrastructure.

## 6. Server Security

Servers are placed in VLAN 60 to separate them from departmental user networks.

The proposed server infrastructure includes DNS, DHCP, Web, File, and Backup services.

Recommended server security measures include:

- Restricting access to server services to authorised users and devices.
- Applying ACLs to control traffic reaching the server VLAN.
- Using strong administrative credentials.
- Keeping server configurations and data backed up.
- Disabling unnecessary services and open ports.
- Monitoring server availability and network communication.

## 7. Voice Network Security

IP phones are placed in a dedicated Voice VLAN (VLAN 100), separate from departmental data traffic.

This separation helps isolate voice communication from normal user data traffic. Access between the Voice VLAN and other network segments should be restricted to the services required for IP telephony.

The DHCP configuration provides the voice network with the required addressing information, while DHCP Option 150 identifies the router hosting the Call Manager Express (CME) and TFTP services.

## 8. Network Monitoring and Maintenance

Network monitoring and regular maintenance help identify potential security problems and maintain network availability.

Recommended activities include:

- Monitoring network device status and connectivity.
- Reviewing device logs for unusual activity.
- Checking interface and routing status.
- Reviewing ACL and firewall rules periodically.
- Backing up network device configurations.
- Updating device configurations when security requirements change.
- Investigating unexpected network traffic or connectivity issues.

## 9. Conclusion

The proposed JCPZ network infrastructure incorporates security principles such as VLAN segmentation, controlled inter-VLAN communication, firewall protection, secure network administration, and server isolation.

These measures provide a foundation for protecting network resources and reducing unauthorised access. Additional security controls, including detailed firewall policies, ACL rules, and continuous monitoring, should be implemented and tested according to the organisation's operational requirements.
