# NETWORKWALKS-B083-WK1-PM1-CYBERSECURITY-ETHICAL HACKING
Hands-on Cybersecurity lab using Virtual box and Kali Linux to practice ethical hacking and penetration testing.

# 🔒 Cybersecurity Lab Environment Setup

### Building an isolated virtual lab for penetration testing and ethical hacking practice.

![Cybersecurity](https://img.shields.io/badge/Skill-Cybersecurity-red?style=for-the-badge)
![VirtualBox](https://img.shields.io/badge/Ver-VirtualBox_v7.2-blue?style=for-the-badge)
![Kali Linux](https://img.shields.io/badge/Kali_Linux-v2026.2-orange?style=for-the-badge&logo=kalilinux&logoColor=white)
![Linux](https://img.shields.io/badge/Skill-Linux-purple?style=for-the-badge)
![Network](https://img.shields.io/badge/Network-10.0.0.0%2F24-teal?style=for-the-badge)
![Penetration Testing](https://img.shields.io/badge/Penetration_Testing-maroon?style=for-the-badge&logo=kalilinux&logoColor=brown)
![Virtualization](https://img.shields.io/badge/Skill-Virtualization-teal?style=for-the-badge)
![GitHub](https://img.shields.io/badge/GitHub-black?style=for-the-badge&logo=github&logoColor=white)
![NetworkWalks](https://img.shields.io/badge/NetworkWalks-yellow?style=for-the-badge)
![Ethical Hacking](https://img.shields.io/badge/Ethical_Hacking-orange?style=for-the-badge&logo=kalilinux&logoColor=crimson)
![Nmap](https://img.shields.io/badge/Nmap-green?style=for-the-badge)   

Isolated virtual lab environment built with VirtualBox and Kali Linux for cybersecurity testing, penetration testing, and ethical hacking practice.

---

# Network Reconnaissance & Ethical Hacking Lab (B083-WK1-PM1)

## Executive Summary
This project demonstrates end-to-end network reconnaissance and vulnerability assessments using Kali Linux and Nmap within an authorized testing environment.

---

## 📌 Project Overview
This project emphasizes setting up a virtual lab environment setup using virtual box and Kali Linux to practicing penetration testing, ethical hacking and cybersecurity concepts.

The primary aim of this project is to create a secure and isolated setup where cybersecurity tools, vulnerability assessments, and network security analysis, reconnaissance, and other security testing can be performed safely within authorized boundaries.
 
---

## 🎯 Objectives
* Install and configure VirtualBox.
* Create NAT Network in the VirtualBox.
* Install/Import Kali Linux on the VirtualBox.
* Set NAT Network in the Kali Linux.
* Assign a consistent IP address to the Kali VM.
* Verify network connectivity and DNS resolution.
* Take snapshot to recover if needed.
* Document the complete setup and prepare the environment for future tasks.
---

## 🛠️ Prerequisites & Setup
* **Extraction Utility:** 7-Zip
* **Virtualization:** Oracle VM VirtualBox
* **Guest OS:** Kali Linux
* **Network Mode:** NAT / Host-Only Adapter

---

## 🚀 Setup Instructions

1. **Install 7-Zip**
   
    Install 7-zip to extract the Kali Linux virtual machine package.
   
    Download 7-Zip: https://7-zip.org/download.html

2. **Install VirtualBox**
   
   Download and install VirtualBox on the host operating system.
   
   Download VirtualBox: https://virtualbox.org/wiki/Downloads
   

3. **Create NAT Network**
   
   Configure the network settings on your Virtualbox
   (create NATNetwork in 10.0.0.0/24)
   
<img width="638" height="377" alt="Screenshot 2026-09-07 211938" src="https://github.com/user-attachments/assets/6635b33c-13eb-48cf-aa10-b57c84f25491" />

4. **Install Kali Linux**

   Import the Kali Linux ISO/OVA into VirtualBox.
   
   Download Kali Linux: https://kali.org/get-kali

    <img width="1599" height="843" alt="WhatsApp Image 2026-09-08 at 4 20 10 PM (1)" src="https://github.com/user-attachments/assets/3e89bd68-0d30-4d5a-a788-460aab4dbe66" />

   The VM network adapter was configured as follows:

```text
Adapter 1
Attached to: NAT Network
Network:     NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
```
<img width="640" height="377" alt="Screenshot 2026-09-07 212746" src="https://github.com/user-attachments/assets/88bb3950-1813-43aa-ab76-ba9ba2faad5d" />


5. **Configure Static IP on Kali Linux and DNS Connectivity**

    Configure IP on the Kali:
    
<img width="1599" height="842" alt="WhatsApp Image 2026-09-08 at 4 20 10 PM" src="https://github.com/user-attachments/assets/c79bd2dd-1d19-449e-9838-bc2398ebd6ff" />


   Open terminal in the Kali Linux and run the following commands:
   
   *For Internet connectivity issue:* ```bash sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0 ```
   
   *To deactivate network profile:* ``` bash sudo nmcli connection down Wired\ connection\ 1```
   
   *To reactivate network profile:* ```bash sudo nmcli connection up Wired\ connection\ 1```
   
   <img width="640" height="377" alt="Screenshot 2026-09-08 141253" src="https://github.com/user-attachments/assets/3f097190-42d4-4e36-ab92-182799fd5590" />


6. **Verify Network Connectivity**

    Open the terminal inside Kali Linux and run:

    ```bash
   ping -c 4 8.8.8.8
   ping -c 4 google.com
   ```
   <img width="1916" height="1010" alt="kali 3" src="https://github.com/user-attachments/assets/579309a5-85ac-4cf3-92fc-e4898287e044" />

  Verifying Results: Both 8.8.8.8 (gateway) and ```google.com``` (DNS) successfully returned 0% packet loss, confirming full outbound network connectivity.
  
7. **Create a Clean VM Snapshot**

After completing the initial network configuration and verification, a baseline VirtualBox snapshot was created.

Example snapshot name:
```bash
Clean Baseline - Post Network Setup
```
The snapshot captures the fully configured state of the laboratory environment.

If a future exercise changes system files, breaks networking, or degrades the VM state, the machine can be restored immediately to this clean baseline.

---

## 💻 Lab capabilities and purpose of the foundational domains

### 1. Network Reconnaissance

* **Objective:** Discover active devices, live host IP addresses, and gateway configurations across the local virtual network subnet.

* **Key Command:** `nmap -sn 10.0.0.0/24`
  
* **Findings:** Identified active primary local interfaces (`10.0.0.2` and `10.0.2.3`) and confirmed active local host connectivity.

<img width="510" height="275" alt="Screenshot 2026-09-09 143621" src="https://github.com/user-attachments/assets/2cc0433c-e3ee-4637-b08e-ab3d399b5553" />


### 2. Port Scanning & Service Enumeration

* **Objective:** Probe open TCP/UDP ports and identify software service versions running on target host interfaces.

* **Key Command:** `nmap -sV 127.0.0.1`
  
* **Findings:** Scanned 1,000 standard TCP ports; verified that no unnecessary background services or open ports are exposed to the network.

<img width="511" height="290" alt="Screenshot 2026-09-09 143557" src="https://github.com/user-attachments/assets/586a473a-d677-4dcf-ae3c-7fa2b9d08152" />

### 3. Vulnerability Assessment

* **Objective:** Automated scanning of identified open ports and software versions for known security vulnerabilities and CVE misconfigurations.

* **Key Command:** `nmap --script vuln 127.0.0.1`
  
* **Findings:** Automated vulnerability checks completed in 0.18 seconds with zero vulnerabilities detected, confirming a hardened security baseline.

<img width="511" height="288" alt="Screenshot 2026-09-09 143652" src="https://github.com/user-attachments/assets/f16e08b1-0375-4252-a9f2-b336b677fc26" />

### 4. Packet Analysis

* **Objective:** Inspect live network traffic flow, measure network latency, and verify ICMP packet transmission efficiency.
  
* **Key Command:** `ping -c 4 127.0.0.1`
  
* **Findings:** Transmitted 4 ICMP packets with 0% packet loss and `<0.1ms` latency, confirming proper network interface behavior.
   
   <img width="511" height="290" alt="Screenshot 2026-09-09 143715" src="https://github.com/user-attachments/assets/40421a60-7cdb-4870-99a0-f4e7a16ff0b2" />

---

   ## 🧪 Lab Tests

### Security Tool & Network Experimentation Matrix

| Phase / Module | Security Tool / Command | Command Executed | Purpose & Experiment Scope | Verified Result |
| :--- | :--- | :--- | :--- | :--- |
| **1. Network Interface Audit** | 🌐 **IP Configuration** | `ip a` | Verify local network interfaces and active assigned IP addresses. | Confirmed local interfaces `10.0.0.2` and `10.0.2.3` on `eth0`. |
| **2. Connectivity Verification** | 📡 **Gateway Reachability** | `ping -c 4 10.0.0.1` | Test ICMP Echo reachability to the local VirtualBox NAT gateway. | Transmitted 4 packets with 0% loss and instant responses. |
| **3. Internet & DNS Audit** | 🌍 **DNS Resolution** | `nslookup google.com` | Verify external internet connectivity and active DNS lookup functionality. | Domain successfully resolved public IP addresses via upstream DNS. |
| **4. Tool Environment Check** | 🧰 **Nmap Utility** | `nmap --version` | Confirm Nmap security scanning suite is installed and operational. | Nmap v7.99 verified and active on Kali Linux environment. |
| **5. Network Reconnaissance** | 🔎 **Nmap Ping Sweep** | `nmap -sn 10.0.0.0/24` | Discover live active hosts across the local NAT network subnet. | Identified active gateway (`10.0.0.1`) and local system interfaces. |
| **6. Port Scanning** | 🚪 **Service Detection** | `nmap -sV 127.0.0.1` | Probe default TCP ports to detect running services and version details. | Scanned 1,000 standard ports; confirmed no exposed services. |
| **7. Vulnerability Assessment** | 🛡️ **Nmap Engine (NSE)** | `nmap --script vuln 127.0.0.1` | Run automated CVE vulnerability checks against local interface services. | Completed scan in 0.18s; confirmed zero unpatched vulnerabilities. |
| **8. Packet Analysis** | 📊 **ICMP Transmission** | `ping -c 4 127.0.0.1` | Analyze local loopback packet delivery, round-trip time, and latency. | Transmitted 4 packets with 0% packet loss and `<0.1ms` latency. |
| **9. Penetration Testing** | 🔒 **Nmap Audit** | `nmap -Pn -sV 127.0.0.1` | Perform baseline host security audit overriding ICMP host discovery. | Verified local interface security posture is fully hardened. |
| **10. Environment Restoration** | 🔄 **Snapshot Verification** | `ip a` | Confirm system baseline state persistence after restoring VM snapshot. | Baseline network configuration successfully restored and verified. |

---

## 🐞 Problems Encountered & Solved

**Problem1:** Do we have to enable IPv6 while attacking the Virtual Boc to NAT Network?

**Solution:** NO, we don't have to enable IPv6, only enable IPv4 and check DHCP.


**Problem2:** How to take screenshot in Kali Linux?

**Solution:** Open the screenshot file from applications in Kali Linux, select the region or full window, click OK and get the screenshot in the folder.


**Problem3:** How to bring the screenshot in your PC file explorer?

**Solution:** Open the snapdrop.net in the Firefox drag the screenshot from Kali Linux open folder to the upload files option, after uploading it click on the share button and get the screenshot by the link or email.

---

## 📝 What I Learned

- **Virtual Machine Networking:**
  
  I learned that using NAT Network in VM will help the machines in the lab communicate safely.

- **Static IP configuration:**
  
  I learned how to configure IP addresses, DNS Connectivity and Gateways.

- **Screenshots in Virtual Machine:**
    
  I was stuck for too long in this, but now I know how to take screenshots in VM.

- **Network Recoinnassance:**

  Understood why detailed service scans (nmap -sV) must target specific individual host IP addresses (10.0.2.2, 10.0.2.3) rather than the subnet ID (10.0.2.0), which causes Nmap to report the host as down.

- **Snapshots:**
  
  Saved a baseline state right after setting up Kali so I can reset the VM anytime.

- **Documentation:**
  
  I learned how to do the documentation of my projects, tasks and set the environment of the lab for future tasks.

---

## 🎯 Key Takeaways & Findings

* **Network Integrity:** Verified host-to-gateway routing and DNS translation on Kali Linux (`10.0.0.0/24`).
  
* **Tool Proficiency:** Successfully performed host discovery, port scanning, and service enumeration using native CLI utilities (`ping`, `nc`, `nmap`).
  
* **Lab Security:** Enforced privacy best practices by isolating test targets and abstracting network configurations.

---

## 🔐 Security & Ethical Issue
   This laboratory is completely for educational purpose only.

   No target-specific credentials, confidential information, patient records, private infrastructure details, or sensitive assessment evidence are included in this repository.

---

## 🔭 Tools and Resources
  1. To install 7-Zip: https://7-zip.org/download.html
  2. To install VirtualBox Machine: https://virtualbox.org/wiki/Downloads
  3. To install Kali Linux: https://kali.org/get-kali

---

## 👤 Author
   Neha
   
   Cybersecurity Intern B083


   LinkedIn: https://www.linkedin.com/in/neha-d-846342-nd

---

  ## 📌 Project Information

  Program Name: Cybersecurity at Networkwalks | Week: 01 | Project: Cybersecurity and Pentesting Lab Setup | Repository: GitHub
