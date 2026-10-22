CCNA Lab: VLANs, Trunking, Router-on-a-Stick, Security, and DHCP

Overview

This project demonstrates practical Cisco networking configuration using Cisco Packet Tracer. It covers VLAN creation, access and trunk port configuration, inter-VLAN routing using router-on-a-stick, basic Cisco device security, and DHCP configuration.

The aim of this lab is to understand how to segment a network, enable communication between VLANs, secure network devices, and automatically assign IP addresses to end devices.

Objectives

- Create and configure VLANs on a Cisco switch.
- Assign switch access ports to the appropriate VLANs.
- Configure trunk links to carry traffic for multiple VLANs.
- Configure router-on-a-stick for inter-VLAN routing.
- Configure Cisco enable passwords and enable secrets.
- Configure DHCP to automatically assign IP addresses to end devices.
- Verify configurations and troubleshoot connectivity.

Technologies and Tools

- Cisco Packet Tracer
- Cisco routers and switches
- VLANs (Virtual Local Area Networks)
- IEEE 802.1Q trunking
- Router-on-a-stick
- DHCP (Dynamic Host Configuration Protocol)
- Cisco IOS CLI

Lab Components

The lab uses Cisco networking devices, end devices, and interconnected router and switch interfaces to demonstrate VLAN segmentation, trunking, routing, security, and DHCP.

Topics Covered

1. VLAN Configuration

VLANs logically divide a switched network into separate broadcast domains.

Tasks include:

- Creating VLANs.
- Assigning VLAN IDs and names.
- Verifying VLAN membership.

Example commands:

enable
configure terminal
vlan 10
 name CM
vlan 20
 name HR
vlan 30
 name DC
end
show vlan brief

2. Access Port Configuration

Access ports connect end devices to a specific VLAN.

Example:

configure terminal
interface fastEthernet 0/1
 switchport mode access
 switchport access vlan 10
 no shutdown
end

3. Trunk Port Configuration

Trunk ports carry traffic for multiple VLANs between compatible network devices.

Example:

configure terminal
interface gigabitEthernet 0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20
 no shutdown
end

Note: The interface names and supported commands may differ depending on the device model and Packet Tracer version.

4. Router-on-a-Stick

Router-on-a-stick allows multiple VLANs to communicate through a single physical router interface using logical subinterfaces and IEEE 802.1Q encapsulation.

Example:

configure terminal
interface gigabitEthernet 0/1
 no shutdown
!
interface gigabitEthernet 0/1.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
!
interface gigabitEthernet 0/1.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
 interface gigabitEthernet 0/1.30
 encapsulation dot1Q 30
 ip address 192.168.30.1 255.255.255.0
end

The router subinterface IP addresses serve as the default gateways for their respective VLANs.

5. Cisco Device Security

The lab demonstrates the difference between configuring an enable password and an enable secret.

Enable password:

configure terminal
enable password kelvin

Enable secret:

enable secret wasili

The "enable secret" command is preferred because it stores the privileged EXEC password using a stronger password-hashing mechanism than the legacy "enable password" command.

For production devices, use strong unique secrets and additional security controls where supported.

6. DHCP Configuration

DHCP automatically assigns IP addresses and other network settings to clients.

Example:

configure terminal
ip dhcp excluded-address 192.168.1.1 192.168.1.10
ip dhcp excluded-address 192.168.2.1 192.168.2.10
ip dhcp excluded-address 192.168.3.1 192.168.3.10
!
ip dhcp pool CM
 network 192.168.10.0 255.255.255.0
 default-router 192.168.11.1
 dns-server 8.8.8.8
end

Repeat the DHCP pool configuration for other VLANs as required, using the correct subnet and gateway addresses.

7. Verification and Troubleshooting

Useful Cisco IOS commands include:

show vlan brief
show interfaces trunk
show interfaces switchport
show ip interface brief
show running-config
show ip dhcp pool
show ip dhcp binding
show ip route

Connectivity can also be tested by pinging the default gateway and devices in other VLANs.

Expected Results

After successful configuration and testing:

- End devices belong to their assigned VLANs.
- Trunk links carry the required VLAN traffic.
- The router routes traffic between VLANs.
- DHCP clients receive appropriate IP addresses and network settings.
- Privileged EXEC access is protected by the configured credentials.

Actual results should be confirmed through the lab's verification commands and connectivity tests.

Skills Demonstrated

- Cisco IOS configuration
- VLAN segmentation and switching
- Access and trunk port configuration
- Inter-VLAN routing
- DHCP configuration and verification
- Basic network device security
- Network troubleshooting

Project Files

The repository may include the following files:

- "ccna_lab_1.pkt" — Packet Tracer lab file.
- "README.md" — Project documentation.
- "router-config.txt" — Router configuration commands.
- "switch-config.txt" — Switch configuration commands.
- "screenshots/" — Topology and verification screenshots.

Conclusion

This lab provides practical experience with fundamental CCNA networking concepts, including switching, VLAN trunking, inter-VLAN routing, DHCP, and basic Cisco device security. It forms part of my ongoing networking practice and professional development.

Author: Kelvin Wasili

Focus: CCNA Networking Labs and Cisco IOS Configuration
