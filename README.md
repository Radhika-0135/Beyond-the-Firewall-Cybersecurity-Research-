# Beyond the Firewall: Post-Breach Attack Lifecycle & Autonomous AI Defenses

This repository contains a technical research blog exploring the post-breach attack lifecycle from an internal penetration-testing perspective.

# Host & Subnet Discovery
sudo netdiscover -r 192.168.1.0/24
sudo arp-scan -l
nmap -sn 192.168.1.0/24

# Service & Port Enumeration
nmap -sV -sC -p 22,80,445,3389 192.168.1.50
ip route

# Active Directory & SMB Enumeration
SharpHound.exe -c All
python3 enum4linux-ng.py -A 192.168.1.50
netexec smb 192.168.1.0/24 -u 'username' -p 'password' --users

# Protocol Weakness & Share Check
sudo python3 Responder.py -I eth0 -w -v
nmap --script smb2-security-mode -p 445 192.168.1.0/24
smbmap -H 192.168.1.50

## Key Topics Covered:
* **Internal Reconnaissance & Discovery:** Host discovery, port scanning, and network mapping.
* **Enumeration & Privilege Escalation:** Active Directory enumeration, extracting user lists, and exploiting protocol weaknesses.
* **Lateral Movement & Pivoting:** Moving across internal network segments and handling credentials.
* **AI-Driven Defenses & Zero Trust:** Deploying autonomous anomaly response, content verification, and zero trust controls to prevent compromise.
