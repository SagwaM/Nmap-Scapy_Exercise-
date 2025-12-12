Ethical Hacking Lab – Nmap & Scapy Exercises

This repository contains the reproduced practical labs from the Cisco Ethical Hacker training (ParoCyber).
The objective of this assignment was to practice network scanning, enumeration, packet capturing, packet sniffing, and protocol analysis using Nmap, tcpdump, Wireshark, and Scapy.

🔹 1. Nmap Labs
1.1 Host Discovery
nmap -sn 10.6.6.0/24

1.2 OS Detection
sudo nmap -O 10.6.6.23

1.3 Service Detection + Aggressive Scan
nmap -p21 -sV -A -T4 10.6.6.23

1.4 SMB Port Scan
nmap -A p139, p445 10.6.6.23

1.5 SMB Enumeration Script
nmap --script smb-enum-shares.nse -p445 10.6.6.23

1.6 Accessing SMB Share
smbclient //10.6.6.23/print$ -N
# type: exit

🔹 2. Network Information Commands
ifconfig
ip route
cat /etc/resolv.conf

🔹 3. Traffic Capture (tcpdump)
sudo tcpdump -i eth0 -s 0 -w ladies.pcap
# Stop with CTRL + C


Verify the capture file:

ls ladies.pcap


Open in Wireshark:

wireshark

🔹 4. Scapy Labs
4.1 Start Scapy as Root
sudo su
scapy

4.2 Basic Sniffing

In Scapy:

sniff()


In a new terminal, generate traffic:

ping google.com


Stop both terminals: CTRL + C.

Save results:

paro = _
paro.summary()

4.3 Sniff on Internal Interface
sniff(iface="br-internal")


Generate traffic:

Ping:

ping 10.6.6.1/24


Open browser and visit:

10.6.6.23


Stop with CTRL + C.

Save results:

paro2 = _
paro2.summary()

4.4 Filtered ICMP Sniff
sniff(iface="br-internal", filter="icmp", count=5)


Generate ICMP packets:

ping 10.6.6.23


Stop both terminals (Ctrl+C).
Save results:

paro3 = _
paro3.summary()
paro3[3]

🔹 5. Key Learning Outcomes

Through these labs, I practiced and reinforced:

Host discovery and active network scanning

OS fingerprinting and service enumeration

SMB scanning and share enumeration

Packet capturing with tcpdump

Protocol analysis in Wireshark

Sniffing and analyzing packets using Scapy

Understanding ICMP, TCP, ARP, and HTTP traffic patterns

The difference between automated discovery (Nmap) and manual packet work (Scapy)

🔹 6. Tools Used

Nmap

Scapy

tcpdump

Wireshark

Kali Linux / Lab Environment

🔹 7. Author

Maria Sagwa
Cisco Ethical Hacker Student – ParoCyber
GitHub: https://github.com/SagwaM/Nmap-Scapy_Exercise-
Medium: your profile link
