🔍 TCP NULL Scan: Technical Concept & Security Analysis

An academic and technical research paper exploring TCP NULL Scan, a stealth port scanning technique used in network security assessment, firewalls evasion, and OS fingerprinting.

📌 Project Overview

This research provides a deep dive into the mechanics of TCP NULL Scanning, operating primarily at the Transport Layer (Layer 4) of the OSI model. It details how stealth scans manipulate TCP flag control headers, exploit differences in TCP/IP stack implementations across operating systems (based on RFC 793 standards), and assist ethical hackers in network reconnaissance.

📑 Table of Contents

Introduction

Technical Description

Targeted OSI Layer

Involved Protocols

Importance & Security Relevance

5.1 Firewall Evasion

5.2 Stealth & Logging Avoidance

5.3 OS Fingerprinting

Ethical & Legal Disclaimer

Conclusion

References

1. Introduction

TCP NULL Scan is a specialized port scanning technique categorized under Stealth Scans. Its primary objective is to determine the state of target host ports (Open, Closed, or Filtered) while minimizing detection risks from traditional Intrusion Detection Systems (IDS) and stateless firewalls.

2. Technical Description

The scanner transmits a modified TCP segment containing no control flags (i.e., SYN, ACK, FIN, RST are all set to 0).

Under normal network protocol standards, a packet without set flags is abnormal. The scanner leverages this non-standard behavior to observe how host operating systems parse and respond according to RFC 793:

[Attacker] --- (TCP Packet with NULL Flags) ---> [Target Host]

Responses:
  - Closed Port : Returns TCP RST (Reset) packet.
  - Open/Filtered Port: Drops packet (No response).


3. Targeted OSI Layer

Layer: Layer 4 — Transport Layer

Function: Responsible for end-to-end communication, port addressing, flow control, and session establishment.

4. Involved Protocols

TCP (Transmission Control Protocol): The primary protocol whose header flags are set to zero.

IP (Internet Protocol): Works at Layer 3 (Network Layer) to route TCP NULL packets from source to destination.

5. Importance & Security Relevance

5.1 Firewall Evasion

Stateless firewalls often filter incoming traffic by blocking initial connection requests (SYN packets). Because a NULL scan carries no SYN flag, it may bypass simple firewall rule-sets undetected.

5.2 Stealth & Logging Avoidance

Since a NULL scan does not complete the standard TCP Three-Way Handshake (SYN -> SYN-ACK -> ACK), applications rarely record these attempts in their connection log files.

5.3 OS Fingerprinting

Different operating systems handle RFC non-compliant packets in distinct ways:

BSD/Linux/Unix: Generally adhere strictly to RFC 793 (RST on closed ports, no response on open ports).

Microsoft Windows: Ignores the RFC standard and sends an RST packet regardless of whether the port is open or closed, allowing remote OS identification.

6. Ethical & Legal Disclaimer

⚠️ IMPORTANT NOTICE:

This project and its contents are intended strictly for educational, research, and authorized defensive testing purposes. Executing port scans against systems or networks without explicit, written permission from the owner is illegal and unethical.

7. Conclusion

While TCP NULL Scanning is a classic stealth technique that exploits protocol specification nuances, modern stateful firewalls and advanced Intrusion Prevention Systems (IPS) can easily detect and drop these anomalous packets. Understanding how NULL scans operate is crucial for configuring robust defense mechanisms and network monitoring rules.

8. References

Postel, J. (1981). RFC 793: Transmission Control Protocol. Internet Engineering Task Force (IETF).

Lyon, G. F. (2009). Nmap Network Scanning: The Official Nmap Project Guide to Network Discovery and Security Scanning. Insecure.Com LLC.

👤 Academic Information

Author: Abdullah Faisal Abdullah Rajeh

Institution: Ibb University

Course: Network Security
