# CYBER-SECURITY-INTERNSHIP
Task 1 Report: Local Network Port Scan
## 1. 🎯 Objective

The objective of this task was to scan the local network to:
- Discover live hosts and open ports.
- Understand the network exposure.
- Identify potential security risks associated with open ports.

---

## 2. 🛠️ Tools Used

- **Nmap** — For performing TCP SYN scans to detect open ports.
- **Wireshark (Optional)** — For capturing and analyzing network packets.

---

## 3. 🖥️ Environment

- **Operating System:** Kali Linux (Bridged Network Mode)
- **Network Interface:** `eth0`
- **Local IP Address:** `192.168.173.195/24`
- **Network Scanned:** `192.168.173.0/24`

---

## 4. 🔍 Methodology

1. Identified local IP and subnet using the `ip a` command.
2. Ran a TCP SYN scan using the command:
   ```bash
   nmap -sS 192.168.173.0/24 -oN local-scan2.txt
3. (Optional) Captured packets using Wireshark on interface eth0.

4. Analyzed Nmap results to identify open ports and services.

5. Reviewed potential security risks associated with those ports.



##  5. 📄 Scan Results
Total IPs scanned: 256 (192.168.173.0 – 192.168.173.255)
Live hosts detected: 4

IP Address	Status	Open Ports	Service	MAC Address	Device Info
192.168.173.95	Host is up	None	—	A8:41:F4:66:5F:BD	AzureWave Technology
192.168.173.126	Host is up	None	—	B8:B1:EA:64:16:B1	Honor Device
192.168.173.227	Host is up	53/tcp	DNS	D2:56:9A:C7:9C:36	Unknown
192.168.173.195	Host is up	None	—	—	Kali (local machine)

##  6. 🔎 Analysis
Port 53 (DNS) is open on 192.168.173.227, which may indicate a running DNS server.

Other hosts had all ports either closed or filtered:

Closed: Host responded with TCP RST.

Filtered: No response, likely due to firewall rules or stealth mode.

Your Kali Linux machine has no open ports, reducing its network exposure.

Wireshark confirmed the sending of SYN packets and observed RST/no-responses, supporting the Nmap findings.

##  7. 🚨 Common Ports and Their Risks
Port	Service	Common Security Risks
22	SSH	Brute-force attacks, weak passwords, open root access
53	DNS	DNS poisoning, amplification attacks
80/443	HTTP/HTTPS	Outdated CMS, unpatched web servers
445	SMB	EternalBlue, remote code execution
3306	MySQL	Exposed databases, weak authentication

##  8. ✅ Conclusion
The scan successfully identified 4 live hosts, including one with an open TCP port (53).

The network appears to be partially exposed, depending on how DNS is configured on the host at 192.168.173.227.

No open ports were found on your scanning machine, which is a good security practice.



