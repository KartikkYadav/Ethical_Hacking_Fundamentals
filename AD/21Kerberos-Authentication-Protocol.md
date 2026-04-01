# Kerberos-Authentication-Protocol
## Kerberos Authentication Protocol

- Kerberos is a network authentication protocol that uses tickets and encryption to securely verify the identity of users and services over an insecure network.
- It is the default authentication mechanism in Microsoft Active Directory environments.

---

## Key Components

- **Client**  
  A user or system requesting access to a service  

- **Key Distribution Center (KDC)**  
  The central authentication server composed of:  
  - Authentication Server (AS)  
  - Ticket Granting Server (TGS)  

- **Service Server**  
  The system or resource the client wants to access (e.g., file server, database)  

---

## Kerberos Authentication Flow

### 1. Authentication Request (AS-REQ)
- The client sends a request to the Authentication Server to obtain a Ticket Granting Ticket.

### 2. Ticket Granting Ticket (TGT)
- The KDC verifies the user and issues a TGT, which is encrypted and used for future requests.

### 3. Service Request (TGS-REQ)
- The client presents the TGT to the Ticket Granting Server to request access to a specific service.

### 4. Service Ticket (TGS)
- The KDC issues a service ticket for the requested service.

### 5. Service Access
- The client presents the service ticket to the target server and is granted access.

---

## Types of Tickets

| Ticket Type | Description |
|------------|------------|
| TGT (Ticket Granting Ticket) | Used to request service tickets without re-authentication |
| TGS (Service Ticket) | Used to authenticate to a specific service |

---

## Key Features

- Passwords are never transmitted over the network in plaintext  
- Supports mutual authentication between client and server  
- Enables Single Sign-On (SSO)  
- Uses symmetric key cryptography  

---<img width="1441" height="857" alt="Screenshot From 2026-04-01 19-40-39" src="https://github.com/user-attachments/assets/7f4e1fbf-d646-4fa4-8a4e-ff02c79ac9a6" />

<img width="1527" height="856" alt="Screenshot From 2026-04-01 19-40-52" src="https://github.com/user-attachments/assets/3b8f0ea3-000b-4ec5-904b-eb485be84618" />




## Kerberos in Active Directory

In Microsoft Active Directory:

- The Domain Controller functions as the Key Distribution Center (KDC)  
- Kerberos operates over TCP/UDP port 88  
- Integrated with domain authentication, Group Policy, and service access  

---

## Common Security Attacks

| Attack | Description |
|--------|------------|
| AS-REP Roasting | Targets accounts without pre-authentication |
| Kerberoasting | Extracts service account ticket hashes for offline cracking |
| Pass-the-Ticket | Uses stolen Kerberos tickets to authenticate |
| Golden Ticket | Forged TGT using the KRBTGT account hash |
| Silver Ticket | Forged service ticket for specific services |

---

## Summary

Kerberos is a secure, ticket-based authentication protocol that enables trusted identity verification and Single Sign-On within Active Directory environments without transmitting user passwords over the network.
