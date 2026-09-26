# Networking

A personal reference covering fundamental networking concepts, protocols, infrastructure, security, troubleshooting, and commonly used commands.

---

# 1. Network Fundamentals

## What Is a Network?

A computer network is a collection of connected devices that communicate and exchange data using defined protocols.

## Common Network Types

- **PAN** — Personal Area Network
- **LAN** — Local Area Network
- **WLAN** — Wireless Local Area Network
- **MAN** — Metropolitan Area Network
- **WAN** — Wide Area Network

## Common Network Devices

### Router
Connects different networks and makes Layer 3 forwarding decisions.

### Switch
Connects devices within a network and forwards Ethernet frames using MAC addresses.

### Access Point
Provides wireless devices with access to a network.

### Firewall
Controls network traffic according to security rules.

### Modem
Provides communication between a local network and an ISP's network.

## OSI Model

| Layer | Name | Examples |
|---|---|---|
| 7 | Application | HTTP, DNS, SSH |
| 6 | Presentation | Encryption, encoding |
| 5 | Session | Session management |
| 4 | Transport | TCP, UDP |
| 3 | Network | IP, routing |
| 2 | Data Link | Ethernet, MAC |
| 1 | Physical | Cables, radio, signals |

## TCP/IP Model

| Layer | Examples |
|---|---|
| Application | HTTP, DNS, SSH, DHCP |
| Transport | TCP, UDP |
| Internet | IP, ICMP |
| Network Access | Ethernet, Wi-Fi |

## Encapsulation

When data moves down the networking stack, each layer adds information required for communication.

```text
Application Data
      ↓
TCP/UDP Segment
      ↓
IP Packet
      ↓
Ethernet Frame
      ↓
Bits

At the destination, the process is reversed through decapsulation.

Important Networking Terms
Bandwidth — Maximum theoretical data capacity.
Throughput — Actual amount of data successfully transferred.
Latency — Delay between sending and receiving data.
Protocol — Rules used for communication.
Frame — Layer 2 data unit.
Packet — Layer 3 data unit.
Segment — Common term for a TCP Layer 4 data unit.
Port — Logical endpoint used by applications.
MAC address — Layer 2 hardware address.
IP address — Layer 3 logical address.
Traffic Types
Unicast

One sender → one receiver.

Broadcast

One sender → all devices within the broadcast domain.

Multicast

One sender → a specific group of receivers.

2. IP Addressing
IPv4

IPv4 uses 32-bit addresses written as four decimal octets.

Example:

192.168.1.10

Each octet ranges from:

0 - 255
Network and Host Portions

An IPv4 address consists of:

Network portion + Host portion

The subnet mask determines which bits belong to each portion.

Private IPv4 Ranges
10.0.0.0/8

172.16.0.0/12

192.168.0.0/16

Private addresses are commonly used inside local networks.

Special IPv4 Addresses
Loopback
127.0.0.0/8

Commonly:

127.0.0.1

Used to refer to the local machine.

APIPA
169.254.0.0/16

A host may automatically assign an address from this range when DHCP fails.

Public vs Private IP
Private IP — Used internally.
Public IP — Routable across the public Internet.
Static vs Dynamic Addressing
Static

Manually configured.

Dynamic

Automatically assigned, commonly through DHCP.

Default Gateway

The default gateway is the device a host uses to reach destinations outside its local network.

Example:

Host:       192.168.1.20
Gateway:    192.168.1.1
IPv6

IPv6 uses 128-bit addresses.

Example:

2001:db8:abcd:0012::1

Important IPv6 address types include:

Global Unicast
Link-Local
Multicast
Loopback

IPv6 loopback:

::1

IPv6 link-local addresses commonly begin with:

fe80::
3. Subnetting
What Is Subnetting?

Subnetting divides a larger IP network into smaller networks.

Benefits include:

Efficient address usage
Network organization
Smaller broadcast domains
Segmentation
Better address management
CIDR

CIDR represents the number of network bits.

Example:

192.168.1.0/24

/24 means the first 24 bits are network bits.

Common Prefixes
CIDR	Subnet Mask	Usable Hosts
/24	255.255.255.0	254
/25	255.255.255.128	126
/26	255.255.255.192	62
/27	255.255.255.224	30
/28	255.255.255.240	14
/29	255.255.255.248	6
/30	255.255.255.252	2
Important Addresses

Every subnet normally has:

Network address
Usable host addresses
Broadcast address

Example:

192.168.10.0/26

Network:    192.168.10.0
First host: 192.168.10.1
Last host:  192.168.10.62
Broadcast:  192.168.10.63
VLSM

Variable Length Subnet Masking allows different subnet sizes to be used within the same network.

FLSM

Fixed Length Subnet Masking uses the same subnet size for all subnets.

4. Switching
What Is Switching?

Switching is the process of forwarding Ethernet frames between devices within a network.

MAC Addresses

A MAC address is a Layer 2 address associated with a network interface.

Example:

00:1A:2B:3C:4D:5E
MAC Address Table

A switch learns which MAC addresses are reachable through which ports.

Basic process:

Receive frame
     ↓
Learn source MAC
     ↓
Check destination MAC
     ↓
Forward or flood
Forwarding

If the destination MAC is known, the switch forwards the frame through the appropriate port.

Flooding

If the destination MAC is unknown, the switch may flood the frame out other ports within the same VLAN.

Broadcast frames are also flooded within their broadcast domain.

Collision Domain

Each switch port normally represents a separate collision domain.

Broadcast Domain

A broadcast domain is the set of devices that receive a Layer 2 broadcast.

VLANs can be used to separate broadcast domains.

5. VLANs
What Is a VLAN?

A VLAN is a logical network segment created on a switch.

VLANs allow one physical switching infrastructure to contain multiple logical networks.

Benefits
Segmentation
Smaller broadcast domains
Better organization
Improved security
Separation of different groups
Access Port

An access port normally carries traffic belonging to one VLAN.

Trunk Port

A trunk can carry traffic for multiple VLANs.

802.1Q

IEEE 802.1Q is commonly used for VLAN tagging on trunk links.

Native VLAN

The native VLAN is the VLAN associated with untagged traffic on an 802.1Q trunk.

Inter-VLAN Routing

Devices in different VLANs require Layer 3 routing to communicate.

Common methods include:

Router-on-a-stick
Layer 3 switching
6. Routing
What Is Routing?

Routing determines how packets travel between different IP networks.

Routing Table

A router uses a routing table to determine where packets should be forwarded.

A route can contain information such as:

Destination network
Subnet mask/prefix
Next hop
Outgoing interface
Metric
Connected Routes

Routes automatically created for directly connected networks.

Static Routes

Routes manually configured by an administrator.

Default Route

Used when a more specific route does not exist.

IPv4 example:

0.0.0.0/0
Dynamic Routing

Dynamic routing protocols allow routers to exchange routing information.

Examples:

RIP
OSPF
EIGRP
BGP
Next Hop

The next-hop address identifies the router or device to which a packet should be forwarded.

Longest Prefix Match

When multiple routes match a destination, routers generally prefer the most specific matching route.

7. DHCP
What Is DHCP?

DHCP automatically provides network configuration information to clients.

It can provide:

IP address
Subnet mask
Default gateway
DNS server
Lease information
DORA

The basic DHCP process is:

Discover
   ↓
Offer
   ↓
Request
   ↓
Acknowledge
DHCP Lease

A DHCP address is normally assigned for a defined period.

DHCP Server

Provides configuration information to clients.

DHCP Client

Requests network configuration.

DHCP Relay

Allows DHCP requests to cross routers so that a DHCP server can serve clients on another network.

DHCP Security

Important defensive technologies include:

DHCP snooping
Trusted/untrusted ports
IP Source Guard
8. DNS
What Is DNS?

The Domain Name System translates human-readable domain names into information such as IP addresses.

Example:

example.com
     ↓
93.184.216.34
DNS Hierarchy
Root
 ↓
TLD
 ↓
Authoritative DNS
 ↓
Domain
DNS Resolver

A resolver performs DNS queries on behalf of clients.

Common DNS Records
Record	Purpose
A	IPv4 address
AAAA	IPv6 address
CNAME	Alias
MX	Mail server
NS	Name server
TXT	Text information
PTR	Reverse lookup
SOA	Zone authority information
Forward Lookup

Domain name → IP address.

Reverse Lookup

IP address → domain name.

DNS Caching

Resolvers and clients may cache DNS responses to reduce repeated queries.

Useful Commands
dig example.com
nslookup example.com
host example.com
DNS Security Concepts
DNSSEC
DNS spoofing
DNS cache poisoning
DNS tunneling
DNS enumeration
9. NAT
What Is NAT?

Network Address Translation changes IP address information as traffic passes through a network device.

NAT is commonly used to allow private networks to communicate with public networks.

Types of NAT
Static NAT

One private address maps to one public address.

Dynamic NAT

Private addresses are translated using a pool of public addresses.

PAT

Port Address Translation allows multiple private hosts to share a public IP by using different source ports.

PAT is commonly called NAT overload.

NAT Terminology
Inside local
Inside global
Outside local
Outside global
NAT Example
192.168.1.10
      ↓
   NAT/PAT
      ↓
203.x.x.x
      ↓
  Internet
NAT Limitations

NAT can complicate:

End-to-end connectivity
Some protocols
Troubleshooting
Inbound connections

NAT is not a replacement for a firewall.

10. ACLs
What Is an ACL?

An Access Control List is a set of rules used to permit or deny traffic.

ACLs can be used to control network access.

Standard ACL

Primarily filters based on source IPv4 address.

Extended ACL

Can filter based on information such as:

Source IP
Destination IP
Protocol
Port
ACL Processing

Rules are evaluated in order.

The first matching rule is generally applied.

Implicit Deny

ACL processing includes an implicit deny at the end if traffic does not match a permitted rule.

Inbound vs Outbound
Inbound

Traffic is evaluated as it enters an interface.

Outbound

Traffic is evaluated as it leaves an interface.

Wildcard Masks

Cisco ACLs commonly use wildcard masks.

Example:

0.0.0.255

This can represent a /24 network when used appropriately in an ACL.

Security Relevance

ACLs can help:

Restrict network access
Limit services
Segment traffic
Reduce attack surface
11. Wireless Networking
WLAN

A Wireless Local Area Network allows devices to communicate using radio instead of physical Ethernet connections.

Access Point

An access point provides wireless connectivity to clients.

SSID

The Service Set Identifier is the network name users see when selecting a Wi-Fi network.

BSSID

Identifies a specific wireless access point/radio interface.

Frequency Bands

Common Wi-Fi bands include:

2.4 GHz
5 GHz
6 GHz
Channels

Wireless devices communicate over radio channels.

Channel overlap and interference can reduce performance.

Wireless Security

Common technologies include:

WPA2
WPA3
WPA2/WPA3 Enterprise
PSK
802.1X
Wireless Security Threats
Rogue access points
Evil twin attacks
Weak passwords
Deauthentication attacks
Unauthorized clients
12. Network Security
CIA Triad
Confidentiality

Prevent unauthorized access to information.

Integrity

Prevent unauthorized modification.

Availability

Keep systems and services accessible.

Authentication

Verifies who a user or device is.

Authorization

Determines what an authenticated entity is allowed to access.

Common Security Controls
Firewall
IDS
IPS
VPN
ACL
Network segmentation
NAC
Authentication systems
Logging and monitoring
Common Network Attacks
ARP spoofing
DNS spoofing
DHCP attacks
MAC flooding
VLAN hopping
Man-in-the-middle attacks
Denial-of-service attacks
Rogue access points
Evil twin attacks
Defensive Technologies
DHCP snooping
Dynamic ARP Inspection
Port security
IP Source Guard
802.1X
Network segmentation
Strong authentication
Monitoring and logging
13. Troubleshooting
General Methodology

Troubleshoot systematically rather than randomly changing configurations.

A useful approach:

Identify the problem
       ↓
Gather information
       ↓
Check physical connectivity
       ↓
Check Layer 2
       ↓
Check Layer 3
       ↓
Check services
       ↓
Test the solution
       ↓
Document the result
Physical Layer

Check:

Power
Cables
Interfaces
Wireless signal
Link status
Layer 2

Check:

VLAN
MAC address table
Trunk
Access port
STP
Interface errors
Layer 3

Check:

IP address
Subnet mask
Default gateway
Routing table
Routes
ACLs
Services

Check:

DHCP
DNS
NAT
Application services
Common Symptoms
169.254.x.x Address

May indicate that DHCP configuration failed.

Can Reach IP but Not Domain

Possible DNS problem.

Can Reach Local Network but Not Remote Network

Possible gateway or routing problem.

Devices in Same VLAN Cannot Communicate

Check:

VLAN assignment
Interface status
IP configuration
Switch configuration
ACLs
Useful Troubleshooting Commands

Linux:

ip addr
ip route
ping
traceroute
ss
arp
dig
nslookup

Cisco:

show ip interface brief
show running-config
show interfaces
show vlan brief
show mac address-table
show arp
show ip route
14. CLI Commands
Cisco IOS
Enter Privileged EXEC Mode
enable
Enter Global Configuration Mode
configure terminal
Display Running Configuration
show running-config
Display Interfaces
show interfaces
Display Interface Summary
show ip interface brief
Display Routing Table
show ip route
Display VLANs
show vlan brief
Display MAC Address Table
show mac address-table
Display ARP Table
show arp
Test Connectivity
ping <ip-address>
Trace a Path
traceroute <ip-address>
Basic Interface Configuration
configure terminal
interface <interface>
ip address <ip-address> <subnet-mask>
no shutdown
Linux Networking Commands
Show IP Addresses
ip addr
Show Routing Table
ip route
Test Connectivity
ping <ip-address>
Trace a Route
traceroute <ip-address>
Show Listening/Network Sockets
ss
DNS Lookup
dig <domain>
DNS Query
nslookup <domain>
Show ARP/Neighbor Information
ip neigh
Quick Reference
OSI
7  Application
6  Presentation
5  Session
4  Transport
3  Network
2  Data Link
1  Physical
TCP/IP
Application
Transport
Internet
Network Access
Common Protocols
Protocol	Purpose
HTTP	Web traffic
HTTPS	Encrypted web traffic
SSH	Secure remote administration
DNS	Name resolution
DHCP	Automatic network configuration
FTP	File transfer
SMTP	Email transmission
ICMP	Network diagnostic/control messages
ARP	IPv4 address-to-MAC resolution
TCP	Reliable transport
UDP	Connectionless transport
Networking Mental Model

When troubleshooting or analyzing network traffic, think through the communication path:

Application
    ↓
Port / Transport
    ↓
IP Address
    ↓
MAC Address
    ↓
Switch
    ↓
Router
    ↓
Destination Network

The goal is not just to memorize commands or protocols.

Understand:

What is communicating?

How is it addressed?

How does the device know where to send it?

What protocol is being used?
