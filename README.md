# Elastic SIEM Home Lab

## What is this?
I built a cybersecurity home lab from scratch to practice real-world SOC analyst skills. The lab simulates an attacker targeting a Windows Server, with all activity monitored by an Elastic SIEM running on Ubuntu. Everything runs on my local machine using VirtualBox.

## Lab Setup
| Machine             | Role     | IP |
| Kali Linux          | Attacker | 192.168.56.102 |
| Windows Server 2022 | Target   | 192.168.56.10 |
| Ubuntu Server 22.04 | SIEM     | 192.168.56.20 |

## Tools Used
- **Elastic Stack** (Elasticsearch + Kibana 8.19.16) — log storage and visualization
- **Winlogbeat** — ships Windows event logs to Elasticsearch
- **Metasploit, Nmap, Hydra** — attack simulation
- **VirtualBox** — virtualization

## What I Did

### Built the Lab
Set up three virtual machines on an isolated network, configured static IPs, and connected them using VirtualBox Host-Only networking.

### Deployed the SIEM
Installed Elasticsearch and Kibana on Ubuntu Server. Configured Winlogbeat on the Windows machine to forward security logs in real time. Verified over 4,700 events were flowing into the SIEM.

### Kibana Discover - 4,700+ Security Events
<img width="975" height="575" alt="image" src="https://github.com/user-attachments/assets/b2454722-3570-4b04-a574-2bbfc280452d" />

### Simulated Attacks
From Kali Linux, I ran:
- Nmap port scans to map the target
- EternalBlue (MS17-010) vulnerability scan
- SMB credential attacks using Metasploit
- Brute force login attempts generating Event ID 4625

### Nmap Scan Results
<img width="1919" height="1194" alt="Screenshot 2026-06-01 161738" src="https://github.com/user-attachments/assets/75b2305d-0af7-477f-bd6a-4a2aa51d54fc" />

### Built Detection Rules
- Installed 1,677 Elastic prebuilt detection rules
- Wrote a custom KQL rule to detect failed login attempts
- Triggered 31 alerts from a simulated brute force attack

### 31 Alerts Fired - Brute Force Detected
<img width="975" height="575" alt="image" src="https://github.com/user-attachments/assets/d577cd23-9aa8-4294-be02-ff0b1c98686f" />

### Built a SOC Dashboard
Created a real-time Kibana dashboard with:
- Security events timeline
- Event type breakdown
- Failed vs successful logins
- Top attacking IPs — caught Kali at 192.168.56.102 with 41 hits

### Real-time SOC Dashboard
<img width="975" height="609" alt="image" src="https://github.com/user-attachments/assets/5619c165-1813-4fa0-85aa-21d6560f972c" />
<img width="975" height="609" alt="image" src="https://github.com/user-attachments/assets/8831aa85-b123-401f-bb63-8ea11bff8596" />

## Results
- 4,700+ security events captured
- 31 alerts fired during brute force simulation
- Successfully identified attacker IP in dashboard

## Skills Practiced
- SIEM deployment and configuration
- Windows event log analysis
- KQL detection rule writing
- Attack simulation
- Security dashboard creation
- Network design and segmentation
