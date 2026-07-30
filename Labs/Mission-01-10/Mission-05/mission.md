# Mission 05

# Mission 05 – Inter-VLAN Routing (Router-on-a-Stick)

---

# Objective

Implement Inter-VLAN Routing using the Router-on-a-Stick (ROAS) method. Configure a router with multiple subinterfaces to allow communication between different VLANs over a single trunk link.

---

# Learning Outcomes

After completing this mission, I should be able to:

- Explain why different VLANs cannot communicate by default
- Configure Router-on-a-Stick
- Configure router subinterfaces
- Configure 802.1Q encapsulation
- Configure default gateways for VLANs
- Verify successful Inter-VLAN communication
- Troubleshoot Layer 2 and Layer 3 issues

---

# Theory Review

A Layer 2 switch forwards frames only within the same VLAN.

Different VLANs are different broadcast domains.

To allow communication between VLANs, a Layer 3 device must route packets between them.

Router-on-a-Stick (ROAS) is a design where one physical router interface is divided into multiple logical subinterfaces.

Each subinterface belongs to one VLAN and acts as that VLAN's default gateway.

Traffic between the switch and router travels across a single trunk link using IEEE 802.1Q VLAN tagging.

---

# Devices Required

- 1 × Cisco 2911 Router
- 1 × Cisco 2960 Switch
- 6 × PCs

---

# VLAN Plan

| VLAN | Name | Network | Gateway |
|------|------|---------|----------|
| 10 | HR | 192.168.10.0/24 | 192.168.10.1 |
| 20 | IT | 192.168.20.0/24 | 192.168.20.1 |
| 30 | SALES | 192.168.30.0/24 | 192.168.30.1 |

---

# IP Addressing

| Device | VLAN | IP Address |
|---------|------|------------|
| PC1 | 10 | 192.168.10.10 |
| PC2 | 10 | 192.168.10.20 |
| PC3 | 20 | 192.168.20.10 |
| PC4 | 20 | 192.168.20.20 |
| PC5 | 30 | 192.168.30.10 |
| PC6 | 30 | 192.168.30.20 |

Subnet Mask

255.255.255.0

Default Gateway

Use the gateway assigned to each VLAN.

---

# Topology

PC1 ----\
PC2 -----\
          \
        Cisco 2960
             |
          Fa0/24
             |
             |
          G0/0
      Cisco 2911

PC3
PC4
PC5
PC6 connected to the switch.

The link between the switch and router must operate as a trunk.

---

# Configuration Tasks

On the Switch

1. Create VLAN 10
2. Create VLAN 20
3. Create VLAN 30
4. Assign access ports
5. Configure Fa0/24 as a trunk

On the Router

1. Enable interface G0/0
2. Create subinterface G0/0.10
3. Configure encapsulation dot1Q 10
4. Assign gateway IP

Repeat for VLAN 20 and VLAN 30.

Configure every PC with the correct default gateway.

Save configurations.

---

# Verification

Run on the Router

show ip interface brief

show running-config

show ip route

Run on the Switch

show vlan brief

show interfaces trunk

---

# Connectivity Tests

Successful

PC1 ↔ PC2

PC1 ↔ PC3

PC2 ↔ PC6

PC4 ↔ PC5

PC6 ↔ PC3

Every VLAN should now communicate successfully.

---

# Simulation Mode

Observe

- ARP Request
- ARP Reply
- ICMP Request
- ICMP Reply
- Router forwarding packets between VLANs
- 802.1Q tagged frames on the trunk

---

# Troubleshooting Challenge

Scenario 1

Remove encapsulation dot1Q from one subinterface.

Observe the failure.

Restore the configuration.

---

Scenario 2

Configure the wrong default gateway on PC5.

Attempt communication.

Correct the gateway.

---

Scenario 3

Configure the switch port connected to the router as an access port.

Observe communication failure.

Restore trunk mode.

---

# Questions

1. Why can't VLANs communicate without a router?
2. What is Router-on-a-Stick?
3. What is a router subinterface?
4. Why is encapsulation dot1Q required?
5. Why is the switch-to-router link configured as a trunk?
6. What is the purpose of the default gateway?
7. Which command verifies router interfaces?
8. Which command verifies trunk status?
9. Which device performs Layer 3 forwarding?
10. Why is one physical interface enough for multiple VLANs?

---

# Key Takeaways

- VLANs require Layer 3 routing to communicate.
- Router-on-a-Stick uses one physical interface with multiple logical subinterfaces.
- Each VLAN requires its own gateway.
- Trunk links carry VLAN traffic to the router.
- Inter-VLAN Routing is a fundamental enterprise networking concept.

---

# Lab Summary

This lab implemented Inter-VLAN Routing using Router-on-a-Stick. Multiple VLANs shared a single trunk connection to a router, where subinterfaces performed routing between networks. Successful testing confirmed end-to-end communication across all VLANs and demonstrated how Layer 2 switching and Layer 3 routing work together in enterprise networks.

What is Dot1Q?

802.1Q (Dot1Q) is a standard that adds a VLAN tag to Ethernet frames.

