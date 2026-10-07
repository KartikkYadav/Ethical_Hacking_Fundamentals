# Networking

A practical collection of notes covering **network fundamentals, reconnaissance, scanning, packet analysis, Nmap, TCP/TLS handshakes, firewall and IDS/IPS considerations, VPN/Tor, and penetration-testing lab setup**.

This section is part of the [Ethical_Hacking_Fundamentals](../) repository and is designed as a hands-on reference for learning networking concepts and applying them during authorized security assessments.

---

## Overview

Strong networking knowledge is essential for penetration testing and cybersecurity. This section starts with Kali Linux and network fundamentals, then progresses into reconnaissance, host discovery, port scanning, Nmap techniques, packet behavior, and network security controls.

The material covers:

**Kali Setup → Network Reconnaissance → Network Pentesting → ICMP/ARP Tools → Packet Crafting → Nmap → TCP/TLS → Port Scanning → Firewall/IDS/IPS → Proxy, VPN & Tor**

---

## Contents

### 00. NVIDIA Drivers Installation in Kali

**[NVIDIA Drivers Installation](./0.nvidia_Drivers_Installation_In_Kali.md)**

System-setup notes for installing NVIDIA drivers on Kali Linux.

Topics include:

- GPU identification
- Nouveau configuration
- Kernel headers and build dependencies
- NVIDIA driver installation
- DKMS
- Driver verification with `nvidia-smi`
- NVIDIA GPU and CUDA-related setup notes

This is a system-environment setup reference used to prepare a Kali workstation.

---

### 01. Kali Linux Setup

**[Kali Linux Setup](./01.Kali_Linux_Setup.md)**

Covers practical Kali Linux environment preparation.

Topics include:

- APT repository configuration
- Package updates and upgrades
- Basic utilities
- Kali metapackages
- Screen
- Kernel headers
- Wireless adapter setup
- Realtek RTL8812AU driver installation
- NVIDIA GPU and CUDA toolkit setup
- SSH service configuration

---

### 02. Network Reconnaissance & Scanning

**[Network Reconnaissance & Scanning](./02.%20Network-Reconnaissance-Scanning.md)**

Introduces network reconnaissance and scanning methodology.

### Key Areas

- Passive reconnaissance
- Active reconnaissance
- Host discovery
- Port scanning
- Service/version detection
- OS detection
- Banner grabbing
- DNS reconnaissance
- UDP scanning
- Traceroute
- Scan-output management
- High-speed scanning with Masscan
- Firewall-evasion concepts

### Tools Referenced

**Nmap · Masscan · Netcat · Hping3 · Fping · Amap · Tcpdump · Wireshark · ZMap · DNSenum · Dig · Nslookup · Xprobe2**

---

### 03. Network Penetration Testing Labs

**[Network Penetration Testing Labs](./03.Network_Pentest_Labs.md)**

Provides references to practical environments for developing penetration-testing skills.

### Platforms Referenced

- Hack The Box
- OffSec Proving Grounds
- VulnHub
- TryHackMe
- PentesterLab
- PortSwigger Web Security Academy

The notes also include references to vulnerable virtual machines and guidance for isolating lab environments with VirtualBox or VMware.

---

### 04. Network Penetration Testing

**[Network Penetration Testing](./04.Network_Pentesting.md)**

Covers internal and external network penetration testing.

### Internal Testing

Focuses on:

- Internal application servers
- Databases
- Workstations
- Network infrastructure
- Security appliances
- Active Directory / LDAP
- Internal authentication

### External Testing

Focuses on:

- Internet-facing systems
- Firewalls and routers
- Public web servers and APIs
- Email servers
- VPN gateways
- Cloud endpoints
- External IP ranges

### Methodology

**Planning & Scoping → Reconnaissance → Scanning & Enumeration → Exploitation → Post-Exploitation → Reporting**

---

### 05. Ping

**[Ping](./05,Ping.md)**

Introduces the Ping utility and ICMP-based host reachability testing.

Core concepts include:

- ICMP Echo Request
- ICMP Echo Reply
- Host availability
- Network troubleshooting
- Basic latency measurement

---

### 06. Arping

**[Arping](./06.Arping.md)**

Covers ARP-based host discovery and local-network reachability testing.

Useful areas include:

- Local network host discovery
- ARP request/response behavior
- MAC-address identification
- Network troubleshooting

---

### 07. Fping & Hping3

**[Fping & Hping3](./07.Fping_&_Hping.md)**

Covers two flexible network-testing utilities.

### Fping

Useful for:

- Multiple-host probing
- ICMP-based discovery
- Batch host checks
- Network availability testing

### Hping3

The notes cover packet crafting and testing with:

- TCP
- UDP
- ICMP
- Raw IP packets
- TCP flags
- Port scanning
- Traceroute
- Source-IP testing
- Firewall behavior analysis

Because Hping3 can generate custom traffic, use it only in controlled or explicitly authorized environments.

---

### 08. Nping

**[Nping](./08.nping.md)**

Nping is covered as a packet-generation and network-testing utility from the Nmap suite.

Topics include:

- ICMP packets
- TCP packets
- UDP packets
- ARP requests
- TCP flags
- TTL manipulation
- Custom packet data
- UDP port testing
- Echo mode
- Route tracing
- Network troubleshooting and security testing

---

### 09. Nmap & Headers

**[Nmap & Headers](./09.nmap_&_headers.md)**

Provides an extensive reference for **Nmap**, including network-layer concepts and packet handling.

### Nmap Capabilities

- Host discovery
- Port scanning
- Service/version detection
- OS detection
- Nmap Scripting Engine (NSE)
- TCP, UDP, ICMP and IP-based scanning
- Output formats
- Network-layer packet behavior
- Firewall and IDS/IPS testing concepts

The note also discusses how Nmap interacts with IP packets and network-layer behavior.

---

### 10. TCP Three-Way Handshake & TLS

**[TCP Three-Way Handshake](./10.TCP-Three-Way-Handshake.md)**

Explains TCP connection establishment.

### TCP Handshake

**SYN → SYN-ACK → ACK**

The notes cover:

- Initial Sequence Numbers
- Acknowledgment numbers
- Connection establishment
- Reliability
- Sequence synchronization

### TLS Handshake

The same note also introduces the TLS handshake, including:

- Client Hello
- Server Hello
- Certificate verification
- Key exchange
- Session-key generation
- Change Cipher Spec
- Finished messages

---

### 11. Nmap Scanning Workflow

**[Nmap Scanning](./11.Nmap_Scanning.md)**

Provides a structured Nmap workflow:

**Host Discovery → PTR Lookup → Port Scanning → Service Detection → OS Detection → Output Storage**

The note also references:

- ARP-based discovery
- ICMP discovery
- TCP discovery
- UDP discovery
- Nmap version detection
- Normal output
- XML output
- Grepable output

---

### 12. Target Specification in Nmap

**[Target Specification in Nmap](./12.Target-Specification-in-Nmap.md)**

Covers methods for defining Nmap scan targets and selecting specific hosts, ranges, or network assets.

---

### 13. Host Discovery

**[Host Discovery](./13.Host-Discovery.md)**

Focuses on identifying live systems before performing deeper port and service enumeration.

Relevant techniques include:

- ICMP discovery
- TCP discovery
- UDP discovery
- ARP discovery
- Nmap host-discovery options

---

### 14. Port Scanning

**[Port Scanning](./14.Ports_Scanning.md)**

Covers the purpose and behavior of TCP/UDP port scanning.

Main areas include:

- Open, closed, and filtered ports
- TCP scanning
- UDP scanning
- Port ranges
- Service exposure
- Scan interpretation

---

### 15. Port Knocking

**[Port Knocking](./15.Port-Knocking.md)**

Introduces port-knocking concepts and their relationship to service exposure and network access control.

---

### 16. Nmap Port-Scanning Output

**[Nmap Port Scanning Output](./16.Nmap-Port-Scanning-Output.md)**

Covers how to interpret and work with Nmap results and scan output.

---

### 17. Nmap Scan Techniques

**[Nmap Scan Techniques](./17.Nmap-Scan-Techniques.md)**

Provides reference material for different Nmap scan approaches.

---

### 18. Additional Nmap Scanning Techniques

**[Additional Nmap Scanning Techniques](./18.Nmap_Scaning_Tchnique.md)**

Additional notes covering Nmap scanning behavior and techniques.

---

### 19. Nmap Version & OS Detection

**[Nmap Version & OS Detection](./19.Nmap-version-Detection_%26_Os-Detection.md)**

Focuses on identifying:

- Running services
- Service versions
- Operating-system fingerprints
- Information useful for subsequent assessment

---

### 20. Nmap Timing & Performance Options

**[Nmap Timing & Performance Options](./20.Nmap-Timing-and-Performance-Options.md)**

Covers Nmap timing and performance controls used to balance:

- Scan speed
- Reliability
- Network load
- Host responsiveness

---

### 21. Nmap Timing & Performance Options (Additional Note)

**[Nmap Timing & Performance Options - Additional Reference](./20.Nmap-timing_%26_Performance-options.md)**

Additional material covering Nmap timing and performance behavior.

---

### 22. Firewall, IDS/IPS Evasion & Spoofing

**[Firewall, IDS & IPS Evasion](./20.Firewall-IDS-and-IPS-Evasion-and-Spoofing-In-Nmap.md)**

Introduces Nmap features related to testing network security controls, including:

- Packet fragmentation
- Source-port manipulation
- Decoy techniques
- Packet-header manipulation
- Firewall behavior testing
- IDS/IPS considerations

These techniques can affect detection and network traffic and should be used only during authorized testing.

---

### 23. Firewall, IDS/IPS Evasion & Spoofing (Additional Note)

**[Firewall, IDS & IPS Evasion - Additional Reference](./21.Firewall-IDS-and-IPS-Evasion-%26-Spoofing-in-Nmap.md)**

Additional Nmap-focused notes covering firewall, IDS/IPS, and spoofing concepts.

---

### 24. Proxy, VPN & Tor

**[Proxy, VPNs, and Tor](./22.Proxy,%20VPNs,%20and%20TOR.md)**

Introduces proxying, VPNs, and Tor as network-routing and privacy technologies.

The notes are relevant to understanding:

- Traffic routing
- Network intermediaries
- VPN connectivity
- Tor concepts
- Proxy-based traffic flows

---

## Core Networking Concepts

| Domain | Focus |
|---|---|
| Network Fundamentals | Packets, protocols, addressing, connectivity |
| Reconnaissance | Passive and active information gathering |
| Host Discovery | Finding live systems |
| Port Scanning | Identifying exposed network services |
| Service Enumeration | Determining protocols and versions |
| Packet Crafting | Custom TCP, UDP, ICMP, ARP traffic |
| Nmap | Network discovery and security auditing |
| TCP | Connection establishment and reliable transport |
| TLS | Secure connection establishment and key negotiation |
| DNS | Host and domain resolution |
| Firewall Testing | Understanding packet filtering behavior |
| IDS/IPS | Detection and prevention considerations |
| VPN / Proxy / Tor | Traffic routing and network intermediaries |

---

## Common Tools

The networking notes reference:

**Nmap · Nping · Hping3 · Fping · Arping · Netcat · Masscan · Amap · Tcpdump · Wireshark · ZMap · DNSenum · Dig · Nslookup · Xprobe2**

Other technologies covered include:

**TCP · UDP · ICMP · ARP · DNS · TLS · VPN · Proxy · Tor**

---

## Practical Network Assessment Workflow

A structured workflow represented across these notes is:

### 1. Define Scope

Identify authorized IP ranges, hosts, networks, and exclusions.

### 2. Reconnaissance

Gather passive information and establish a basic understanding of the environment.

### 3. Host Discovery

Identify responsive systems using appropriate discovery methods.

### 4. Port Scanning

Identify exposed TCP and UDP services.

### 5. Service Enumeration

Determine service names, versions, banners, and relevant protocol behavior.

### 6. Network Analysis

Use packet analysis and protocol knowledge to understand traffic and system behavior.

### 7. Vulnerability Assessment

Correlate discovered services and configurations with relevant weaknesses.

### 8. Validation

Safely verify applicable findings within the engagement scope.

### 9. Documentation

Record scan results, evidence, affected assets, risk, and remediation guidance.

---

## Nmap Study Progression

A useful progression through this section is:

**Nmap Basics → Host Discovery → Target Specification → Port Scanning → Scan Techniques → Service/Version Detection → OS Detection → Timing & Performance → Output Analysis → Firewall/IDS/IPS Testing**

Then combine Nmap knowledge with:

**Arping · Fping · Hping3 · Nping · Netcat · Wireshark**

to strengthen practical network-analysis skills.

---

## Lab Environment

For hands-on practice, use isolated environments such as:

- Hack The Box
- Proving Grounds
- VulnHub
- TryHackMe
- PentesterLab
- PortSwigger Web Security Academy
- Intentionally vulnerable virtual machines

For local labs, use isolated VirtualBox or VMware networking such as **Host-Only** or **Internal Network** where appropriate.

---

## Reporting Checklist

When documenting network-testing activities, capture:

| Item | Example |
|---|---|
| Target | IP address, hostname, network range |
| Discovery | Live-host result |
| Port | TCP/UDP port |
| Service | Detected service |
| Version | Service/version information |
| Evidence | Scan output, packets, screenshots |
| Finding | Exposure or security weakness |
| Impact | Security consequence |
| Recommendation | Hardening or remediation |
| Retest | Verification after remediation |

---

## Responsible Use

This section is intended for:

**Cybersecurity Education · CTFs · Security Labs · Authorized Penetration Testing · Network Security Research**

Some notes contain packet-crafting, spoofing, brute-force, firewall/IDS/IPS testing, and traffic-generation techniques. Use them only on systems and networks you own or have explicit authorization to assess.

Avoid high-volume scanning, stress testing, or evasion techniques against production infrastructure without explicit approval and appropriate safeguards.

---

## Related Repository

This section is part of:

**[Ethical_Hacking_Fundamentals](../)**

Related areas include:

- [Active Directory](../AD)
- [Enumeration Techniques for Penetration Testing](../Enumeration%20Techniques%20for%20Penetration%20Testing)
- [File Transfer](../File_Transfer)
- [Information Security](../Information_Security)
- Tunneling & Port Forwarding
- Privilege Escalation
- Wireless Pentesting

---

## Author

**Kartik Yadav**

Cybersecurity | Networking | Penetration Testing

GitHub: [KartikkYadav](https://github.com/KartikkYadav)

---

⭐ **A practical networking reference for understanding reconnaissance, scanning, Nmap, packet behavior, and network security testing.**
