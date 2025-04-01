# Common Network Attack Scenarios

This document outlines common network attack scenarios, their characteristics, and potential indicators. Understanding these scenarios can help in identifying and mitigating threats effectively.

---

## 1. **TCP SYN Flood Attack**

### Description:
A TCP SYN flood attack is a type of Denial-of-Service (DoS) attack where an attacker sends a large number of SYN packets to a target server. The server allocates resources for each connection request, which can overwhelm its capacity.

### Indicators:
- High volume of TCP packets with the SYN flag set and the ACK flag unset.
- Unusually high resource usage on the target server.

### Mitigation:
- Use SYN cookies to validate connection requests.
- Implement rate limiting to restrict the number of SYN packets from a single source.

---

## 2. **Port Scanning**

### Description:
Port scanning is a reconnaissance technique used by attackers to identify open ports and services on a target system. Common types include SYN scans and UDP scans.

### Indicators:
- Multiple connection attempts to different ports in a short time frame.
- Unusual traffic patterns on non-standard ports.

### Mitigation:
- Use firewalls to block unauthorized scanning attempts.
- Monitor and log unusual port activity.

---

## 3. **ARP Spoofing**

### Description:
ARP spoofing involves sending fake ARP messages to associate the attacker’s MAC address with the IP address of another device. This allows the attacker to intercept or modify network traffic.

### Indicators:
- High volume of ARP reply packets.
- Duplicate IP addresses detected on the network.

### Mitigation:
- Enable dynamic ARP inspection (DAI) on network switches.
- Use static ARP entries for critical devices.

---

## 4. **DNS Tunneling**

### Description:
DNS tunneling is a technique where attackers encode data within DNS queries to exfiltrate information or establish covert communication channels.

### Indicators:
- DNS queries with unusually long or suspicious domain names.
- High volume of DNS traffic from a single source.

### Mitigation:
- Monitor DNS traffic for anomalies.
- Use DNS filtering to block suspicious domains.

---

## 5. **HTTP Flood Attack**

### Description:
An HTTP flood is a Distributed Denial-of-Service (DDoS) attack where attackers send a large number of HTTP requests to overwhelm a web server.

### Indicators:
- High volume of HTTP requests from a single source or multiple sources.
- Increased server response times or crashes.

### Mitigation:
- Use a web application firewall (WAF) to filter malicious traffic.
- Implement rate limiting for HTTP requests.

---

## 6. **ICMP Flood Attack**

### Description:
An ICMP flood attack involves sending a large number of ICMP Echo Request (ping) packets to a target, overwhelming its resources.

### Indicators:
- High volume of ICMP Echo Request packets (type 8).
- Network latency or downtime.

### Mitigation:
- Block ICMP traffic from untrusted sources.
- Use rate limiting for ICMP packets.

---

## 7. **Brute-Force Attack**

### Description:
A brute-force attack involves systematically trying different combinations of usernames and passwords to gain unauthorized access to a system.

### Indicators:
- Multiple failed login attempts in a short time frame.
- Unusual login activity from unknown IP addresses.

### Mitigation:
- Implement account lockout policies after a certain number of failed attempts.
- Use multi-factor authentication (MFA) for added security.

---

## 8. **Man-in-the-Middle (MITM) Attack**

### Description:
In a MITM attack, an attacker intercepts communication between two parties to eavesdrop, modify, or steal data.

### Indicators:
- Unexpected SSL/TLS certificate warnings.
- Unusual ARP or DNS activity.

### Mitigation:
- Use encrypted communication protocols like HTTPS and VPNs.
- Enable certificate pinning to detect fake certificates.

---

## 9. **SQL Injection**

### Description:
SQL injection is a web application attack where malicious SQL queries are injected into input fields to manipulate the database.

### Indicators:
- Unusual database errors in application logs.
- Unexpected changes to database records.

### Mitigation:
- Use parameterized queries or prepared statements.
- Validate and sanitize user inputs.

---

## 10. **Phishing Attack**

### Description:
Phishing attacks involve tricking users into revealing sensitive information, such as login credentials or financial details, through fraudulent emails or websites.

### Indicators:
- Emails with suspicious links or attachments.
- Reports of unauthorized access to user accounts.

### Mitigation:
- Educate users about phishing tactics.
- Use email filtering to block malicious emails.

---

