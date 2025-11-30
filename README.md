# Secure Host-Specific Site-to-Site IPsec VPN with Redundancy

![Cisco Packet Tracer](https://img.shields.io/badge/Simulation-Cisco%20Packet%20Tracer-blue)
![Protocol](https://img.shields.io/badge/Protocol-IPsec%20VPN-red)
![Security](https://img.shields.io/badge/Encryption-AES--256-green)

## 📄 Abstract
This project implements a secure **Site-to-Site IPsec VPN tunnel** between two organizations, *MyCo* and *TheirCo*. Unlike standard VPNs that tunnel all traffic between subnets, this solution utilizes Access Control Lists (ACLs) to restrict encrypted communication exclusively between **System-A** (MyCo) and **System-C** (TheirCo).

To ensure high availability and reliability, the network design incorporates **Port-Channel (EtherChannel)** for internal link redundancy and **Dual ISP Serial Links** for WAN failover.

## 👥 Team Members
* **Surya Pramod** - BL.SC.U4AIE24252
* **S.Santhosh** - BL.SC.U4AIE24248
* **Varshith KCS** - BL.SC.U4AIE24235

---

## 🏗️ Project Architecture

### Key Features
* [cite_start]**Host-Specific Tunneling:** Encrypted traffic is permitted *only* between specific hosts (System-A and System-C)[cite: 232].
* [cite_start]**Strong Encryption:** Uses **AES-256** encryption with Pre-Shared Key (PSK) authentication[cite: 233].
* [cite_start]**Internal Redundancy:** Configured Port-Channel between the router and switch to increase bandwidth and provide link failover[cite: 234].
* [cite_start]**WAN Redundancy:** Dual ISP serial links configured with adjusted administrative distances to allow automatic failover if the primary link goes down[cite: 246].

### Network Topology
The network consists of:
1.  **MyCo Site:** Hosting System-A (10.6.48.1/16).
2.  **TheirCo Site:** Hosting System-C (10.196.31.8/24).
3.  **ISP Layer:** Connecting the two sites via Primary and Backup serial links.

---

## 🛠️ Technologies & Components
* **Hardware Simulation:** Cisco 2811 Routers, Cisco 2950-24 Switches.
* [cite_start]**Protocols:** * **IPsec (Internet Protocol Security):** For data confidentiality and integrity[cite: 483].
    * [cite_start]**ISAKMP (IKEv1):** For negotiating security associations[cite: 302].
    * **ESP (Encapsulating Security Payload):** For encapsulating data.
* **Redundancy Protocols:** EtherChannel (L2), Floating Static Routes (L3).

---

## ⚙️ Configuration Highlights

### 1. ISAKMP (Phase 1) Policy
We established the IKE Phase 1 policy to handle the secure key exchange using AES-256 and SHA hashing.

```cisco
crypto isakmp policy 10
 encr aes 256
 authentication pre-share
 group 5
 lifetime 3600
