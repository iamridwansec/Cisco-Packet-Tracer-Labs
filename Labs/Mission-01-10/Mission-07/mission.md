# Mission 07

# Mission 07 – Default Routing (Gateway of Last Resort)

---

# Objective

Learn how to configure and use a default route so that a router can forward traffic destined for unknown networks through a single gateway.

---

# Learning Outcomes

After completing this mission, I should be able to:

- Explain what a default route is
- Explain the Gateway of Last Resort
- Configure a default static route
- Verify the default route in the routing table
- Compare static routing with default routing
- Troubleshoot default route issues

---

# Theory Review

A router automatically knows its directly connected networks.

With static routing, you manually configure a route for every remote network.

As networks grow, this becomes difficult to manage.

A default route is a special route used whenever the router does not have a more specific route to a destination.

It is known as the Gateway of Last Resort.

Instead of maintaining many static routes, a router forwards unknown traffic to one next-hop router.

Default routing is common in branch offices where there is only one path to the rest of the network or the Internet.

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
| WAN Link | 10.0.0.0/30 |
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

| Device | Address | Default Gateway |
|---------|----------------|----------------|
| PC1 | 192.168.10.10 | 192.168.10.1 |
| PC2 | 192.168.10.20 | 192.168.10.1 |
| PC3 | 192.168.20.10 | 192.168.20.1 |
| PC4 | 192.168.20.20 | 192.168.20.1 |

---

# Topology

PC1 ---\
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
      /      \
   PC3      PC4

---

# Configuration Tasks

Router 1

- Configure interfaces
- Configure ONE default route pointing to Router 2

Router 2

- Configure interfaces
- Configure ONE default route pointing to Router 1

Configure all PCs with the correct default gateways.

Save the configuration.

---

# Verification

Run:

show ip interface brief

show ip route

show running-config

Verify:

- Gateway of Last Resort appears
- Default route is installed
- Interfaces are up

---

# Connectivity Tests

Successful

PC1 → PC3

PC1 → PC4

PC2 → PC3

PC4 → PC2

All devices should communicate successfully.

---

# Simulation Mode

Observe:

- ARP
- ICMP Echo Request
- ICMP Echo Reply
- Router forwarding using the default route

---

# Troubleshooting Challenge

Scenario 1

Delete the default route.

Test connectivity.

Restore the route.

---

Scenario 2

Configure an incorrect next-hop address.

Observe packet loss.

Correct the configuration.

---

Scenario 3

Shutdown the WAN interface.

Observe communication failure.

Restore the interface.

---

# Questions

1. What is a default route?
2. What is the Gateway of Last Resort?
3. When does a router use the default route?
4. How does a default route differ from a static route?
5. Which command displays the routing table?
6. Why is a next-hop address required?
7. What happens if the next-hop router is unreachable?
8. In what type of network is a default route commonly used?
9. How does the router choose between a static route and a default route?
10. Why are default routes useful?

---

# Key Takeaways

- A default route is used for unknown destinations.
- The Gateway of Last Resort simplifies routing.
- Default routes reduce routing table complexity.
- Routers always prefer more specific routes before using the default route.

---

# Lab Summary

This lab introduced default routing, allowing routers to forward unknown traffic through a single gateway. The Gateway of Last Resort simplified routing configuration while maintaining end-to-end connectivity between separate networks.
