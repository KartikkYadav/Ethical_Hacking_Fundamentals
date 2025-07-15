# Email-Tracking

##  Email Tracking & Protocols

###  What is E-mail?

- ( E-mail (Electronic Mail) allows users to send and receive messages over the internet.

### Three Parts of an Email Address

**Example:**  `sachin@armourinfosec.com`

1. **sachin** — Account name or username  
2. **@** — Separator  
3. **armourinfosec.com** — Domain (could represent company, group, or department)

###  Mail User Agent (MUA)

A Mail User Agent (MUA) is software that allows users to send and receive emails.

####  MUA Programs:

- Microsoft Outlook  
- Mozilla Thunderbird

####  MUA Web-Based Clients:

- Gmail  
- Yahoo Mail  
- Outlook.com


---


### Desktop-Based MUA Programs

| MUA Program       | Platform              |
|-------------------|-----------------------|
| Microsoft Outlook | Windows, macOS.       |
| Mozilla Thunderbird | Windows, macOS, Linux |
| eM Client         | Windows, macOS.       |
| Mailbird          | Windows               |
| Apple Mail        | macOS, iOS            |
| The Bat!          | Windows               |
| Claws Mail        | Linux, Windows        |
| Evolution         | Linux                 |

---
### Description

- **Microsoft Outlook**: Feature-rich client, supports Exchange, POP3, IMAP  
- **Mozilla Thunderbird**: Free, open-source; supports add-ons and multiple accounts  
- **eM Client**: Simple UI, calendar integration  
- **Mailbird**: Lightweight, supports third-party apps  
- **Apple Mail**: Default client for Apple devices  
- **The Bat!**: Advanced filtering and encryption support  
- **Claws Mail**: Lightweight and fast, focused on performance  
- **Evolution**: GNOME desktop default email client with calendar and tasks

---


###  Mail Transfer Agent (MTA)

A Mail Transfer Agent (MTA), also known as:

- Mail Server  
- Mail Router  
- Internet Mailer

It receives emails from MUAs and routes them to the appropriate destination using:

- **Simple Mail Transfer Protocol (SMTP)**

| Port | Description                  |
|------|------------------------------|
| 25   | Default (non-encrypted)      |
| 465 (TCP) | Encrypted (SMTPS)       |

---
## Mail Transfer Agent (MTA)

A Mail Transfer Agent (MTA) is a software application responsible for sending, receiving, and routing email messages between mail servers.

### What Does an MTA Do?

- Accepts outgoing mail from a Mail User Agent (MUA).
- Routes email to the destination MTA (or relays it through other MTAs).
- Hands off messages to a Mail Delivery Agent (MDA) for final delivery.

### MTA Workflow

[Sender MUA] → [Sender MTA] → [Internet] → [Recipient MTA] → [MDA] → [Recipient Mailbox]


### Protocol Used

| Protocol | Purpose            | Port (Unencrypted) | Port (Encrypted)       |
|----------|---------------------|--------------------|------------------------|
| SMTP     | Sending/relaying mail | 25               | 465 (SSL), 587 (STARTTLS) |





###  Mail Delivery Agent (MDA)

A Mail Delivery Agent (MDA) delivers emails from the Mail Transfer Agent (MTA) to the recipient's mailbox.

- Uses protocols like:
  - **POP3 (Post Office Protocol v3)**
  - **IMAP (Internet Message Access Protocol)**


A Mail Delivery Agent (MDA) is a software component responsible for receiving email messages from the Mail Transfer Agent (MTA) and delivering them to the recipient's mailbox.

###  MDA Workflow

[Sender MUA] > [Sender MTA] > [Recipient MTA] > [MDA] > [Recipient Mailbox] ©


- The MTA routes the email  
- The MDA handles the final delivery to the correct mailbox (e.g., `/var/mail/username` or a maildir).

---

###  Common MDA Protocols

| Protocol | Description                                           | Default Port | Secure Port (SSL/TLS) |
|----------|-------------------------------------------------------|--------------|-----------------------|
| POP3     | Downloads email from server to client and deletes from server | 110          | 995                   |
| IMAP     | Accesses email stored on server; syncs across devices | 143          | 993                   |

---

##  IMAP vs POP3

- IMAP and POP3 are both protocols used by MDAs to retrieve emails from a server.

| Feature             | IMAP                        | POP3                           |
|----------------------|----------------------------|--------------------------------|
| Storage              | Keeps emails on server     | Downloads & deletes from server|
| Sync across devices  | Yes                        | No                             |
| Offline access       | Downloads on demand        | Full download                  |
| Folder support       | Yes                        | No                             |

##  IMAP (Internet Message Access Protocol)

- Default port: **143**
- Secure port: **993 (SSL/TLS)**

##  POP3 (Post Office Protocol v3)

- Default port: **110**
- Secure port: **995 (SSL/TLS)**
- 
###  Popular MDA Software

| MDA Tool   | Description                                           |
|------------|-------------------------------------------------------|
| Procmail   | One of the oldest MDAs, supports filtering and mail sorting |
| Maildrop   | Lightweight MDA, used with Courier mail server        |
| Dovecot    | Commonly used for IMAP/POP3 and mailbox delivery      |
| Postfix (Local) | Postfix can act as an MDA when configured with local |
| Fetchmail  | Technically a remote mail retriever, often used with MDA for local delivery |

---

## Key Points

- The MDA does not send emails; it only delivers them locally.
- It may perform actions like:
  - Filtering spam
  - Sorting into folders
  - Triggering scripts
- MDA is often integrated with email servers like Dovecot or Postfix.



##  SMTP (Simple Mail Transfer Protocol)

- SMTP is the protocol used by MTAs to send emails.
- Primarily used to transfer emails from the client to the mail server and between servers.

| Port | Encryption Type |
|------|-----------------|
| 25   | None (plaintext)|
| 465  | SSL/TLS         |
| 587  | STARTTLS        |

##  SMTP Authentication

- Ensures that only authorized users can send emails through the server.
- Helps prevent spam and misuse.



##  Summary: Email Infrastructure

| Component | Role                                  | Protocols / Ports                      |
|-----------|---------------------------------------|---------------------------------------|
| MUA       | Mail User Agent - user interface      | IMAP (143/993), POP3 (110/995), SMTP (587) |
| MTA       | Mail Transfer Agent - routes emails   | SMTP (25/465/587)                     |
| MDA       | Mail Delivery Agent - final delivery | IMAP, POP3                            |

##  Flow Overview

[User writes email on MUA]
→ sends via SMTP to MTA
→ MTA routes across internet
→ recipient MTA receives
→ MDA delivers to mailbox
→ recipient MUA fetches via IMAP/POP3


##  Key Security Measures

- Enable encryption (SSL/TLS) on all protocols.
- Use strong SMTP authentication to prevent misuse.
- Employ spam and malware filters on MTAs and MDAs.
