Enterprise Network with DHCP & RIP | Cisco Packet Tracer


📌 Overview

This project demonstrates the design and implementation of a scalable enterprise network using Cisco Packet Tracer. The topology consists of 4 routers, 4 switches, and 12 PCs, with each router providing DHCP services for its local network and RIP v2 enabling dynamic routing between all LANs.

The lab simulates a small enterprise environment where hosts automatically receive IP addresses, communicate across multiple subnets, and exchange routing information dynamically.

🏗️ Network Topology
4 Cisco 2911 Routers
4 Cisco 2960 Switches
12 End Devices (PCs)
4 LAN Segments
3 WAN Point-to-Point Links

⚙️ Technologies Used
Cisco Packet Tracer
DHCP (Dynamic Host Configuration Protocol)
RIP Version 2 (Dynamic Routing)
IPv4 Addressing
Router-to-Router WAN Links
LAN Switching
End-to-End Connectivity Testing

🚀 Features
Automatic IP address assignment using DHCP.
Dynamic route learning using RIP Version 2.
Multiple LANs interconnected through WAN links.
Communication between all hosts across different networks.
Simplified IP management with centralized DHCP on each router.
Routing tables updated automatically without static routes.

🌐 IP Addressing Scheme
Network 	Subnet	    Gateway
LAN 1	 192.168.1.0/24	192.168.1.1
LAN 2	 192.168.2.0/24	192.168.2.1
LAN 3	 192.168.3.0/24	192.168.3.1
LAN 4	 192.168.4.0/24	192.168.4.1
R1-R2	 10.0.12.0/30	  Point-to-Point
R2-R3	 10.0.23.0/30	  Point-to-Point
R3-R4	 10.0.34.0/30	  Point-to-Point

#Router 1 (Leftmost)
enable
conf t

hostname R1

interface g0/0
ip address 10.0.12.1 255.255.255.252
no shutdown

interface g0/1
ip address 192.168.1.1 255.255.255.0
no shutdown

ip dhcp excluded-address 192.168.1.1 192.168.1.10

ip dhcp pool LAN1
network 192.168.1.0 255.255.255.0
default-router 192.168.1.1
dns-server 8.8.8.8

router rip
version 2
no auto-summary
network 10.0.0.0
network 192.168.1.0
end
wr


#Router 2
enable
conf t

hostname R2

interface g0/0
ip address 10.0.12.2 255.255.255.252
no shutdown

interface g0/1
ip address 10.0.23.1 255.255.255.252
no shutdown

interface g0/2
ip address 192.168.2.1 255.255.255.0
no shutdown

ip dhcp excluded-address 192.168.2.1 192.168.2.10

ip dhcp pool LAN2
network 192.168.2.0 255.255.255.0
default-router 192.168.2.1
dns-server 8.8.8.8

router rip
version 2
no auto-summary
network 10.0.0.0
network 192.168.2.0
end
wr


#Router 3
enable
conf t

hostname R3

interface g0/0
ip address 10.0.23.2 255.255.255.252
no shutdown

interface g0/1
ip address 10.0.34.1 255.255.255.252
no shutdown

interface g0/2
ip address 192.168.3.1 255.255.255.0
no shutdown

ip dhcp excluded-address 192.168.3.1 192.168.3.10

ip dhcp pool LAN3
network 192.168.3.0 255.255.255.0
default-router 192.168.3.1
dns-server 8.8.8.8

router rip
version 2
no auto-summary
network 10.0.0.0
network 192.168.3.0
end
wr

#Router 4 (Rightmost)
enable
conf t

hostname R4

interface g0/0
ip address 10.0.34.2 255.255.255.252
no shutdown

interface g0/1
ip address 192.168.4.1 255.255.255.0
no shutdown

ip dhcp excluded-address 192.168.4.1 192.168.4.10

ip dhcp pool LAN4
network 192.168.4.0 255.255.255.0
default-router 192.168.4.1
dns-server 8.8.8.8

router rip
version 2
no auto-summary
network 10.0.0.0
network 192.168.4.0
end
wr

🎯 Learning Outcomes

Through this project, I gained hands-on experience with:

Enterprise network design
Dynamic IP address allocation using DHCP
Dynamic routing using RIP Version 2
IPv4 subnetting and addressing
Router and switch configuration
Cisco IOS troubleshooting commands
End-to-end network connectivity testing
