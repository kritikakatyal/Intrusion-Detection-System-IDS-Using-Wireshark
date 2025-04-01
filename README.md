# Intrusion Detection System (IDS) Using Wireshark

## Project Overview
This project focuses on setting up **Wireshark** as an **Intrusion Detection System (IDS)** to monitor network traffic and detect potential security threats. By utilizing Wireshark’s powerful filtering and packet analysis capabilities, we can identify suspicious activity, detect network anomalies, and respond to security incidents effectively.

## Objectives
- Understand the role of **Intrusion Detection Systems (IDS)** in cybersecurity.
- Learn how to configure **Wireshark filters** to detect **various attack patterns**.
- Analyze network packets to identify potential **security threats**.
- Document **findings and best practices** for network security monitoring.

## 🛠️ Tools & Requirements
### **Operating System:**
- Linux (Ubuntu, Kali Linux, ParrotOS)
- Windows 10/11
- macOS

### **Required Tools:**
- **Wireshark** – A network protocol analyzer for inspecting and capturing network traffic.
- **Npcap (for Windows users)** – A packet capture driver for Windows.
- **tcpdump (Optional)** – CLI-based network packet analyzer.
- **Test Network Environment** – A virtual lab setup or a test machine to simulate attacks.

## Setup Guide
### **1️⃣ Install Wireshark**
#### **For Linux:**
```bash
sudo apt update && sudo apt install wireshark -y
```

#### **For Windows:**
- Download Wireshark from [Wireshark’s official website](https://www.wireshark.org/).
- Install **Npcap** when prompted during installation.

#### **For macOS:**
```bash
brew install wireshark
```

### **2️⃣ Capture Network Traffic**
1. Open **Wireshark**.
2. Select the network interface to monitor (e.g., `eth0`, `wlan0`).
3. Start the packet capture.
4. Apply filters to analyze specific network behaviors.

## 🔍 Detecting Security Threats Using Wireshark Filters
Below are some **essential Wireshark filters** for identifying different types of security threats:

### **Unusual Traffic Patterns & Port Scanning**
- **Detect TCP SYN scans (Nmap scan):**  
  ```plaintext
  tcp.flags.syn == 1 && tcp.flags.ack == 0
  ```
- **Detect Null Scans (stealth scanning attempt):**  
  ```plaintext
  tcp.flags == 0x000
  ```
- **Detect FIN Scans:**  
  ```plaintext
  tcp.flags.fin == 1 && tcp.flags.ack == 0
  ```

### **Suspicious Data Transfers & Malware Communications**
- **Detect Unencrypted Passwords (HTTP Basic Auth):**  
  ```plaintext
  http.authbasic
  ```
- **Detect Large Data Transfers (possible exfiltration):**  
  ```plaintext
  frame.len > 1000
  ```
- **Detect DNS Tunneling (excessive DNS queries):**  
  ```plaintext
  dns.qry.name contains "example.com"
  ```

### **Possible Intrusions & Attacks**
- **Detect ARP Spoofing:**  
  ```plaintext
  arp.duplicate-address-detected
  ```
- **Detect DDoS Attack (Multiple SYN Requests from One Source):**  
  ```plaintext
  tcp.flags.syn == 1 && tcp.analysis.initial_rtt == 0
  ```
- **Detect Unauthorized Access Attempts:**  
  ```plaintext
  ip.addr == <suspicious IP>
  ```

## Analyzing Results
Once Wireshark captures and filters the packets:
1. **Look for patterns** indicating abnormal behavior.
2. **Investigate flagged packets** for potential threats.
3. **Save logs** and generate reports for further analysis.

## Best Practices for Effective IDS Monitoring
- Keep **Wireshark updated** to detect new attack signatures.
- Combine **Wireshark with SIEM tools** for enhanced threat detection.
- Regularly update **firewall and IDS rules** to block evolving threats.
- Use **encrypted protocols (HTTPS, SSH, VPNs)** to prevent data interception.
- Monitor **unusual network activity** and correlate logs with threat intelligence.

## Documentation & References
- **Installation Guide**: [installation.md]
- **Wireshark Filters**: [wireshark_filters.md]
- **Attack Scenarios**: [attack_scenarios.md]
- **Results Analysis**: [results_analysis.md]
- **Troubleshooting Guide**: [troubleshooting.md]
- **Compliance & Best Practices**: [best_practices.md]

## Disclaimer
This project is intended for **educational and ethical security research purposes** only. Unauthorized network monitoring or intrusion detection without proper permission is **illegal**. Always obtain explicit consent before analyzing network traffic.

## 📂 Repository
Clone this repository to get started:
```bash
git clone https://github.com/yourusername/IDS-Wireshark.git
cd IDS-Wireshark
```



