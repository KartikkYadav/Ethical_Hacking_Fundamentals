# Tor & Proxy

A practical collection of notes covering **proxy servers, VPNs, Tor, ProxyChains, proxy validation, Surface/Deep/Dark Web concepts, and privacy-focused networking**.

This section is part of the [Ethical_Hacking_Fundamentals](../) repository and provides a structured reference for understanding how traffic can be routed through intermediary networks, how proxy chains work, and how privacy technologies are used in networking and security research.

---

## Overview

This section introduces several technologies that are commonly discussed in network security, privacy, reconnaissance, and controlled penetration-testing environments.

The material progresses through:

**Proxy & VPN Fundamentals → Tor → ProxyChains → Proxy Validation → Web Layers → Tor & Tails OS**

---

## Contents

### 01. Proxy, VPNs & Tor

**[Proxy, VPNs, and TOR](./01.Proxy_VPNs%2C_and_TOR.md)**

Introduces three different approaches to traffic routing and privacy.

### Proxy Servers

Covers:

- HTTP / HTTPS proxies
- SOCKS5
- Transparent proxies
- Reverse proxies
- Traffic-flow concepts
- Advantages and limitations

Basic traffic flow:

**Device → Proxy → Internet**

### VPNs

Covers:

- Virtual private networks
- Encrypted tunnels
- IP masking
- WireGuard
- OpenVPN
- IKEv2
- L2TP/IPSec
- Advantages and limitations

Basic traffic flow:

**Device → Encrypted Tunnel → VPN Server → Internet**

### Tor

Introduces:

- Guard / entry node
- Middle relay
- Exit node
- Onion routing
- Multi-layer encryption
- .onion services
- Privacy and anonymity considerations

The source note also compares Proxy, VPN, and Tor across encryption, anonymity, speed, trust, and system-wide coverage.

---

### 02. ProxyChains

**[ProxyChains](./02.ProxyChains.md)**

Explains how ProxyChains redirects application network connections through configured proxy servers.

### Core Concepts

- SOCKS4
- SOCKS5
- HTTP proxies
- LD_PRELOAD
- Proxy chaining
- Dynamic chains
- Strict chains
- Random chains
- Application proxying

Traffic flow:

**Application → ProxyChains → Proxy Server(s) → Destination**

### Common Use Cases

The notes reference:

- Network security testing
- Proxy-based routing
- Privacy-oriented configurations
- Testing applications through intermediary servers

The source also notes that some Nmap scan types may not function correctly through proxies.

---

### 03. Proxy Checker

**[Proxy Checker](./03.Proxy%20Checker.md)**

Contains an asynchronous Python-based proxy checker using:

**asyncio + aiohttp + aiohttp_socks**

The source note covers checking:

- HTTP proxies
- HTTPS proxies
- SOCKS4 proxies
- SOCKS5 proxies
- Proxy connectivity
- Exit-IP verification
- High-concurrency testing

### Workflow

**Collect Proxy List → Test Connectivity → Verify Exit IP → Save Working Proxies**

The note also discusses proxy-list sources, proxy scraping tools, and a Python implementation that writes working proxies to an output file.

---

### 04. Surface Web vs Deep Web vs Dark Web

**[Surface Web vs Deep Web vs Dark Web](./04.%20Surface%20Web%20vs%20Deep%20Web%20vs%20Dark%20Web.md)**

Explains the commonly used distinction between three categories of internet content.

### Surface Web

Publicly accessible content indexed by conventional search engines.

Examples covered include:

- Search engines
- Video platforms
- News websites
- Public blogs
- Public forums

### Deep Web

Content that is not indexed by ordinary search engines.

Examples covered include:

- Email accounts
- Online banking
- Private databases
- Subscription-based services

### Dark Web

A portion of the Deep Web that requires specialized access mechanisms.

The source note references:

- Tor Browser
- .onion services
- Privacy-focused platforms
- Anonymous forums
- Security and legal risks

The section also includes an internet-iceberg comparison and a side-by-side table.

---

### 05. Tor (The Onion Router)

**[Tor (The Onion Router)](./05.Tor%20(The%20Onion%20Router).md)**

Provides extended notes on Tor, its routing model, history, setup, and related privacy technologies.

### Tor Routing

The notes describe:

**Entry Node → Middle Relay → Exit Node → Destination**

and explain the onion-routing concept in which traffic is protected through multiple encryption layers.

### Topics Covered

- Tor fundamentals
- Privacy and anonymity
- Hidden .onion services
- Tor Browser
- Tor limitations
- Tor history
- Tor Project
- Modern Tor use
- Linux Tor setup
- Tor Browser installation
- Tails OS
- Tails vs VPN vs Tor Browser

### Linux Setup References

The source includes notes for:

- Installing Tor
- Starting the Tor service
- Checking the service status
- Inspecting the local Tor SOCKS listener
- Installing Tor Browser Launcher

---

## Proxy vs VPN vs Tor

| Feature | Proxy | VPN | Tor |
|---|---|---|---|
| Traffic Encryption | Usually not | Yes | Multi-layer routing/encryption |
| IP Masking | Yes | Yes | Yes |
| Typical Speed | Fast | Medium | Slower |
| Trust Model | Proxy operator | VPN provider | Distributed relay network |
| Coverage | Often per application | System-wide | Tor Browser by default |
| Primary Focus | Routing / filtering | Encrypted tunneling | Privacy / anonymity |

The exact privacy and security properties depend on configuration and user behavior.

---

## Proxy Chain Modes

ProxyChains notes describe three main chain modes:

### Dynamic Chain

Uses proxies in order and can skip unavailable proxies.

### Strict Chain

Requires proxies to be used in the configured order. A failed proxy can cause the connection to fail.

### Random Chain

Selects proxies randomly according to the configured chain behavior.

---

## Privacy Limitations

The collection emphasizes that privacy tools do **not guarantee complete anonymity**.

Potential exposure sources discussed in the notes include:

- Browser fingerprinting
- Account logins
- DNS leaks
- Behavioral patterns
- Malware or a compromised endpoint
- Unencrypted traffic through an exit node

A privacy technology is only one part of the overall security model.

---

## Tails OS

The Tor notes also introduce **Tails OS (The Amnesic Incognito Live System)**.

The source describes Tails as a privacy-focused live Linux operating system designed around Tor.

### Topics Covered

- Booting from USB
- Tor integration
- Amnesic behavior
- Persistence considerations
- GnuPG
- KeePassXC
- Tor Browser
- Privacy-focused applications
- Tails vs VPN vs Tor Browser

The material also discusses the limitations of relying on privacy tools without considering user behavior and endpoint security.

---

## Practical Learning Workflow

A structured progression through this section is:

### 1. Understand Traffic Routing

Learn how direct connections differ from:

**Proxy → VPN → Tor**

### 2. Understand the Trust Model

Identify which intermediary can observe traffic, source IP information, or destination information.

### 3. Learn ProxyChains

Understand how application connections can be redirected through configured proxies.

### 4. Validate Connectivity

Use the proxy-checker material to understand:

**Connectivity → Protocol → Exit IP → Reliability**

### 5. Study Tor

Understand relay-based routing, onion encryption, .onion services, and operational limitations.

### 6. Study Web Layers

Understand the difference between publicly indexed content, private/unindexed services, and hidden services.

### 7. Review Privacy Risks

Consider fingerprinting, DNS behavior, account identity, endpoint compromise, and traffic characteristics.

---

## Common Tools & Technologies

The notes reference:

**Tor · Tor Browser · ProxyChains · SOCKS4 · SOCKS5 · HTTP/HTTPS Proxies · VPNs · WireGuard · OpenVPN · IKEv2 · Tails OS · aiohttp · aiohttp_socks**

---

## Security & Privacy Considerations

For responsible use:

- Use privacy technologies for legitimate security, research, and privacy purposes.
- Understand the trust model of the proxy or VPN provider you choose.
- Prefer encrypted connections such as HTTPS for sensitive communications.
- Be aware that Tor exit nodes can observe unencrypted destination traffic.
- Avoid treating IP masking as complete anonymity.
- Keep the endpoint secure and updated.
- Follow local laws and the rules of the network or service you are using.

---

## Authorized Security Testing

Proxy and Tor technologies can also appear in penetration-testing and security-research workflows.

When used during an engagement:

**Define Scope → Confirm Allowed Routing → Configure Test Infrastructure → Validate Connectivity → Perform Test → Document Results**

Network-routing changes should remain within the approved rules of engagement.

---

## Reporting Checklist

When documenting a proxy or privacy-network configuration, record:

| Item | Description |
|---|---|
| Routing Method | Proxy, VPN, Tor, or chained configuration |
| Protocol | HTTP, HTTPS, SOCKS4, SOCKS5, etc. |
| Endpoint | Proxy/VPN/Tor endpoint used |
| Application | Tool or application being routed |
| Exit IP | Observed external IP |
| Validation | Connectivity and routing verification |
| Impact | Effect on visibility, performance, or access |
| Evidence | Screenshots, logs, or command output |

---

## Recommended Study Order

For a strong understanding of this section:

**Proxy Fundamentals → VPN Fundamentals → Tor Fundamentals → ProxyChains → Proxy Checking → Surface/Deep/Dark Web → Tor Browser → Tails OS → Privacy Limitations**

Then connect these concepts with the repository's **Networking, Enumeration, File Transfer, Active Directory, and Tunneling & Port Forwarding** sections.

---

## Responsible Use

This section is intended for:

**Cybersecurity Education · Privacy Research · CTFs · Security Labs · Authorized Penetration Testing**

Do not use proxying, Tor, or chained networking to bypass access controls or conduct unauthorized activity.

---

## Related Repository

This section is part of:

**[Ethical_Hacking_Fundamentals](../)**

Related areas include:

- [Networking](../Networking)
- [Enumeration Techniques for Penetration Testing](../Enumeration%20Techniques%20for%20Penetration%20Testing)
- [File Transfer](../File_Transfer)
- [Active Directory](../AD)
- [Information Security](../Information_Security)

---

## Author

**Kartik Yadav**

Cybersecurity | Networking | Penetration Testing

GitHub: [KartikkYadav](https://github.com/KartikkYadav)

---

⭐ **A practical reference for understanding proxies, VPNs, Tor, ProxyChains, and privacy-focused network routing in cybersecurity.**
