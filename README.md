# CYBER-SECURITY-INTERNSHIP
Task 1 Report: Local Network Port Scan
1. Objective
The objective of this task was to scan the local network to discover open ports on devices, understand network exposure, and identify potential security risks associated with the open ports.
2. Tools Used
Nmap — Network scanning tool to perform TCP SYN scan.

Wireshark (optional) — Packet capture and analysis tool.


3. Environment
Operating System: Kali Linux (running in bridged mode)

Network Interface: eth0

Local IP: 192.168.67.195/24

Network Range Scanned: 192.168.67.0/24


4. Methodology
Identified the local network IP range using ip a command.

Ran the Nmap TCP SYN scan with the command:
nmap -sS 192.168.67.0/24 -oN local-scan.txt

Captured network packets during the scan using Wireshark on interface eth0.

Analyzed open ports and services found.

Researched common services running on those ports and potential security risks.


5. Scan Results
Total IPs scanned: 256 (192.168.67.0 to 192.168.67.255)

Hosts up: 1 (the scanning host itself at 192.168.67.195)

Open ports found: None on the scanning host.

Nmap scan report for 192.168.67.195
Host is up (0.0000030s latency).
All 1000 scanned ports on 192.168.67.195 are closed.


No other hosts responded to the scan on this subnet.

Wireshark capture showed outgoing SYN packets to scanned IPs, with RST responses indicating closed ports.


6. Analysis
The scan host (192.168.67.195) has no open TCP ports in the scanned range.

No other devices on the network responded, likely due to:

Network client isolation or firewall restrictions.

Other devices may have host-based firewalls blocking probes.

Possible network segmentation.

The absence of open ports reduces the immediate risk of remote network attacks on this host.

Common ports typically scanned (22, 80, 443, etc.) were closed, indicating limited network exposure.

7. Common Services and Security Risks (If Ports Were Open)
Port    Service Common Risks
22      SSH     Weak passwords, open root login
80/443  HTTP/HTTPS      Outdated software, unpatched vulnerabilities
445     SMB     Exploitable vulnerabilities (e.g., EternalBlue)
3306    MySQL   Weak authentication, exposed databases



8. Conclusion
This scan demonstrated the use of Nmap to enumerate network hosts and open ports. The network shows limited exposure, with no open ports detected on the scanning host and no visible devices on the subnet.

Further steps could include:

Verifying network isolation or firewall policies.

Scanning during different network conditions.

Expanding to UDP scans or vulnerability scanning tools.
