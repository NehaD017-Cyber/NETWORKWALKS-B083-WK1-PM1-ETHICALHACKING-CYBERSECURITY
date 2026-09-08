# NETWORKWALKS-B083-WK1-PM1-ETHICALHACKING-CYBERSECURITY
Hands-on Cybersecurity lab using Virtual box and Kali Linux to practice ethical hacking and penetration testing.

# 🔒 Cybersecurity Lab Environment Setup

### Building an isolated virtual lab for penetration testing and ethical hacking practice

![Cybersecurity](https://img.shields.io/badge/Skill-Cybersecurity-red?style=for-the-badge)
![VirtualBox](https://img.shields.io/badge/Ver-VirtualBox_v7.2-blue?style=for-the-badge)
![Kali Linux](https://img.shields.io/badge/Kali_Linux-v2026.2-orange?style=for-the-badge&logo=kalilinux&logoColor=white)

![Linux](https://img.shields.io/badge/Skill-Linux-red?style=for-the-badge)
![Network](https://img.shields.io/badge/Network-10.0.0.0%2F24-teal?style=for-the-badge)
![Penetration Testing](https://img.shields.io/badge/Penetration_Testing-red?style=for-the-badge&logo=kalilinux&logoColor=white)

![Virtualization](https://img.shields.io/badge/Skill-Virtualization-red?style=for-the-badge)
![GitHub](https://img.shields.io/badge/GitHub-black?style=for-the-badge&logo=github&logoColor=white)
![NetworkWalks](https://img.shields.io/badge/NetworkWalks-grey?style=for-the-badge)

![Ethical Hacking](https://img.shields.io/badge/Ethical_Hacking-orange?style=for-the-badge&logo=kalilinux&logoColor=white)
![NEHA](https://img.shields.io/badge/NEHA-Certification-red?style=for-the-badge)

![Nmap](https://img.shields.io/badge/Nmap-blue?style=for-the-badge)   

Isolated virtual lab environment built with VirtualBox and Kali Linux for cybersecurity testing, penetration testing, and ethical hacking practice.

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

4. **Deploy Kali Linux**

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


7. **Create a Clean VM Snapshot**

After completing the initial network configuration and verification, a baseline VirtualBox snapshot was created.

Example snapshot name:
```bash
Clean Baseline - Post Network Setup
```
The snapshot captures the fully configured state of the laboratory environment.

If a future exercise changes system files, breaks networking, or degrades the VM state, the machine can be restored immediately to this clean baseline.

## 🧪 Lab Tests

| ✅ Test | 📃 Command | 🎯 Expected Result |
| :--- | :--- | :--- |
| 🌐 Check IP address | `ip a` | Correct Kali IP displayed |
| 📡 Test gateway | `ping 10.0.0.1` | Successful replies |
| 🌍 Test Internet connectivity | `ping 8.8.8.8` | Successful replies |
| 🔎 Test DNS resolution | `nslookup networkwalks.com` | Domain resolves |
| 🧰 Verify Nmap | `nmap --version` | Nmap version displayed |
| 🔄 Verify snapshot | Restore snapshot and run `ip a` | Baseline configuration restored |

**Example Results:**

IP Address:
10.0.0.2/24

Gateway:
10.0.0.1

DNS:
8.8.8.8

## 🐞 One Problems Encountered & Solved

**Problem1:** Do we have to enable IPv6 while attacking the Virtual Boc to NAT Network?

**Solution:** NO, we don't have to enable IPv6, only enable IPv4 and check DHCP.


**Problem2:** How to take screenshot in Kali Linux?

**Solution:** Open the screenshot file from applications in Kali Linux, select the region or full window, click OK and get the                     screenshot in the folder.


**Problem3:** How to bring the screenshot in your PC file explorer?

**Solution:** Open the snapdrop.net in the Firefox drag the screenshot from Kali Linux open folder to the upload files option, after               uploading it click on the share button and get the screenshot by the link or email.

## 📝 What I Learned

- **Virtual Machine Networking:**
  
  I learned that using NAT Network in VM will help the machines in the lab communicate safely.

- **Static IP configuration:**
  
  I learned how to configure IP addresses, DNS Connectivity and Gateways.

- **Screenshots in Virtual Machine:**
    
  I was stuck for too long in this, but now I know how to take screenshots in VM.

- **Snapshots:**
  
  Saved a baseline state right after setting up Kali so I can reset the VM anytime.

- **Documentation:**
  
  I learned how to do the documentation of my projects, tasks and set the environment of the lab for future tasks.

## 🔐 Security & Ethical Issue
   This laboratory is completely for educational purpose only.

## 🔭 Tools and Resources
  1. To install 7-Zip: https://7-zip.org/download.html
  2. To install VirtualBox Machine: https://virtualbox.org/wiki/Downloads
  3. To install Kali Linux: https://kali.org/get-kali

## 👤 Author
   Neha
   
   Cybersecurity Intern B083


   LinkedIn: https://www.linkedin.com/in/neha-d-846342-nd

  ## 📌 Project Information

  Program Name: Cybersecurity at Networkwalks | Week: 01 | Project: Cybersecurity and Pentesting Lab Setup | Repository: GitHub
