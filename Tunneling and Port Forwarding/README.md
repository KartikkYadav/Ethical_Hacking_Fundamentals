# Tunneling & Port Forwarding

A practical collection of notes covering **network tunneling, SSH port forwarding, SOCKS proxies, VPN-style SSH tunnels, sshuttle, Chisel, Ligolo-ng, and network pivoting** for authorized penetration testing and controlled lab environments.

This section is part of the [Ethical_Hacking_Fundamentals](../) repository and focuses on securely transporting traffic between network segments and accessing services that are not directly reachable from the testing host.

---

## Overview

Tunneling and port forwarding are important networking concepts in penetration testing, system administration, and internal network assessments.

The notes progress from the underlying concepts into practical tunneling methods:

**Tunneling Fundamentals → Lab Setup → SSH Port Forwarding → SOCKS Proxying → VPN-Style SSH Tunnels → sshuttle → Chisel → Ligolo-ng → Pivoting & Internal Network Access**

---

## Contents

### 01. Tunneling & Port Forwarding Fundamentals

**[Tunneling and Port Forwarding](./01.Tunneling_and_Port_Forwarding)**

Introduces the difference between tunneling and port forwarding.

### Tunneling

The notes describe tunneling as encapsulating one protocol inside another to transport traffic across a network.

Examples referenced include:

- SSH tunneling
- VPNs
- HTTPS/TLS-based transport

### Port Forwarding

Covers:

- Local port forwarding
- Remote port forwarding
- Dynamic port forwarding
- Service redirection
- Controlled access to internal services

Basic SSH examples in the source material include:

`ssh -L`, `ssh -R`, and `ssh -D`

---

### 02. Lab Setup

**[Lab Setup](./01.Tunneling_and_Port_Forwarding/02.Lab_Setup.md)**

Provides the network layout used in the practical tunneling exercises.

The lab contains multiple networks and systems, including:

- Kali / attacker system
- Windows jumpbox
- Debian jumpbox
- Windows Server
- Additional Windows host
- Separate network segments

The lab is designed to demonstrate **pivoting and access between network segments**.

---

# SSH Tunneling

### 03. SSH Tunneling

**[SSH Tunneling](./02.SSH%20Tunneling%20(SSH%20Port%20Forwarding)/03.SSH_Tunneling.md)**

Provides the main SSH tunneling reference.

The source covers three primary SSH forwarding modes:

| Mode | SSH Option | Purpose |
|---|---|---|
| Local Port Forwarding | `-L` | Make a remote/internal service available locally |
| Remote Port Forwarding | `-R` | Expose a client-side service through the SSH server |
| Dynamic Port Forwarding | `-D` | Create a SOCKS proxy for dynamic routing |

The note also covers background tunnels, gateway binding, SSH configuration options, VPN comparisons, and penetration-testing use cases.

---

### 04. Local Port Forwarding

**[SSH Local Port Forwarding](./02.SSH%20Tunneling%20(SSH%20Port%20Forwarding)/04.Local_Port_Forwarding.md)**

Local forwarding allows a port on the testing machine to reach a service accessible from the SSH server.

### Traffic Flow

**Local Host → SSH Server / Pivot → Internal Service**

### Common Use Cases

- Internal web applications
- Database services
- Administrative interfaces
- Services hidden behind network boundaries

The notes use:

`ssh -L [LOCAL_PORT]:[DESTINATION_HOST]:[DESTINATION_PORT] user@SSH_SERVER`

and explain the role of `-N` for tunnel-only sessions.

---

### 05. Remote Port Forwarding

**[SSH Remote Port Forwarding](./02.SSH%20Tunneling%20(SSH%20Port%20Forwarding)/05.Remote_Port_forwarding.md)**

Remote forwarding opens a listening port on the SSH server and forwards traffic back toward a service reachable from the SSH client side.

### Traffic Flow

**Remote Client → SSH Server → Client-Side Service**

The source material covers:

- `-R` syntax
- Remote bind addresses
- GatewayPorts
- SSH server configuration
- Reverse pivoting
- Local-service exposure
- Windows `plink.exe` examples

A key security point is that externally bound forwarded ports should be avoided unless explicitly required.

---

### 06. Dynamic Port Forwarding / SOCKS

**[SSH Dynamic Port Forwarding](./02.SSH%20Tunneling%20(SSH%20Port%20Forwarding)/06.SSH_Dynamic_Port_Forwarding.md)**

Creates a local SOCKS proxy that can dynamically route traffic through an SSH server.

### Traffic Flow

**Application → SOCKS Proxy → SSH Server → Destination**

The notes cover:

- SOCKS4 / SOCKS5 concepts
- `ssh -D`
- Windows PuTTY configuration
- ProxyChains integration
- HTTP requests through the tunnel
- Nmap traffic through a SOCKS proxy

The source specifically notes that some Nmap scan types do not work correctly through proxies.

---

### 07. VPN Tunnel Using SSH Server

**[VPN Tunnel Using SSH Server](./02.SSH%20Tunneling%20(SSH%20Port%20Forwarding)/06.VPN%20Tunnel%20Using%20SSH%20Server.md)**

Explains a VPN-like Layer-3 tunnel using SSH and **TUN interfaces**.

### Key Components

- TUN interfaces
- SSH tunnel forwarding
- IP addressing
- Routing
- IP forwarding
- NAT
- Internal subnet access
- Cleanup and rollback

### Traffic Flow

**Attacker → TUN Interface → SSH Server → Internal Network**

The source also includes steps for restoring forwarding settings, removing NAT rules, deleting routes, and restoring SSH hardening.

---

### 08. sshuttle

**[sshuttle - Transparent Proxy / VPN over SSH](./02.SSH%20Tunneling%20(SSH%20Port%20Forwarding)/07.sshuttle.md)**

Covers sshuttle as a transparent proxy / VPN-like solution using SSH.

The notes include:

- Installation
- Basic SSH connectivity
- Routing a specific subnet
- Routing all traffic
- Excluding hosts or subnets
- DNS forwarding
- Daemon mode
- SSH-key usage
- Sudoers handling
- Testing access through the tunnel
- Scanning internal services through the routed connection

The source recommends targeting specific subnets during penetration testing rather than unnecessarily routing all traffic.

---

### 09. Chisel

**[Chisel - Tunneling & Port Forwarding](./02.SSH%20Tunneling%20(SSH%20Port%20Forwarding)/08.Chisel.md)**

Introduces Chisel as a tunneling and port-forwarding tool.

The source covers:

- Installation
- Server and client setup
- Reverse tunneling
- Local and remote forwarding concepts
- SOCKS5
- ProxyChains integration
- Windows and Linux client usage
- Internal-network access

### Main Concepts

**Client ↔ Chisel Server ↔ Forwarded Service**

and:

**SOCKS5 → ProxyChains → Internal Destination**

Use Chisel only inside an approved testing environment because tunneling can bypass normal network boundaries.

---

# Ligolo-ng

### 10. Ligolo-ng - Pivoting & Internal Network Access

**[Ligolo-ng - Pivoting & Internal Network Access](./03.Ligolo-ng%20-%20Pivoting%20%26%20Internal%20Network%20Access)**

Covers Ligolo-ng as a userland VPN-style pivoting tool.

The source highlights:

- TUN-based networking
- TCP & UDP access
- Reverse agent connections
- Multiple pivoting
- Internal network routing
- Agent localhost access
- Port-forwarding listeners

### General Architecture

**Kali / Ligolo Proxy → Ligolo Agent → Internal Network**

### Main Workflow

**Create TUN Interface → Start Proxy → Connect Agent → Start Session → Add Route → Test Internal Access**

The notes also cover forwarding access to the agent's localhost and listener-based port forwarding.

---

## Tunneling Methods Compared

| Technique | Main Capability | Typical Scope |
|---|---|---|
| SSH Local Forward | Access one remote service locally | Single service |
| SSH Remote Forward | Expose a client-side service remotely | Single service |
| SSH Dynamic Forward | SOCKS-based dynamic routing | Multiple TCP destinations |
| SSH TUN/TAP | Layer-3 VPN-style routing | Network/subnet |
| sshuttle | Transparent routed access over SSH | Selected subnets |
| Chisel | Port forwarding and SOCKS tunneling | Services / networks |
| Ligolo-ng | TUN-based pivoting | Internal network access |

---

## Local vs Remote vs Dynamic Forwarding

### Local Forwarding

**Local Port → SSH Server → Remote Service**

Use when the testing machine needs access to an internal service reachable from the SSH host.

### Remote Forwarding

**Remote Port → SSH Server → Client-Side Service**

Use when a remote system needs access to a service reachable from the SSH client.

### Dynamic Forwarding

**Application → SOCKS Proxy → SSH Server → Destination**

Use when multiple destinations need to be reached dynamically through a pivot.

---

## Practical Pivoting Workflow

A structured workflow represented across this section is:

### 1. Map the Network

Identify:

- Reachable hosts
- Network interfaces
- Internal subnets
- Pivot hosts
- Services behind the pivot

### 2. Identify the Pivot

Determine which authorized host can reach the internal network.

### 3. Select the Tunnel Type

Choose based on the required access:

**Single Service → SSH `-L` / `-R`**

**Multiple Destinations → SSH `-D` / Chisel SOCKS**

**Subnet-Level Access → sshuttle / TUN-based tunnel / Ligolo-ng**

### 4. Establish the Tunnel

Configure the server, client, routes, listeners, or SOCKS interface.

### 5. Verify Connectivity

Use appropriate checks such as:

- `ip route`
- `ss`
- `curl`
- `ping`
- Nmap where appropriate

### 6. Access the Internal Service

Use the appropriate client or security-testing tool through the established path.

### 7. Document the Path

Record:

**Attacker → Pivot → Tunnel → Internal Network → Target Service**

### 8. Clean Up

Remove:

- Temporary routes
- TUN interfaces
- NAT rules
- Forwarded ports
- Temporary binaries
- Tunnel processes

Restore modified security settings where applicable.

---

## Troubleshooting

| Symptom | Possible Cause |
|---|---|
| Forwarded port not listening | Tunnel not established or incorrect bind address |
| Internal host unreachable | Missing route or wrong destination |
| SOCKS application fails | Tool does not support the configured proxy method |
| Tunnel connects but traffic fails | Routing or firewall configuration |
| TUN interface unavailable | Interface not created or insufficient privileges |
| Remote forward inaccessible | SSH server binding / GatewayPorts configuration |
| sshuttle traffic fails | Incorrect subnet, routing, DNS, or firewall rules |

---

## Security Considerations

Tunneling can intentionally bypass normal network boundaries, so careful scope control is essential.

During authorized testing:

- Define exactly which subnets may be reached.
- Prefer the smallest required network scope.
- Bind forwarded ports locally unless external access is explicitly needed.
- Protect SSH keys and tunnel credentials.
- Monitor tunnel processes and network connections.
- Remove routes and listeners after testing.
- Restore firewall, SSH, NAT, and forwarding configuration changes.

---

## Detection & Defense

Defenders can monitor tunneling and pivoting through several signals.

### Host Indicators

- Unexpected SSH sessions
- TUN/TAP interface creation
- New listening ports
- Chisel or Ligolo-ng processes
- sshuttle processes
- Unusual command-line activity

### Network Indicators

- Long-lived encrypted connections
- Unexpected outbound SSH
- Traffic crossing normally restricted segments
- Unexpected SOCKS-like traffic
- New connections from pivot hosts to internal networks

### Configuration Indicators

- `AllowTcpForwarding`
- `GatewayPorts`
- `PermitTunnel`
- New routes
- NAT rules
- Firewall changes

---

## Reporting Checklist

For each tunneling or pivoting activity, record:

| Field | Description |
|---|---|
| Pivot Host | System used as the intermediary |
| Tunnel Type | SSH, sshuttle, Chisel, Ligolo-ng, etc. |
| Source | Testing host |
| Destination | Internal host/service |
| Port / Subnet | Forwarded port or routed network |
| Route | Traffic path |
| Evidence | Commands, screenshots, logs |
| Impact | Service or network access obtained |
| Cleanup | Routes, listeners, and processes removed |

---

## Recommended Study Order

For the strongest progression:

**Tunneling Fundamentals → Lab Setup → SSH Local Forwarding → SSH Remote Forwarding → SSH Dynamic Forwarding → SSH TUN/TAP → sshuttle → Chisel → Ligolo-ng → Advanced Pivoting**

Before using the advanced pivoting tools, understand how **routing, NAT, interfaces, TCP connections, SOCKS proxies, and SSH forwarding** work.

---

## Lab Safety

Tunneling and pivoting can expose internal services and bridge network segments.

Use these techniques only in:

**CTFs · Isolated Labs · Training Environments · Authorized Penetration Tests**

Avoid exposing forwarded services to unintended networks and restore all temporary routing or security changes after testing.

---

## Responsible Use

This section is intended for:

**Cybersecurity Education · CTFs · Security Labs · Authorized Penetration Testing · Network Security Research**

Do not create tunnels, pivots, or forwarded listeners to access networks or systems without explicit authorization.

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
- [Tor & Proxy](../Tor%26Proxy)

---

## Author

**Kartik Yadav**

Cybersecurity | Network Security | Penetration Testing

GitHub: [KartikkYadav](https://github.com/KartikkYadav)

---

⭐ **A practical reference for understanding SSH tunneling, port forwarding, SOCKS proxying, VPN-style tunnels, and internal network pivoting.**
