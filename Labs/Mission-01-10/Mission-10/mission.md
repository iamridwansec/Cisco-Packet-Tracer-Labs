# Mission 10 – Dynamic Host Configuration Protocol (DHCP)

---

# Objective

Configure a Cisco router as a DHCP server to automatically assign IP addresses, subnet masks, default gateways, and DNS server information to client devices.

---

# Learning Outcomes

After completing this mission, I should be able to:

- Explain the purpose of DHCP
- Describe the DHCP DORA process
- Configure a router as a DHCP server
- Exclude reserved IP addresses
- Verify DHCP leases
- Troubleshoot DHCP issues

---

# Theory Review

Dynamic Host Configuration Protocol (DHCP) automatically assigns network configuration to client devices.

Without DHCP, every device must be configured manually.

DHCP reduces configuration errors, saves administrative time, and simplifies network management.

DHCP operates using the DORA process:

Discover → Offer → Request → Acknowledgment

Ports Used:

Client → UDP 68

Server → UDP 67

---

# Devices Required

- 1 × Cisco 2911 Router
- 1 × Cisco 2960 Switch
- 6 × PCs

---

# Network Plan

| Network | Address |
|----------|----------------|
| LAN | 192.168.10.0/24 |

Gateway

192.168.10.1

DNS

8.8.8.8

---

# Address Reservation

Reserve these addresses:

192.168.10.1

192.168.10.2

192.168.10.3

192.168.10.4

192.168.10.5

Clients should receive addresses beginning at:

192.168.10.6

---

# Topology

PCs
      |
Cisco 2960
      |
Cisco 2911

---

# Configuration Tasks

Router

1. Configure interface G0/0
2. Exclude reserved addresses
3. Create DHCP Pool "LAN"
4. Configure network
5. Configure default gateway
6. Configure DNS server
7. Save configuration

PCs

1. Open Desktop
2. Open IP Configuration
3. Select DHCP
4. Verify automatic IP assignment

---

# Verification

Run:

show ip dhcp binding

show ip dhcp pool

show running-config

Verify:

- DHCP pool exists
- Clients receive addresses
- Gateway is assigned
- DNS server is assigned

---

# Connectivity Tests

Successful

PC1 → PC2

PC3 → PC6

PC1 → Router

Verify that every PC received a unique IP address.

---

# Simulation Mode

Observe:

- DHCP Discover
- DHCP Offer
- DHCP Request
- DHCP Acknowledgment

Observe the complete DORA process.

---

# Troubleshooting Challenge

Scenario 1

Remove the DHCP pool.

Attempt DHCP renewal.

Restore the pool.

---

Scenario 2

Configure an incorrect default gateway.

Observe communication failure.

Correct the gateway.

---

Scenario 3

Exclude the entire address range.

Observe that clients cannot receive addresses.

Restore the exclusions.

---

# Questions

1. What is DHCP?
2. What problem does DHCP solve?
3. What does DORA stand for?
4. Which UDP ports does DHCP use?
5. Why are IP addresses excluded?
6. Which command displays DHCP bindings?
7. What happens if no DHCP server exists?
8. Why should routers keep reserved addresses?
9. What information does DHCP provide?
10. Why is DHCP preferred over static addressing?

---

# Key Takeaways

- DHCP automates IP address assignment.
- DHCP uses the DORA process.
- Excluded addresses protect reserved devices.
- DHCP simplifies administration in enterprise networks.
- Every client receives a unique network configuration automatically.

---


# Lab Summary

This lab demonstrated how to configure a Cisco router as a DHCP server. Client devices automatically received IP addresses, subnet masks, default gateways, and DNS information. The DORA process was observed in Simulation Mode, providing a clear understanding of how DHCP operates in modern networks.# Mission 10
