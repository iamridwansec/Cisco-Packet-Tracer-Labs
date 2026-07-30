# Mission 03

# Mission 03 – VLAN Fundamentals

---

# Objective

Learn how Virtual Local Area Networks (VLANs) logically separate devices on the same physical switch into different broadcast domains.

After completing this mission, I should understand how VLANs improve security, organization, and network performance.

---

# Learning Outcomes

After completing this mission, I should be able to:

- Explain what a VLAN is
- Create VLANs on a Cisco switch
- Assign switch ports to VLANs
- Verify VLAN membership
- Explain why devices in different VLANs cannot communicate without a router

---

# Theory Review

A Virtual Local Area Network (VLAN) is a logical segmentation of a switch. Instead of every device belonging to one broadcast domain, VLANs divide the switch into multiple isolated networks.

Devices in the same VLAN can communicate directly.

Devices in different VLANs require a Layer 3 device (router or Layer 3 switch) to communicate.

Each VLAN has its own broadcast domain.

---

# Devices Required

- 1 × Cisco 2960 Switch
- 6 × PCs

---

# VLAN Plan

| Department | VLAN ID | Ports |
|------------|---------|--------|
| HR | 10 | Fa0/1–Fa0/2 |
| IT | 20 | Fa0/3–Fa0/4 |
| Sales | 30 | Fa0/5–Fa0/6 |

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

Subnet Mask:

255.255.255.0

Default Gateway:

192.168.X.1

(X represents the VLAN number.)

---

# Topology

One Cisco 2960 switch connected to six PCs.

Connect:

PC1 → Fa0/1

PC2 → Fa0/2

PC3 → Fa0/3

PC4 → Fa0/4

PC5 → Fa0/5

PC6 → Fa0/6

Use Copper Straight-Through cables.

---

# Configuration Tasks

1. Create VLAN 10 named HR
2. Create VLAN 20 named IT
3. Create VLAN 30 named SALES
4. Assign switch ports
5. Configure PC IP addresses
6. Save configuration

---

# Verification

Run the following commands:

show vlan brief

show running-config

show interfaces switchport

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

Record all results.

---

# Simulation Mode

Observe:

- ARP Requests
- ARP Replies
- Broadcast traffic inside a VLAN
- No communication between VLANs

---

# Troubleshooting Challenge

Perform each scenario individually.

Scenario 1

Assign Fa0/2 to VLAN 20 instead of VLAN 10.

Observe communication failure.

Correct the configuration.

---

Scenario 2

Assign PC3 an incorrect IP address.

Attempt communication.

Restore the correct IP.

---

Scenario 3

Delete VLAN 30.

Observe what happens to PC5 and PC6.

Recreate VLAN 30.

---

# Questions

1. What is a VLAN?
2. Why are VLANs used?
3. What is a broadcast domain?
4. Why can't VLAN 10 communicate with VLAN 20?
5. Which command displays VLAN information?
6. What happens when a switch port is assigned to the wrong VLAN?
7. How does VLAN segmentation improve network security?

---

# Key Takeaways

- VLANs logically separate devices.
- Each VLAN is an independent broadcast domain.
- Switches isolate traffic between VLANs.
- Inter-VLAN communication requires Layer 3 routing.

---

# Lab Summary

This lab demonstrated how VLANs logically divide a Layer 2 switch into multiple isolated networks. Devices within the same VLAN communicated successfully, while communication between different VLANs failed because no Layer 3 routing was configured. VLANs improve organization, security, and network efficiency in enterprise environments.
