# Mission 09 – Single-Area OSPF

---

# Objective

Configure and verify Single-Area OSPF (Area 0) on multiple routers to enable dynamic routing across an enterprise network.

---

# Learning Outcomes

After completing this mission, I should be able to:

- Explain the purpose of OSPF
- Compare OSPF with RIP
- Configure OSPF Area 0
- Advertise networks using OSPF
- Verify OSPF neighbor relationships
- Analyze the OSPF routing table
- Troubleshoot OSPF issues

---

# Theory Review

Open Shortest Path First (OSPF) is a link-state routing protocol widely used in enterprise networks.

Unlike RIP, OSPF does not rely on hop count. Instead, it calculates the shortest path using Cost, which is based primarily on interface bandwidth.

OSPF routers exchange Link-State Advertisements (LSAs) to build a complete map of the network.

Each router independently calculates the best path using Dijkstra's Shortest Path First (SPF) algorithm.

Area 0 is known as the Backbone Area and is required for all multi-area OSPF deployments.

---

# Devices Required

- 3 × Cisco 2911 Routers
- 3 × Cisco 2960 Switches
- 6 × PCs

---

# Network Plan

| Network | Address |
|----------|----------------|
| LAN A | 192.168.10.0/24 |
| LAN B | 192.168.20.0/24 |
| LAN C | 192.168.30.0/24 |
| R1-R2 | 10.0.12.0/30 |
| R2-R3 | 10.0.23.0/30 |

---

# IP Addressing

## Router 1

| Interface | Address |
|------------|----------------|
| G0/0 | 192.168.10.1/24 |
| G0/1 | 10.0.12.1/30 |

---

## Router 2

| Interface | Address |
|------------|----------------|
| G0/0 | 10.0.12.2/30 |
| G0/1 | 10.0.23.1/30 |
| G0/2 | 192.168.20.1/24 |

---

## Router 3

| Interface | Address |
|------------|----------------|
| G0/0 | 10.0.23.2/30 |
| G0/1 | 192.168.30.1/24 |

---

# Topology

Router1 ----- Router2 ----- Router3

Each router connects to its own LAN through a Cisco 2960 switch.

---

# Configuration Tasks

On every router:

1. Configure interfaces
2. Enable OSPF Process ID 1
3. Advertise all connected networks
4. Place every network into Area 0
5. Save the configuration

---

# Verification

Run:

show ip route

show ip ospf neighbor

show ip ospf interface brief

show ip protocols

show running-config

Verify:

- OSPF neighbors are FULL
- OSPF routes appear in the routing table
- Area 0 is configured
- Every router has learned remote networks

---

# Connectivity Tests

Successful

PC1 → PC6

PC2 → PC4

PC3 → PC5

PC6 → PC1

Verify communication between all LANs.

---

# Simulation Mode

Observe:

- OSPF Hello packets
- OSPF Database Description packets
- OSPF Link-State Updates
- ICMP Echo Requests
- ICMP Echo Replies

---

# Troubleshooting Challenge

Scenario 1

Configure Router 3 with Area 1 while the other routers use Area 0.

Observe that OSPF neighbors fail to form.

Correct the area configuration.

---

Scenario 2

Configure an incorrect network statement.

Observe that the router fails to advertise the correct network.

Correct the network statement.

---

Scenario 3

Shutdown the interface between Router 2 and Router 3.

Observe how OSPF removes routes from the routing table.

Restore the interface.

---

# Questions

1. What is OSPF?
2. What type of routing protocol is OSPF?
3. What metric does OSPF use?
4. What is Area 0?
5. What is an OSPF neighbor?
6. Which command displays OSPF neighbors?
7. Why is OSPF preferred over RIP?
8. What algorithm does OSPF use?
9. What happens when a link fails?
10. Why does OSPF converge faster than RIP?

---

# Key Takeaways

- OSPF is a link-state routing protocol.
- OSPF uses Cost instead of hop count.
- OSPF converges quickly after topology changes.
- OSPF builds neighbor relationships before exchanging routes.
- Area 0 is the backbone of every OSPF network.


router ospf 1

means:

“Start OSPF (process ID 1 — just a label inside the router)”

This part:
network 192.168.10.0 0.0.0.255 area 0

means:

“Enable OSPF on this network and place it inside Area 0”

Quick decoding (important)
Subnet Mask	Wildcard
255.255.255.0	0.0.0.255
255.255.255.252	0.0.0.3

Wildcard is just:

“Which part should OSPF ignore?”

---

# Lab Summary

This lab introduced Single-Area OSPF, one of the most widely used enterprise routing protocols. Three routers established OSPF neighbor relationships, exchanged link-state information, and automatically learned remote networks. Successful testing confirmed full connectivity across all LANs and demonstrated the speed and efficiency of OSPF compared to RIP.# Mission 09
