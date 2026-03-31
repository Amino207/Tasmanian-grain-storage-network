# Tasmanian Grain Storage Network

A multi-site Cisco Packet Tracer network designed to support communication between a farm, grain transport operators, and a remote storage facility. This project was built to model a practical agricultural logistics scenario and demonstrates structured network design, dynamic routing, core network services, and layered security controls.

<img width="1798" height="1103" alt="Screenshot 2026-03-31 at 22 57 44" src="https://github.com/user-attachments/assets/b79d4837-817f-4cab-bca8-f0b724a098d4" />


## Project Summary

This project simulates a real-world scenario in which a wheat farmer in Tasmania requires urgent communication with transport operators and a remote storage provider after local grain storage capacity becomes insufficient.

To support this scenario, the network was designed as a **segmented multi-site topology** consisting of three main operational environments:

- **Farm LAN**
- **Delivery LAN**
- **Storage LAN**

These sites are connected through a **routed WAN backbone**, allowing communication between operationally separate locations while maintaining structure, scalability, and administrative control.

The project was implemented in **Cisco Packet Tracer** and includes a combination of routing, addressing, network services, wireless connectivity, and security features that reflect core CCNA-level networking concepts.

---

## Network Objectives

The main objectives of the project were:

- design a structured multi-site network rather than a flat local topology
- support communication between farm, delivery, and storage environments
- implement dynamic routing across the backbone using OSPF
- Implementing routing redundancy 
- deploy DHCP and DNS services to improve usability and management
- apply layered security through firewall boundaries and hardening measures
- improve resilience through distributed server deployment

---

## Topology Overview

The topology is divided into three main LANs, each representing a separate operational part of the scenario:

### Farm LAN
The Farm LAN represents the farmer’s local network environment. It includes the farm server, desktop PC, laptop, smartphone, wireless access components, and farm-related IoT devices. This site acts as the starting point of the operational workflow, where storage shortages are identified and communication with the wider network begins.

### Delivery LAN
The Delivery LAN represents the grain transport coordination environment. It includes the transfer server, desktop PC, tablet, smartphone, and transport-related connectivity. This section was designed to reflect communication requirements for operators who need updates while moving between locations.

### Storage LAN
The Storage LAN represents the remote storage facility. It includes the storage server, desktop PC, smartphone, and storage-related devices. This site models the destination environment where additional storage capacity is managed once the farm’s local storage is no longer sufficient.

---

## Core Technologies Implemented

### Routing
- **OSPF dynamic routing**
- **Loopback interfaces** on routers for stable logical identification
- **Passive interfaces** configured on loopback and LAN-facing interfaces for routing hardening
- Point-to-point WAN subnetting using `/30` networks
  
<img width="1800" height="698" alt="Screenshot 2026-03-31 at 23 18 24" src="https://github.com/user-attachments/assets/796a6036-e594-4321-9464-5a2c72eb6947" />

  

### Network Services
- **DHCP** for dynamic address allocation to wireless/mobile end hosts
- **DNS** configured on all three servers for name resolution of key devices and infrastructure
- Static addressing for important infrastructure devices such as routers, firewalls, and servers

### Security
- **ASA firewalls** with inside and outside interfaces at site boundaries
- **Network segmentation** across Farm, Delivery, and Storage LANs
- **WPA2-PSK with AES** for wireless security
- **Unused interfaces disabled** on routers and switches
- **OSPF passive interface configuration** to prevent unnecessary neighbour formation on internal LAN segments

### Infrastructure
- Cisco ISR routers
- Layer 3 switching for backbone interconnection
- Access switches for local site connectivity
- Dedicated servers in each LAN
- Wireless access and mobile end devices

---

## Why Layer 3 Switches Were Used

Layer 3 switches were included in the topology because the selected router model did not provide enough physical interfaces to support all required backbone connections(packet tracer limitation does not allowed to configure more than 2 ip addresses). As a result, the Layer 3 switches provided a practical solution for handling multiple routed interconnections within the network while maintaining efficient communication between the core parts of the topology.

---

## Why OSPF Was Used

OSPF was selected because the topology contains multiple routers and several routed links between operationally separate network areas. Using OSPF allowed route exchange to happen dynamically, reducing the need for extensive static routing and making the network easier to manage, troubleshoot, and scale.

---

## Why Loopback Interfaces Were Implemented

Loopback interfaces were configured on the routers to provide stable logical addresses that are not dependent on physical interface status. This improves router identification within the OSPF environment and supports a more structured routing design.

---


## DHCP and DNS Implementation

DHCP was used to allocate IP addresses dynamically to wireless and mobile clients, making the network more realistic and easier to manage. This was especially useful for devices such as smartphones, tablets, and laptops connected through the wireless environment.

DNS was configured on all three servers so that key infrastructure devices and services could be accessed by name rather than relying only on IP addresses. Since DHCP-assigned client addresses can change, DNS was focused mainly on **stable devices and infrastructure records**.

<img width="1789" height="1070" alt="Screenshot 2026-03-31 at 23 15 44" src="https://github.com/user-attachments/assets/198b3189-58f9-4e5d-86da-0e0daeb63643" />


### Configured DNS Records

The DNS service on the servers was configured with records for key network devices, including:

- `farm-srv` → `192.168.10.20`
- `transfer-srv` → `192.168.20.20`
- `storage-srv` → `192.168.30.20`
- `pc0` → `192.168.10.10`
- `pc1` → `192.168.20.10`
- `pc2` → `192.168.30.10`
- `r1` → `1.1.1.1`
- `r2` → `2.2.2.2`
- `r3` → `3.3.3.3`
- `r4` → `4.4.4.4`
- `r5` → `5.5.5.5`
- `r-core` → `13.13.13.13`

This allowed key devices to be identified consistently across the topology and improved the realism of the implementation.

---

## Security Overview

Security was built into the topology rather than added afterwards. The implementation follows a layered approach that combines segmentation, firewall protection, wireless security, interface hardening, and routing hardening.

Key security measures include:

- ASA firewall boundaries between LANs and the routed backbone
- separate subnets for each operational environment
- WPA2-PSK with AES for wireless access protection
- shutdown of unused router and switch interfaces
- passive OSPF interfaces on loopback and LAN-facing links
- controlled use of static and dynamic addressing

This created a cleaner and more secure network structure suitable for the scope of the project.

---

## Testing Scope

The Packet Tracer model was tested to verify:

- local communication within each LAN
- end-to-end communication between Farm, Delivery, and Storage sites
- OSPF neighbour relationships and route propagation
- DHCP address assignment for wireless clients
- DNS name resolution
- firewall-aware traffic flow
- server reachability across the topology

---

## Skills Demonstrated

This project demonstrates practical work in:

- multi-site network design
- IP addressing and subnetting
- OSPF configuration
- loopback and passive interface use
- DHCP and DNS deployment
- firewall-aware topology design
- wireless security implementation
- interface hardening
- technical documentation and network presentation

---

## Author

Amin Kazemi 
