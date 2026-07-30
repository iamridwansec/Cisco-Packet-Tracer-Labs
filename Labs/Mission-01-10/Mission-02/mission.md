# Mission 02

# Mission 02 – Switch MAC Address Learning and ARP

---

# Objective

Understand how a switch learns MAC addresses and how ARP works before communication begins.

This lab focuses on what happens behind the scenes when devices communicate in a LAN.

---

# Learning Outcomes

After completing this mission, I should be able to:

- Explain how a switch learns MAC addresses
- Describe how ARP works
- Observe MAC address table population
- Understand frame forwarding
- Use CLI to verify switch behavior

---

# Theory Review

When a PC sends data to another PC in the same network, it needs the destination MAC address.

If the MAC address is unknown, the PC sends an ARP request as a broadcast.

The switch floods this broadcast to all ports.

The destination device replies with its MAC address.

The switch then learns MAC addresses by associating them with the ports they come from.

This information is stored in the MAC address table.

---

# Devices Required

- 1 × Cisco 2960 Switch
- 2 × PCs

---

# IP Addressing Table

| Device | IP Address | Subnet Mask | Default Gateway |
|--------|------------|-------------|-----------------|
| PC1 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC2 | 192.168.1.20 | 255.255.255.0 | 192.168.1.1 |

---

# Topology

PC1 → Switch → PC2

Use Copper Straight-Through cables.

---

# Practical Tasks

1. Place 1 switch and 2 PCs
2. Connect both PCs to the switch
3. Assign IP addresses
4. Save the topology

---

# Simulation Mode Analysis

Switch to Simulation Mode.

Perform a ping from PC1 to PC2.

Observe:

- ARP Request (Broadcast)
- ARP Reply (Unicast)
- ICMP Echo Request
- ICMP Echo Reply

Watch how the switch floods then learns.

---

# Verification

On the switch CLI, run:

show mac address-table

show running-config

Observe:

- MAC addresses learned
- Ports associated with devices

---

# Expected Behavior

First Ping:

- ARP process occurs
- Slight delay

Second Ping:

- Faster
- No ARP broadcast

---

# Troubleshooting Challenge

1. Clear ARP cache and test again
2. Disconnect cable and observe failure
3. Change IP to wrong subnet and test

---

# Questions

1. What is ARP?
2. Why does the first ping take longer?
3. What is a MAC address?
4. How does a switch learn MAC addresses?
5. What happens when the switch does not know the destination MAC?
6. What is the difference between broadcast and unicast?
7. Why is ARP necessary?

---

# Key Takeaways

- Switches learn MAC addresses dynamically
- ARP resolves IP to MAC
- First communication uses broadcast
- Subsequent communication is faster due to learning

---

# Lab Summary

This lab demonstrated how switches learn MAC addresses and how ARP enables communication between devices in the same network. By observing Simulation Mode, the internal processes of ARP and frame forwarding were clearly understood.


