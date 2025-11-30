# Secure Host-Specific Site-to-Site IPsec VPN with Redundancy

![Status](https://img.shields.io/badge/Status-Completed-success)
![Tool](https://img.shields.io/badge/Cisco-Packet%20Tracer-blue)
![Security](https://img.shields.io/badge/Security-IPsec%20AES--256-red)

## 📄 Abstract
This project focuses on establishing a secure **Site-to-Site IPsec VPN tunnel** between two organizations, *MyCo* and *TheirCo*. Unlike standard VPNs that tunnel traffic between entire subnets, this solution implements strict **Host-Specific Tunneling**. [cite_start]Encrypted communication is permitted *exclusively* between **System-A** (MyCo) and **System-C** (TheirCo), while traffic from other devices is blocked or routed normally[cite: 6].

To ensure network resilience, the design includes:
* [cite_start]**Internal Redundancy:** Port-Channel (EtherChannel) links between routers and switches[cite: 8].
* [cite_start]**WAN Redundancy:** Dual ISP serial links with automatic failover capabilities[cite: 8].

---

## 👥 Team Members
| Name | ID |
| :--- | :--- |
| **Surya Pramod** | BL.SC.U4AIE24252 |
| **S.Santhosh** | BL.SC.U4AIE24248 |
| **Varshith KCS** | BL.SC.U4AIE24235 |

[cite_start]*[cite: 3]*

---

## 🏗️ Network Topology & Design

### IP Addressing Schema
| Device | Interface | IP Address | Subnet Mask | Description |
| :--- | :--- | :--- | :--- | :--- |
| **System-A** | NIC | 10.6.48.1 | 255.255.0.0 | [cite_start]MyCo Host (Allowed) [cite: 33] |
| **System-C** | NIC | 10.196.31.8 | 255.255.255.0 | [cite_start]TheirCo Host (Allowed) [cite: 35] |
| **MyCo Router** | Serial 1/1 | 103.24.99.2 | 255.255.255.252 | [cite_start]Primary Link [cite: 103] |
| **MyCo Router** | Serial 1/2 | 103.24.99.102 | 255.255.255.252 | [cite_start]Backup Link [cite: 107] |

### Key Components
* [cite_start]**Routers:** Cisco 2811 (handling ISAKMP, IPsec, and routing)[cite: 48].
* [cite_start]**Switches:** Cisco 2950-24 (configured with EtherChannel)[cite: 45].
* **End Devices:** Specific PCs and Servers designated for secure communication.

 authentication pre-share
 group 5
 lifetime 3600
