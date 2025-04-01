# Wireshark Filters for Intrusion Detection

Wireshark is a powerful tool for analyzing network traffic. It allows network administrators and security professionals to capture and analyze packets in real-time. Below are some useful filters to detect potential security threats, along with explanations of their purpose and usage.

## Filters

### 1. **TCP SYN Flood Attack**
A TCP SYN flood attack is a type of Denial-of-Service (DoS) attack where an attacker sends a large number of SYN packets to a target server, overwhelming its resources.

**Filter:**
```plaintext
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

**Explanation:**
This filter captures TCP packets with the SYN flag set and the ACK flag unset. These packets are typically used to initiate a connection. A high volume of such packets from a single source or multiple sources may indicate a SYN flood attack.

---

### 2. **Port Scanning**
Port scanning is a technique used by attackers to identify open ports on a target system. There are different types of port scans, such as SYN scans and UDP scans.

- **SYN Scan:**
```plaintext
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

**Explanation:**
This filter identifies SYN packets without an ACK response. These packets are often used in stealthy port scans to detect open ports without completing the TCP handshake.

- **UDP Scan:**
```plaintext
udp
```

**Explanation:**
This filter captures all UDP packets. Attackers use UDP scans to identify open UDP ports. Unusual patterns or a high volume of UDP packets may indicate a scan.

---

### 3. **ARP Spoofing**
ARP spoofing is a technique where an attacker sends fake ARP messages to associate their MAC address with the IP address of another device, enabling them to intercept or modify traffic.

**Filter:**
```plaintext
arp.opcode == 2
```

**Explanation:**
This filter captures ARP reply packets. In a normal network, ARP replies are rare compared to ARP requests. A high number of ARP replies may indicate ARP spoofing or poisoning.

---

### 4. **DNS Tunneling**
DNS tunneling is a method used by attackers to exfiltrate data or establish a covert communication channel by encoding data within DNS queries.

**Filter:**
```plaintext
dns.qry.name
```

**Explanation:**
This filter captures DNS query packets. Unusually long or suspicious domain names in the queries may indicate DNS tunneling activity.

---

### 5. **HTTP Flood**
An HTTP flood is a type of Distributed Denial-of-Service (DDoS) attack where attackers send a large number of HTTP requests to overwhelm a web server.

**Filter:**
```plaintext
http.request
```

**Explanation:**
This filter captures all HTTP request packets. A high volume of HTTP requests from a single source or multiple sources may indicate an HTTP flood attack.

---

### 6. **ICMP Flood**
An ICMP flood is a type of DoS attack where attackers send a large number of ICMP Echo Request (ping) packets to overwhelm a target.

**Filter:**
```plaintext
icmp.type == 8
```

**Explanation:**
This filter captures ICMP Echo Request packets (type 8). A high volume of such packets from a single source may indicate an ICMP flood attack.

---

### 7. **Unusual Traffic on Specific Ports**
Monitoring traffic on specific ports can help identify unusual or unauthorized activity. For example, SSH traffic on port 22.

- **Example for SSH (Port 22):**
```plaintext
tcp.port == 22
```

**Explanation:**
This filter captures all TCP packets on port 22. Unusual patterns, such as a high number of connection attempts, may indicate brute-force attacks or unauthorized access attempts.

---

### 8. **Malicious HTTP Headers**
Attackers often use malicious HTTP headers, such as a suspicious `User-Agent`, to disguise their activities.

**Filter:**
```plaintext
http.user_agent contains "malicious"
```

**Explanation:**
This filter captures HTTP packets where the `User-Agent` header contains the word "malicious". You can customize this filter to detect specific patterns or known malicious headers.

---

