# Lab XX – Lab Title

> **Example:** Lab 01 – Build Your First LAN

---

# Lab Information

| Field | Details |
|--------|----------|
| Lab Number | Lab XX |
| Difficulty | Beginner / Intermediate / Advanced |
| Estimated Time | 20–60 Minutes |
| Category | Switching / Routing / VLAN / Security |
| Software | Cisco Packet Tracer |
| Author | Your Name |
| Last Updated | YYYY-MM-DD |

---

# Objective

Explain what this lab is designed to teach.

Example:

After completing this lab, I should be able to build a small LAN, configure IPv4 addresses, verify communication between hosts, and troubleshoot basic connectivity issues.

---

# Skills Covered

- Device placement
- Cabling
- IP Addressing
- Switch configuration
- Router configuration
- VLAN
- Routing
- DHCP
- DNS
- NAT
- ACL
- Troubleshooting

---

# Prerequisites

Before attempting this lab, I should understand:

- Basic Networking
- OSI Model
- TCP/IP
- IPv4 Addressing
- Ethernet
- Packet Tracer Interface

---

# Theory Review

Briefly explain the networking concepts used in this lab.

Do not simply list commands.

Explain:

- Why
- How
- Where
- When

the technologies are used.

---

# Devices Required

| Device | Quantity |
|---------|---------:|
| PC | 2 |
| Switch | 1 |
| Router | 0 |
| Server | 0 |

---

# Network Topology

Insert topology screenshot.

Location:

```
Topologies/
```

or

```
Screenshots/Topology/
```

---

# IP Addressing Table

| Device | Interface | IP Address | Subnet Mask | Gateway |
|----------|-----------|------------|-------------|----------|
| PC1 | FastEthernet0 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC2 | FastEthernet0 | 192.168.1.20 | 255.255.255.0 | 192.168.1.1 |

---

# Step 1 – Build the Topology

Explain every action.

Do not skip steps.

Example:

1. Open Cisco Packet Tracer.
2. Drag one switch.
3. Drag two PCs.
4. Connect using Copper Straight Through.

Explain WHY each step is performed.

---

# Step 2 – Configure Devices

Explain every configuration.

Example:

Assign:

PC1

```
192.168.1.10
```

PC2

```
192.168.1.20
```

---

# Step 3 – Verification

Explain how to verify the configuration.

Commands may include:

```
ping

ipconfig

show ip interface brief

show mac address-table

show running-config
```

---

# Expected Output

Describe what success looks like.

Example:

```
Reply from 192.168.1.20

Packets: Sent = 4

Received = 4

Lost = 0
```

---

# Troubleshooting

Common mistakes.

Example:

Wrong cable

Wrong subnet mask

Wrong gateway

Incorrect VLAN

Disabled interface

Shutdown interface

Duplicate IP address

---

# Packet Analysis

Explain what happens to the packet.

Cover:

Layer 1

Layer 2

Layer 3

ARP

Switch forwarding

Routing

Encapsulation

Decapsulation

---

# Screenshot Checklist

Capture:

☐ Topology

☐ Configuration

☐ CLI

☐ Ping

☐ Simulation Mode

☐ Successful Test

Store them in

```
Screenshots/
```

---

# Challenge Exercise

Give yourself one harder challenge.

Example:

Add another PC.

Configure another subnet.

Add another switch.

Enable SSH.

Create VLANs.

---

# Real-World Application

Explain where this configuration would be used.

Example:

Office LAN

School

Bank

Hospital

ISP

Enterprise Network

---

# Key Takeaways

After completing this lab I can:

- Build the topology
- Configure devices
- Verify connectivity
- Troubleshoot problems
- Explain packet flow

---

# Related Documentation

Reference the theory documentation.

Example:

- network-fundamentals.md
- ip-addressing.md
- switching.md

---

# Files Produced

| File | Location |
|--------|----------|
| Packet Tracer File | Topologies/ |
| Screenshots | Screenshots/ |
| Documentation | Labs/ |
| Config Backup | Exports/Configs/ |

---

# Lab Summary


