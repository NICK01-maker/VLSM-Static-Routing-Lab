# 🌐 VLSM & Static Routing Project
*Projet de découpage VLSM et Routage Statique*

![Network Topology](Network_topology.png)

---

## 🇺🇸 English Version

### 📋 Project Overview
This project, designed during my **CCNA 1 training**, simulates a network infrastructure for a company with two expanding branches. The goal is to interconnect them securely while optimizing IP address usage.

**Note on Naming:** The device hostnames in the simulation are in French:
* `Succursale` = Branch Office
* `SwitchSucc` = Branch Switch

### ⚙️ Key Features
* **VLSM Implementation:** Optimized subnetting for the `192.168.40.0/24` network based on specific host requirements (35 hosts and 23 hosts).
* **Static Routing:** Configured between **Succursale1** and **Succursale2** routers to ensure full connectivity between the two distinct LANs.
* **Documentation:** Full configuration files are included in this repository.

### 📊 Addressing Table
| Device | Interface | IP Address | Subnet Mask | Default Gateway |
| :--- | :--- | :--- | :--- | :--- |
| **Succursale1** | G0/0/0 | 192.168.40.97 | 255.255.255.252 | N/A |
| | G0/0/1 | 192.168.40.65 | 255.255.255.224 | N/A |
| **Succursale2** | G0/0/0 | 192.168.40.98 | 255.255.255.252 | N/A |
| | G0/0/1 | 192.168.40.1 | 255.255.255.192 | N/A |
| **SwitchSucc1** | Vlan1 | 192.168.40.66 | 255.255.255.224 | 192.168.40.65 |
| **SwitchSucc2** | Vlan1 | 192.168.40.2 | 255.255.255.192 | 192.168.40.1 |
| **AgentSucc1** | NIC | 192.168.40.94 | 255.255.255.224 | 192.168.40.65 |
| **AgentSucc2** | NIC | 192.168.40.62 | 255.255.255.192 | 192.168.40.1 |

### 🧮 VLSM Design (Subnetting)
*Base Network: 192.168.40.0/24*

| Description | Network Address (CIDR) | Subnet Mask | 1st Address | Broadcast | Hosts Needed |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Subnet1** | 192.168.40.0/26 | 255.255.255.192 | 192.168.40.1 | 192.168.40.63 | **35** |
| **Subnet2** | 192.168.40.64/27 | 255.255.255.224 | 192.168.40.65 | 192.168.40.95 | **23** |
| **Subnet3** | 192.168.40.96/30 | 255.255.255.252 | 192.168.40.97 | 192.168.40.99 | **2** |

---

## 🇫🇷 Version Française

### 📋 Présentation
Ce projet simule l'interconnexion de deux succursales d'entreprise. Il met en pratique le découpage **VLSM** pour adapter les masques de sous-réseau au nombre réel d'hôtes requis, évitant le gaspillage d'adresses.

### ⚙️ Points Techniques
* **Routage Statique :** Configuré manuellement entre les routeurs `Succursale1` et `Succursale2` pour permettre le ping de bout en bout.
* **VLSM :** Calcul précis pour les besoins de 35 hôtes (Subnet 1) et 23 hôtes (Subnet 2).
* **Documentation :** Les fichiers de configuration (running-config) sont disponibles dans les fichiers `.txt` de ce dépôt.

### 🛠️ Comment tester (How to test)
1. Download `Lab_vlsm_and_static_routing.pkt`.
2. Open with Cisco Packet Tracer.
3. Ping from **AgentSucc1** to **AgentSucc2**.
