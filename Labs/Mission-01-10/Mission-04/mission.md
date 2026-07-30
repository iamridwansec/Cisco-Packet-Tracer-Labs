# Mission 04

# Mission 04 – VLAN Trunking (802.1Q)

---

# Objective

Learn how to connect two switches using an IEEE 802.1Q trunk so that multiple VLANs can communicate across the trunk while maintaining VLAN separation.

This lab introduces trunk ports, VLAN propagation, and enterprise switch-to-switch communication.

---

# Learning Outcomes

After completing this mission, I should be able to:

- Explain the purpose of a trunk link
- Differentiate between access and trunk ports
- Configure an 802.1Q trunk
- Verify trunk status
- Extend VLANs across multiple switches
- Troubleshoot trunk-related issues

---

# Theory Review

An access port belongs to a single VLAN and connects end devices such as PCs, printers, and servers.

A trunk port carries traffic for multiple VLANs over one physical cable by adding an IEEE 802.1Q VLAN tag to Ethernet frames.

Without a trunk, VLANs cannot extend between switches.

Trunking reduces cabling, improves scalability, and is widely used in enterprise networks.

---

# Devices Required

- 2 × Cisco 2960 Switches
- 6 × PCs

---

# VLAN Plan

| VLAN | Name | Devices |
|------|------|---------|
| 10 | HR | PC1, PC2 |
| 20 | IT | PC3, PC4 |
| 30 | SALES | PC5, PC6 |

---

# IP Addressing

## VLAN 10

| Device | IP Address |
|---------|------------|
| PC1 | 192.168.10.10 |
| PC2 | 192.168.10.20 |

---

## VLAN 20

| Device | IP Address |
|---------|------------|
| PC3 | 192.168.20.10 |
| PC4 | 192.168.20.20 |

---

## VLAN 30

| Device | IP Address |
|---------|------------|
| PC5 | 192.168.30.10 |
| PC6 | 192.168.30.20 |

Subnet Mask

255.255.255.0

Default Gateway

192.168.X.1

---

# Topology

Switch1

Fa0/1 → PC1

Fa0/2 → PC3

Fa0/3 → PC5

Fa0/24 → Switch2 Fa0/24

Switch2

Fa0/1 → PC2

Fa0/2 → PC4

Fa0/3 → PC6

The connection between Fa0/24 on both switches must operate as a trunk.

Use Copper Straight-Through cables.

---

# Configuration Tasks

Configure on both switches:

1. Create VLAN 10
2. Create VLAN 20
3. Create VLAN 30
4. Assign access ports
5. Configure Fa0/24 as a trunk
6. Save the configuration

---

# Verification

Run:

show vlan brief

show interfaces trunk

show running-config

show interfaces switchport

Verify:

- VLANs exist
- Trunk is operational
- Correct ports belong to correct VLANs

---

# Connectivity Tests

Successful:

PC1 ↔ PC2

PC3 ↔ PC4

PC5 ↔ PC6

Failed:

PC1 ↔ PC3

PC2 ↔ PC5

PC4 ↔ PC6

Document every result.

---

# Simulation Mode

Observe:

- VLAN-tagged frames crossing the trunk
- ARP Requests
- ICMP Echo Requests
- ICMP Echo Replies

Notice that broadcasts remain inside their VLAN.

---

# Troubleshooting Challenge

Scenario 1

Configure one end of the trunk as an access port.

Observe communication failure.

Restore trunk mode.

---

Scenario 2

Allow only VLAN 10 on the trunk.

Test communication for VLAN 20 and VLAN 30.

Restore all VLANs.

---

Scenario 3

Place PC4 in VLAN 10.

Observe the change.

Return PC4 to VLAN 20.

---

# Questions

1. What is trunking?
2. Why is trunking necessary?
3. What is IEEE 802.1Q?
4. What is the difference between an access port and a trunk port?
5. Which command verifies trunk status?
6. Why can VLAN 10 communicate across two switches?
7. What happens if the trunk fails?
8. Why are VLAN tags removed before frames reach a PC?

---

# Key Takeaways

- Trunks carry multiple VLANs.
- IEEE 802.1Q tags Ethernet frames.
- Access ports belong to one VLAN.
- Trunk ports carry many VLANs.
- Enterprise networks depend heavily on trunk links.

---

# Lab Summary

This lab introduced VLAN trunking using IEEE 802.1Q. Two switches were connected through a trunk link, allowing VLANs to extend across multiple switches while maintaining broadcast domain separation. Verification commands confirmed VLAN operation and trunk status, reinforcing the importance of trunking in scalable enterprise networks.
