#  Azure Honeypot & SIEM Threat Intelligence Lab

[![Azure](https://img.shields.io/badge/Azure-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com/)
[![T-Pot](https://img.shields.io/badge/Honeypot-T--Pot-red?style=for-the-badge)](https://github.com/telekom-security/tpotce)
[![SIEM](https://img.shields.io/badge/SIEM-Kibana-blue?style=for-the-badge&logo=kibana&logoColor=white)](https://www.elastic.co/kibana)

##  Project Overview
This project demonstrates the deployment of a cloud-native honeypot environment using **Microsoft Azure** and the **T-Pot** multi-honeypot platform. The primary objective is to entice, capture, and analyze real-world cyberattacks in a controlled environment to gain insights into global threat actor behaviors.

By exposing intentionally vulnerable services to the public internet, this lab provides firsthand experience in **Threat Intelligence**, **Log Analysis**, and **Security Visualization** via the Kibana dashboard.

###  Key Objectives
* **Attack Discovery:** Identify real-time attack sources, including geographical location and ISP data.
* **Credential Intelligence:** Capture frequently used usernames and passwords from brute-force attempts.
* **Behavioral Analysis:** Monitor intruder actions, executed commands, and dropped malware samples.
* **SIEM Mastery:** Utilize the ELK stack (Elasticsearch, Logstash, Kibana) for security monitoring and visualization.

---

##  Tech Stack
* **Cloud Infrastructure:** Microsoft Azure (Virtual Machines, NSGs)
* **Operating System:** AlmaLinux 9 (x64 Gen2)
* **Honeypot Framework:** T-Pot (Standard/HIVE)
* **Visualization/SIEM:** Kibana (ELK Stack)
* **Networking:** Network Security Groups (NSG) & Port Forwarding

---

##  Deployment Steps

### 1. Azure Environment Setup
1. Create a **Resource Group** (e.g., `Honeypot-Lab`).
2. Deploy a **Virtual Machine**:
   - **Image:** AlmaLinux 9.
   - **Size:** `Standard_B4ms` (Recommended: 4 vCPUs, 16 GiB RAM).
3. **Configure Networking:**
   - In the Network Security Group (NSG), create an **Inbound Security Rule**.
   - Set **Destination Port Ranges** to `*` (Allow all).
   - Set **Action** to `Allow`.
   - *Note: This opens the VM to the entire internet to attract attackers.*

### 2. T-Pot Installation
Connect to your VM via SSH and run the following commands:

```bash
# Update the system
sudo yum update -y
sudo yum install python3 git -y

# Clone the T-Pot repository
git clone [https://github.com/telekom-security/tpotce.git](https://github.com/telekom-security/tpotce.git)
cd tpotce

# Execute the installer
./install.sh
