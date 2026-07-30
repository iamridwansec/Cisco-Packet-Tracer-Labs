# Mission 06

# Mission 06 – Static Routing

---

# Objective

Learn how to configure Static Routing between two routers so that devices on different networks can communicate.

---

# Learning Outcomes

After completing this mission, I should be able to:

- Explain the purpose of routing
- Differentiate between directly connected and remote networks
- Configure static routes
- Verify the routing table
- Test communication across multiple networks
- Troubleshoot routing problems

---

# Theory Review

Routers connect different networks.

A router automatically knows networks directly connected to its interfaces.

If a destination network is not directly connected, the router must be told how to reach it.

Static Routing is the manual process of creating routes to remote networks.

Static routes are commonly used in small or predictable networks because they are simple, secure, and require minimal resources.

---

# Devices Required

- 2 × Cisco 2911 Routers
- 2 × Cisco 2960 Switches
- 4 × PCs

---

# Network Plan

| Network | Address |
|----------|----------------|
| LAN A | 192.168.10.0/24 |
| Router Link | 10.0.0.0/30 |
| LAN B | 192.168.20.0/24 |

---

# IP Addressing

## Router 1

| Interface | Address |
|------------|----------------|
| G0/0 | 192.168.10.1/24 |
| G0/1 | 10.0.0.1/30 |

---

## Router 2

| Interface | Address |
|------------|----------------|
| G0/0 | 192.168.20.1/24 |
| G0/1 | 10.0.0.2/30 |

---

## PCs

| Device | Address | Gateway |
|---------|----------------|----------------|
| PC1 | 192.168.10.10 | 192.168.10.1 |
| PC2 | 192.168.10.20 | 192.168.10.1 |
| PC3 | 192.168.20.10 | 192.168.20.1 |
| PC4 | 192.168.20.20 | 192.168.20.1 |

---

# Topology

PC1 ----\
          \
        Switch1
           |
        Router1
           |
      10.0.0.0/30
           |
        Router2
           |
        Switch2
          / \
      PC3   PC4

---

# Configuration Tasks

On Router 1

- Configure G0/0
- Configure G0/1
- Create a static route to 192.168.20.0/24

On Router 2

- Configure G0/0
- Configure G0/1
- Create a static route to 192.168.10.0/24

Configure all PCs.

Save configurations.

---

# Verification

Router Commands

show ip interface brief

show ip route

show running-config

Verify:

- Connected routes
- Static routes
- Interface status

---

# Connectivity Tests

Successful

PC1 → PC3

PC1 → PC4

PC2 → PC3

PC4 → PC1

Every device should communicate successfully.

---

# Simulation Mode

Observe:

- ARP
- ICMP Echo Request
- ICMP Echo Reply
- Router forwarding decisions
- Packet movement across both routers

---

# Troubleshooting Challenge

Scenario 1

Delete one static route.

Observe communication failure.

Restore the route.

---

Scenario 2

Configure an incorrect default gateway on PC3.

Observe failure.

Correct the gateway.

---

Scenario 3

Shut down Router2 G0/1.

Observe routing failure.

Restore the interface.

---

# Questions

1. What is routing?
2. What is a static route?
3. Why are static routes required?
4. What is a directly connected network?
5. What is a remote network?
6. Which command displays the routing table?
7. Why do routers need routing information?
8. What happens if a static route is incorrect?
9. What does the next-hop IP address represent?
10. When should static routing be used?

---

# Key Takeaways

- Routers connect different networks.
- Static routes define paths to remote networks.
- Every router requires knowledge of remote destinations.
- Routing tables determine packet forwarding.
- Proper gateway configuration is essential.

---

# Lab Summary

This lab introduced Static Routing between two routers. Each router was manually configured with routes to remote networks, allowing communication between separate LANs. Verification of the routing table and successful end-to-end testing demonstrated how routers forward traffic beyond directly connected networks.
