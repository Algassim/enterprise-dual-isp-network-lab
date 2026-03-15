# enterprise-dual-isp-network-lab
Enterprise Network Design Lab using EVE-NG with Dual ISP, FortiGate Firewall,ASA Firewall, BGP, EIRGP, OSPF, SD-WAN and DMZ architecture.

## Overview
This project simulates an enterprise network architecture using EVE-NG.

The design includes:

- Dual ISP connectivity
- FortiGate firewall cluster
- ASA ACL policy acitve passive failover
- BGP routing with ISPs
- EIRGP for LAN
- OSPF internal routing
- DMZ network
- SD-WAN implementation
- NAT and security policies

## Technologies Used

- Cisco IOS
- FortiGate Firewall
- ASA firewall
- BGP
- EIRGP
- OSPF
- SD-WAN
- EVE-NG

## Network Topology

![Topology](topology.png)

## Key Features

- Redundant ISP connectivity
- Firewall high availability
- Traffic engineering with BGP
- DMZ segmentation
- Enterprise-grade security design

# Verification & Troubleshooting

The following commands were used to validate connectivity across the enterprise network from the **Access Layer → Distribution/Core → ASA → FortiGate → ISPs**.

# 1. Access Switch Verification

Verify that end devices are connected to the correct VLAN and switch ports.

show vlan brief  
show interfaces status  
show mac address-table  
show mac address-table dynamic  
show spanning-tree  

Check which port a specific device is connected to:

show mac address-table address <MAC_ADDRESS>

Verify trunk links to distribution/core switches:

show interfaces trunk  

Test connectivity to the default gateway:

ping <gateway-ip>

---

# 2. Distribution / Core Switch Verification (EIGRP)

Verify internal routing across the enterprise network.

Check EIGRP neighbors:

show ip eigrp neighbors  

Verify EIGRP topology table:

show ip eigrp topology  

Verify routing table:

show ip route  

Check only EIGRP learned routes:

show ip route eigrp  

Test connectivity between internal networks:

ping <remote-lan-network>

---

# 3. Cisco ASA Firewall Verification

Verify ASA interface status:

show interface ip brief  

Verify routing table:

show route  

Check NAT configuration:

show nat  
show xlate  

Verify access control lists:

show access-list  

Verify VPN security associations if configured:

show crypto isakmp sa  
show crypto ipsec sa  

Simulate traffic through the firewall:

packet-tracer input inside icmp <source-ip> 8 0 <destination-ip>

---

# 4. FortiGate Firewall Verification

Verify interfaces:

get system interface  

Verify routing table:

get router info routing-table all  

Verify BGP neighbors:

get router info bgp summary  

Verify SD-WAN status:

diagnose sys sdwan health-check  

Verify firewall policies:

show firewall policy  

---

# 5. ISP Router Verification (BGP)

Verify BGP neighbors:

show ip bgp summary  

Verify BGP routes:

show ip bgp  

Verify routing table:

show ip route  

---

# 6. End-to-End Connectivity Testing

Validate connectivity from internal networks to the ISPs.

ping 1.1.1.1  
ping 2.2.2.2  

Verify the path taken to reach the ISP networks:

traceroute 1.1.1.1  
traceroute 2.2.2.2  

---

# 7. Failover / Redundancy Testing

Simulate ISP failure and verify traffic rerouting.

Example procedure:

• Shut down the primary ISP interface  
• Verify BGP reconvergence  
• Confirm traffic switches to the backup ISP  

Verification commands:

show ip bgp summary  
show ip route  
ping 1.1.1.1  
ping 2.2.2.2  

---

# Validation Results

The following were successfully verified:

✔ VLAN segmentation and switching at the access layer  
✔ EIGRP neighbor adjacency across internal routers  
✔ Firewall NAT and security policy enforcement  
✔ BGP peering with both ISPs  
✔ End-to-end connectivity to ISP networks  
✔ Network redundancy and failover behavior


