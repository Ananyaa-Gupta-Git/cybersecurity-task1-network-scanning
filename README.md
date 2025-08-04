# cybersecurity-task1-network-scanning
# Cybersecurity Task 1: Network Port Scanning

## Objective
Learn to discover open ports on devices in local network to understand network exposure and security risks.

## Tools Used
- **Nmap**: Network discovery and security auditing tool
- **Command Line**: For executing scanning commands
- **Wireshark** (Optional): For packet analysis

## Task Overview
This task involves scanning the local network to identify:
- Active devices on the network
- Open ports on discovered devices
- Services running on those ports
- Potential security risks

## Network Information
- **Local IP Range**: 192.168.1.0/24
- **My IP Address**: 192.168.1.54
- **Gateway**: 192.168.1.1

## Commands Used

### Basic Network Discovery
```bash
# Discover active hosts on network
nmap -sn 192.168.1.0/24

# TCP SYN scan for open ports
nmap -sS 192.168.1.0/24

# Detailed scan with service detection
nmap -sS -sV 192.168.1.0/24
```

## Scan Results Summary

### Active Devices Found
| IP Address | MAC Address | Device Type | Status |
|------------|-------------|-------------|---------|
| 192.168.1.1 | 6C:EB:B6:91:15:3B | Huawei Router | Up |
| 192.168.1.3 | 30:07:4D:52:08:21 | Samsung Device | Up |
| 192.168.1.4 | 4A:DD:6A:BA:80:CE | Unknown Device | Up |
| 192.168.1.11 | D2:74:A3:03:7C:97 | Unknown Device | Up |
| 192.168.1.54 | (This Computer) | Windows PC | Up |

### Open Ports Analysis
| Device IP | Port | Service | Protocol | Risk Level |
|-----------|------|---------|----------|------------|
| 192.168.1.1 | 53 | DNS | TCP | Low |
| 192.168.1.1 | 80 | HTTP | TCP | Medium |
| 192.168.1.1 | 443 | HTTPS | TCP | Low |
| 192.168.1.54 | 135 | RPC | TCP | Medium |
| 192.168.1.54 | 139 | NetBIOS | TCP | High |
| 192.168.1.54 | 445 | SMB | TCP | Critical |
| 192.168.1.54 | 3306 | MySQL | TCP | High |

## Security Findings

### Common Open Ports Discovered
- **Port 22 (SSH)**: Secure shell access - ensure strong passwords
- **Port 80 (HTTP)**: Web server - check if intentional
- **Port 443 (HTTPS)**: Secure web server - generally safe
- **Port 53 (DNS)**: Domain name resolution - normal for routers

### Potential Security Risks
1. **Unnecessary open ports**: Services running that may not be needed
2. **Default credentials**: Devices using factory default passwords
3. **Unencrypted services**: HTTP instead of HTTPS
4. **Outdated services**: Old versions with known vulnerabilities

### Recommendations
1. Close unnecessary ports using firewall rules
2. Change default passwords on all devices
3. Enable encryption where possible
4. Regularly update device firmware
5. Monitor network for unauthorized devices

## Files in This Repository
- `README.md`: This documentation
- `scan_results.txt`: Raw Nmap output
- `network_analysis.md`: Detailed analysis
- `screenshots/`: Screenshots of scan process

## Key Concepts Learned
- **Port Scanning**: Technique to discover open ports and services
- **TCP SYN Scan**: Stealthy scanning method using SYN packets
- **Network Reconnaissance**: Information gathering about network infrastructure
- **Security Assessment**: Identifying vulnerabilities and risks

## Interview Questions Preparation

### 1. What is an open port?
An open port is a network port on a device that is actively listening for incoming connections. It indicates a service or application is running and accepting network traffic on that specific port number.

### 2. How does Nmap perform a TCP SYN scan?
Nmap sends TCP SYN packets to target ports. If the port is open, the target responds with SYN-ACK. Nmap then sends RST to close the connection without completing the handshake, making it stealthier than full TCP connect scans.

### 3. What risks are associated with open ports?
- Unauthorized access to services
- Potential entry points for attackers
- Information disclosure about running services
- Exploitation of vulnerable services
- DDoS attack vectors

### 4. Difference between TCP and UDP scanning?
- **TCP scanning**: Uses connection-oriented protocol, more reliable, easier to detect open ports
- **UDP scanning**: Uses connectionless protocol, harder to determine if ports are open, slower scanning process

### 5. How can open ports be secured?
- Close unnecessary ports using firewalls
- Use strong authentication
- Enable encryption (TLS/SSL)
- Regular security updates
- Access control and IP restrictions
- Network segmentation

### 6. What is a firewall's role regarding ports?
Firewalls control traffic by allowing or blocking specific ports based on security rules. They act as barriers between trusted internal networks and untrusted external networks, filtering packets based on port numbers, protocols, and IP addresses.

### 7. What is a port scan and why do attackers perform it?
Port scanning is the process of probing network ports to discover open services. Attackers use it for reconnaissance to:
- Identify potential attack vectors
- Discover running services and versions
- Map network infrastructure
- Find vulnerable or misconfigured services

### 8. How does Wireshark complement port scanning?
Wireshark captures and analyzes network packets in real-time, allowing you to:
- See the actual network traffic generated by Nmap
- Understand scanning techniques at packet level
- Detect scanning attempts on your network
- Analyze responses from target systems

## Conclusion
This task provided hands-on experience with network reconnaissance using Nmap. Understanding how to discover and analyze open ports is crucial for both offensive security (penetration testing) and defensive security (network hardening).

---
**Author**: Ananyaa Gupta  
**Date**: 04/08/2025
**Course**: Cybersecurity Internship - Task 1
