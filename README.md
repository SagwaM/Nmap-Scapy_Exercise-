Ethical Hacking Lab – Nmap & Scapy Exercises

This repository contains my reproduced labs from the Cisco Ethical Hacker course.
The goal was to practice network scanning, host discovery, OS fingerprinting, service enumeration, packet sniffing, and basic protocol analysis using Nmap and Scapy.

🔍 Nmap Exercises
1. Host Discovery
nmap -sn 10.6.6.0/24

2. OS Detection
sudo nmap -O 10.6.6.23

3. Service & Aggressive Scan
nmap -p21 -sV -A -T4 10.6.6.23

4. SMB Port Check
nmap -A p139, p445 10.6.6.23

5. SMB Enumeration Script
nmap --script smb-enum-shares.nse -p445 10.6.6.23

6. SMB Share Access
smbclient //10.6.6.23/print$ -N
# type 'exit' to close

📡 Network Information Checks
ifconfig
ip route
cat /etc/resolv.conf

🧪 Capturing Traffic with tcpdump
sudo tcpdump -i eth0 -s 0 -w ladies.pcap
# Ctrl + C to stop
ls ladies.pcap

Open the capture in Wireshark:
wireshark

🐍 Scapy Exercises
1. Start Scapy as Root
sudo su
scapy

2. Basic Sniffing
sniff()


Open a new terminal and run:

ping google.com


Stop both with Ctrl + C.

3. Save Sniff Output
paro = _
paro.summary()

4. Sniff on Internal Interface
sniff(iface="br-internal")


Trigger traffic:

ping 10.6.6.1/24
Open browser → visit 10.6.6.23


Stop sniffing: Ctrl + C

paro2 = _
paro2.summary()

5. ICMP Filtered Sniff
sniff(iface="br-internal", filter="icmp", count=5)


Trigger traffic:

ping 10.6.6.23


Stop:

Ctrl + C on ping window

Ctrl + C on Scapy window

Save results:

paro3 = _
paro3.summary()
paro3[3]
