# 🔐 Ethical Hacking Lab – Nmap & Scapy Exercises

A practical cybersecurity lab documenting host discovery, OS detection, service enumeration, SMB scanning, packet capturing, and protocol analysis performed during the Cisco Ethical Hacker Course (ParoCyber).
This project demonstrates foundational skills in network reconnaissance, packet crafting, and traffic analysis.

# 🚀 Lab Objectives

## The goal of this assignment is to:

- Reproduce all Nmap labs covered in class
- Recreate all Scapy exercises
- Capture and analyze traffic using tcpdump & Wireshark
- Document commands, screenshots, and results
- Build a clean, professional cybersecurity repo

# 🛠️ Tools Used

- Nmap – Network scanning & enumeration
- Scapy – Packet crafting & sniffing
- tcpdump – Command-line packet capture
- Wireshark – Deep packet analysis
- Kali Linux – Attack & analysis environment

# 🔍 1. Nmap Labs
## 🌐 1.1 Host Discovery Scan

Used to identify active hosts on the network.

`nmap -sn 10.6.6.0/24`


Purpose: Performs a “ping scan” to find live hosts without port scanning.

## 🖥️ 1.2 OS Detection
`sudo nmap -O 10.6.6.23`

Purpose: Attempts to identify the operating system based on network responses.

## 🔎 1.3 Service Detection + Aggressive Scan
`nmap -p21 -sV -A -T4 10.6.6.23`

Purpose:

- -p21 → scan FTP port
- -sV → detect versions
- -A → OS detection, traceroute, scripts
- -T4 → faster timing template

## 📦 1.4 SMB Port Scan
`nmap -A p139,p445 10.6.6.23`

Purpose: Scans Windows SMB ports used for file sharing & authentication.

## 📂 1.5 SMB Enumeration Script
`nmap --script smb-enum-shares.nse -p445 10.6.6.23`

Purpose: Enumerates SMB shared folders exposed on the target.

## 🔐 1.6 Accessing SMB Share
`smbclient //10.6.6.23/print$ -N`

Purpose: Anonymous access to the SMB share.
Type `exit` to close the SMB shell.

# 🛰️ 2. Network Information Commands

These commands verify interface configuration & routing.

`ifconfig`

`ip route`

`cat /etc/resolv.conf`

Purpose:

- ifconfig → View interface details
- ip route → Check routing table
- resolv.conf → DNS information

# 📡 3. Traffic Capture (tcpdump)

Start capture:

`sudo tcpdump -i eth0 -s 0 -w ladies.pcap`

Stop: CTRL + C.

Verify file:

`ls ladies.pcap`

Open in Wireshark:

`wireshark`

# 🐍 4. Scapy Exercises
## 🧪 4.1 Starting Scapy
`sudo su`

`scapy`

## 📥 4.2 Basic Sniffing

In Scapy:

`sniff()`

Generate traffic:

`ping google.com`

Stop with CTRL + C.

Store results:
`paro = _`

`paro.summary()`

## 🌐 4.3 Sniffing on br-internal Interface
`sniff(iface="br-internal")`

Generate traffic:

`ping 10.6.6.1/24`

And browse:

10.6.6.23

Save:
`paro2 = _`

`paro2.summary()`

## 🎯 4.4 ICMP-Only Sniff
`sniff(iface="br-internal", filter="icmp", count=5)`

Generate ICMP packets:

`ping 10.6.6.23`
Save & inspect:

`paro3 = _`

`paro3.summary()`

`paro3[3]`

# 📘 What I Learned

- How to identify hosts and open ports
- How OS detection works using packet signatures
- Service/version enumeration using Nmap
- SMB enumeration and share discovery
- Capturing packets with tcpdump
- Analyzing ICMP, ARP, HTTP, and TCP behavior
- Using Scapy for custom packet crafting & filtering

# 🧩 Challenges Encountered

- Understanding differences between scan types
- Interpreting OS detection accuracy
- Managing Scapy sniffing sessions
- Filtering the right packets in Wireshark

# 🎯 Why This Matters in Real Cybersecurity

These tools form the foundation of real-world penetration testing:

- Reconnaissance
- Enumeration
- Vulnerability identification
- Traffic analysis
- Incident investigation
- Mastering them is essential for ethical hackers and SOC analysts.

# 📬 Contact

For questions or collaboration:
- 📧 Maria Sagwa
- 🔗 GitHub: [repo](https://github.com/SagwaM/Nmap-Scapy_Exercise-)
- 🔗 Medium: [profile](https://medium.com/@sagwamkaari/reproducing-ethical-hacking-labs-nmap-scapy-16bfec3a0820?postPublishedType=initial)
