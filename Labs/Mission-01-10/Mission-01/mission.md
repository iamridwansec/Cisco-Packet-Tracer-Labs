# Mission 01 – Building a Basic Local Area Network (LAN)

# Objective
Build a functional Local Area Network (LAN) using a Layer 2 switch and four PCs. Configure IPv4 addressing, verify end-to-end connectivity, observe how the switch learns MAC addresses, and understand communication within the same subnet.

# Learning Outcomes
After completing this mission, I should be able to:

- Explain what a LAN is.
- Identify the role of a Layer 2 switch.
- Configure IPv4 addresses on PCs.
- Verify connectivity using ping.
- View the switch MAC address table.
- Troubleshoot basic Layer 1, Layer 2, and Layer 3 issues.

# Theory Review
A Local Area Network (LAN) connects devices within a limited geographical area such as a home, office, or school. In this lab, a Cisco 2960 switch forwards Ethernet frames based on MAC addresses.

All four PCs are placed in the same IPv4 subnet (192.168.1.0/24). Since they are on the same network, communication occurs through the switch without requiring a router.

When one PC sends traffic to another for the first time, it first discovers the destination MAC address using ARP. The switch learns the source MAC addresses on each port and stores them in its MAC address table to improve forwarding efficiency.

# Devices Required
| Device            | Quantity |
| ----------------- | -------: |
| Cisco 2960 Switch |        1 |
| PC                |        4 |

# IP Addressing Table
| Device | IP Address   | Subnet Mask   | Default Gateway |
| ------ | ------------ | ------------- | --------------- |
| PC1    | 192.168.1.10 | 255.255.255.0 | 192.168.1.1     |
| PC2    | 192.168.1.20 | 255.255.255.0 | 192.168.1.1     |
| PC3    | 192.168.1.30 | 255.255.255.0 | 192.168.1.1     |
| PC4    | 192.168.1.40 | 255.255.255.0 | 192.168.1.1     |

        +-------------------+
        |   Cisco 2960      |
        +-------------------+
          |   |   |   |
          |   |   |   |
         PC1 PC2 PC3 PC4   

# Practical Tasks
Tasks
Place one Cisco 2960 switch.
Place four PCs.
Connect each PC to the switch.
Configure the IP addresses from the addressing table.
Save the topology.

# Verification
Ping PC2 from PC1.
Ping PC3 from PC1.
Ping PC4 from PC1.

On the switch CLI, run:
show mac address-table
show interfaces status
show running-config


# Questions
1. What is a Local Area Network (LAN)?

2. Why is a switch used instead of connecting computers directly?

3. What is the purpose of an IPv4 address?

4. What is the purpose of a subnet mask?

5. Why should every host have a unique IP address?

6. What is a MAC address?

7. How does a switch learn MAC addresses?

8. Why does every device in this lab belong to the same subnet?

9. Why are straight-through cables used in this lab?

10. What command allows you to view the MAC address table?

# Key Takeaways
After completing this lab, I can:

- Build a simple LAN using a Layer 2 switch.
- Configure IPv4 addresses on end devices.
- Verify connectivity using ping.
- Understand how switches learn MAC addresses.
- Identify and troubleshoot common Layer 1 and Layer 3 issues.
- Save and document a Packet Tracer project professionally.

# Lab Summary
Mission 01 introduced the process of building a basic Local Area Network (LAN) using a Cisco 2960 switch and four PCs. The lab covered IPv4 addressing, physical connectivity, connectivity testing with ping, and verification using the switch's MAC address table. Basic troubleshooting exercises demonstrated how common configuration mistakes affect network communication and how to identify and resolve them.


Perform each mistake one at a time.

Scenario 1
- Disconnect PC2 from the switch.
- Attempt to ping PC2 from PC1.
- Record the result.
- Reconnect the cable.

Scenario 2
- Change PC3's IP address to 192.168.2.30.
- Ping PC3 from PC1.
- Observe the failure.
- Restore the correct IP address.

Scenario 3
- Configure PC4 with the same IP address as PC2.
- Observe the network behavior.
- Restore a unique IP address.

For each scenario, answer:

1. What happened?
2. Why did it happen?
3. How did you fix it?
