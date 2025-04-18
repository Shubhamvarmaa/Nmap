# Nmap (Network Mapper) - Complete Guide

## 📌 Introduction
Nmap (Network Mapper) is a powerful open-source tool for network discovery and security auditing. It is widely used for network inventory, monitoring host services, and detecting vulnerabilities. This guide provides a detailed explanation of Nmap commands, options, and best practices.

---

## 🔹 Installation
### 📌 Linux (Debian/Ubuntu)
```bash
sudo apt update && sudo apt install nmap
```

### 📌 Linux (CentOS/RHEL)
```bash
sudo yum install nmap
```

### 📌 macOS (Using Homebrew)
```bash
brew install nmap
```

### 📌 Windows
Download from [Nmap Official Site](https://nmap.org/download.html) and install it.

---

## 🔹 Basic Nmap Commands

### 📌 Scan a Single Host
Scans a specific target to check for open ports and running services.
```bash
nmap <target>
```
Example:
```bash
nmap 192.168.1.1
```

### 📌 Scan Multiple Hosts
Scans multiple specified hosts at once.
```bash
nmap 192.168.1.1 192.168.1.2 192.168.1.3
```

### 📌 Scan a Range of IPs
Scans a range of IP addresses within a network.
```bash
nmap 192.168.1.1-100
```

### 📌 Scan an Entire Subnet
Scans all devices within a subnet using CIDR notation.
```bash
nmap 192.168.1.0/24
```

### 📌 Scan a Domain Name
Resolves and scans the given domain name.
```bash
nmap example.com
```

### 📌 Scan Random Targets
Scans random hosts across the internet.
```bash
nmap -iR 10
```

---

## 🔹 Advanced Scanning Techniques

### 📌 Scan with Service and Version Detection
Identifies running services and their versions.
```bash
nmap -sV <target>
```

### 📌 Perform a Stealth Scan (SYN Scan)
A stealthy method of scanning that reduces detection chances by not completing TCP handshakes.
```bash
nmap -sS <target>
```

### 📌 Perform a UDP Scan
Scans for open UDP ports instead of TCP.
```bash
nmap -sU <target>
```

### 📌 Perform an Aggressive Scan
Runs multiple detection scripts for OS detection, service detection, and traceroute.
```bash
nmap -A <target>
```

### 📌 Scan for OS Detection
Tries to determine the operating system running on the target.
```bash
nmap -O <target>
```

### 📌 Scan Specific Ports
Allows scanning of specific ports instead of all open ports.
```bash
nmap -p <port> <target>
```
Example:
```bash
nmap -p 22,80,443 192.168.1.1
```

### 📌 Scan All 65535 Ports
Scans every possible port on the target.
```bash
nmap -p- <target>
```

### 📌 Perform a TCP Connect Scan
Used when SYN scan is not possible due to restrictions.
```bash
nmap -sT <target>
```

### 📌 Perform a Idle (Zombie) Scan
Uses an idle host to scan another system stealthily.
```bash
nmap -sI <zombie-host> <target>
```

### 📌 Perform a FIN Scan
Tries to bypass firewalls by sending FIN packets.
```bash
nmap -sF <target>
```

---

## 🔹 Firewall Evasion Techniques

### 📌 Fragmented Packets Scan
Breaks packets into smaller fragments to bypass packet filtering firewalls.
```bash
nmap -f <target>
```

### 📌 Spoof Source IP Address
Changes the source IP address of the scan to avoid detection.
```bash
nmap -S <fake-ip> <target>
```

### 📌 Use Decoys to Hide the Real Source
Generates fake scan sources to obfuscate the attacker's real identity.
```bash
nmap -D RND:10 <target>
```

### 📌 Randomize Scan Order
Prevents scans from being detected as a sequential attack pattern.
```bash
nmap --randomize-hosts <target>
```

### 📌 Set Custom TTL Values
Alters packet TTL values to evade detection.
```bash
nmap --ttl <value> <target>
```

---

## 🔹 Nmap Scripting Engine (NSE)

### 📌 Scan for Vulnerabilities
Runs scripts that check for common vulnerabilities.
```bash
nmap --script=vuln <target>
```

### 📌 Scan for Open Ports and Services
Uses default scripts to identify open ports and services.
```bash
nmap --script=default <target>
```

### 📌 Scan for HTTP Vulnerabilities
Runs security checks related to HTTP servers.
```bash
nmap --script=http-vuln* <target>
```

### 📌 Scan for SSH Brute Force
Attempts to brute-force SSH login credentials.
```bash
nmap --script=ssh-brute -p 22 <target>
```

### 📌 List Available Scripts
Displays a list of all available NSE scripts.
```bash
ls /usr/share/nmap/scripts/
```

---

## 🔹 Master Commands
### 📌 The Ultimate Nmap Command for Complete Scanning
```bash
nmap -sS -sV -A -O -p- --script=vuln <target>
```
This command performs:
- Stealth SYN Scan (`-sS`)
- Service and Version Detection (`-sV`)
- Aggressive Mode (`-A` includes OS detection, version detection, and traceroute)
- OS Detection (`-O`)
- Full Port Scan (`-p-`)
- Vulnerability Scanning (`--script=vuln`)

---

## 🔹 Saving Scan Results
### 📌 Save Output in a Text File
```bash
nmap -oN scan_results.txt <target>
```

### 📌 Save Output in XML Format
```bash
nmap -oX scan_results.xml <target>
```

### 📌 Save Output in Greppable Format
```bash
nmap -oG scan_results.gnmap <target>
```

---

## 📌 Conclusion
Nmap is an essential tool for system administrators and security professionals. With its powerful scanning capabilities and scripting engine, it helps in network reconnaissance, vulnerability assessment, and security hardening.

🔗 **For more information, visit:** [https://nmap.org](https://nmap.org)
