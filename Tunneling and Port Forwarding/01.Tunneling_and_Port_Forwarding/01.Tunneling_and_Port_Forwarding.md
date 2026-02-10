# Tunneling and Port Forwarding

**Tunneling and Port Forwarding** are networking techniques widely used in **system administration, DevOps, and cybersecurity** to securely access internal services, bypass network restrictions, and control traffic flow.

---

## Tunneling

**Tunneling** is the process of encapsulating one network protocol inside another to securely transmit data across an untrusted network such as the internet.

### Key Characteristics
- Creates a secure communication channel
- Encrypts transmitted data
- Enables remote access to internal or restricted resources

### Common Examples
- SSH Tunneling
- VPNs (IPsec, OpenVPN, WireGuard)
- HTTPS (TLS over TCP)

### Example: SSH Tunnel

Access an internal database through a bastion host:

    ssh -L 3306:internal-db:3306 user@bastion-host

This forwards local port 3306 to internal-db:3306 through a secure SSH tunnel.

## Port Forwarding
Port Forwarding redirects network traffic from one port to another, either on the same system or a different system.

### Key Characteristics

- Redirects or maps traffic

- Commonly used with NAT, firewalls, and routers

- Can expose internal services in a controlled manner

### Types of Port Forwarding

- Local Port Forwarding

- Remote Port Forwarding

- Dynamic Port Forwarding (SOCKS Proxy)

### Port Forwarding Types with Examples

#### 1. Local Port Forwarding
Forwards a local port to a remote service:

    ssh -L 8080:localhost:80 user@server

Traffic sent to localhost:8080 is forwarded to port 80 on the remote server.

#### 2. Remote Port Forwarding
Exposes a local service on a remote server:

    ssh -R 9090:localhost:3000 user@server

Traffic sent to server:9090 is forwarded to the local application running on port 3000.

#### 3. Dynamic Port Forwarding
Creates a SOCKS proxy for flexible traffic routing:

    ssh -D 1080 user@server

Applications configured to use the SOCKS proxy at localhost:1080 can route traffic through the SSH tunnel.

### Tunneling vs Port Forwarding

    Feature              	Tunneling	                        Port  Forwarding
    Purpose	                Secure communication	            Traffic redirection
    Encryption          	Usually enabled                  	Not always
    Primary Use          	Remote access, VPNs	                Service exposure & access
    Common Tools        	SSH, VPN software                	SSH, routers, firewalls

#### Cybersecurity Use Cases

- Secure access to internal systems during penetration testing

- Firewall and network restriction bypassing

- Administrative access to private infrastructure

- Network pivoting in ethical hacking scenarios

### Summary
Tunneling focuses on secure data transmission across networks, while port forwarding focuses on directing traffic between ports. Both techniques are essential in modern networking and cybersecurity environments.

