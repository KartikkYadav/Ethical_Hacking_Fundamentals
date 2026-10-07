# File Transfer

A practical collection of notes covering **file transfer techniques, transfer servers, protocol selection, remote file movement, and NetExec-based file operations** for authorized penetration testing and cybersecurity lab environments.

This section is part of the [Ethical_Hacking_Fundamentals](../) repository and focuses on moving files between systems during security testing while also considering verification, cleanup, and defensive detection.

---

## Overview

File transfer is a common requirement during penetration testing and red team exercises. Testers may need to stage tools on a host, retrieve files for analysis, move data through an available protocol, or transfer files across network segments.

This section covers both **traditional file-transfer services** and **offensive-security transfer methods**, including HTTP/HTTPS, FTP, SFTP, SMB, TFTP, WebDAV, raw TCP sockets, SSH-based transfers, living-off-the-land techniques, Base64-based transfer, and NetExec.

---

## Learning Path

**File Transfer Fundamentals → Transfer Servers → Protocol-Based Transfers → Remote File Movement → NetExec File Operations → Integrity Verification → Detection & Defense**

---

## Contents

### 01. Offensive File Transfer Techniques

**[Offensive File Transfer Techniques](./01.Offfensive_File_Transfer_Technique.md)**

A broad reference covering file movement from an offensive-security perspective.

Topics referenced include:

- HTTP / HTTPS
- Custom HTTP `PUT` and PHP `POST` upload methods
- SMB
- FTP
- TFTP
- WebDAV
- Netcat
- Socat
- Bash `/dev/tcp`
- SCP
- Rsync
- SFTP
- Windows LOLBAS
- Linux GTFOBins
- Base64 copy-paste transfers
- Hash-based integrity verification
- Meterpreter file transfer
- NetExec
- Detection and defense considerations

The note is organized around moving files in both directions, verification, cleanup, and related techniques.

---

### 02. File Transfers

**[File Transfers](./02.File%20Transfers.md)**

A map-of-content that organizes file-transfer techniques by transport method.

Main categories include:

**HTTP / HTTPS**
- HTTP server
- HTTP/HTTPS server
- HTTP/HTTPS client
- HTTP file-transfer one-liners
- PHP HTTP POST server

**SMB**
- SMB server
- SMB client

**FTP**
- FTP server
- FTP client commands

**TFTP**
- TFTP server
- TFTP client

**WebDAV**
- WebDAV-based file transfer

**Raw Sockets**
- Netcat
- Socat
- Bash `/dev/tcp`

**SSH-Based**
- SCP
- Rsync
- SFTP

**Living Off the Land**
- Windows LOLBAS
- Linux GTFOBins

**No-Egress & Integrity**
- Base64 copy-paste transfer
- Integrity verification

The note also connects file transfer with tunneling, enumeration, and payload staging.

---

### 03. File Transfer Servers

**[File Transfer Servers](./03.%20File-Transfers-Servers.md)**

Practical server-side setup notes for commonly used file-transfer protocols.

### Protocols Covered

| Protocol | Typical Use | Security Consideration |
|---|---|---|
| HTTP / HTTPS | Browser and command-line transfers | Prefer HTTPS for sensitive data |
| FTP / FTPS | File transfer services | Prefer encrypted alternatives |
| SFTP | Secure file transfer over SSH | Encrypted and strongly preferred |
| SMB | Windows/Linux network file sharing | Restrict shares and permissions |
| TFTP | Lightweight transfers | Insecure; use only where appropriate |

The note also covers:

- Shared directory preparation
- Apache HTTP server
- `vsftpd`
- OpenSSH / SFTP
- Samba
- `tftpd-hpa`
- File-transfer client applications
- Permissions and ownership
- Service configuration
- Security best practices
- Logging and patching

---

### 04. NetExec File Transfers & Execution

**[NXC File Transfers and Execution](./04.NXC-File-Transfers-and-Execution.md)**

Reference material for using **NetExec (`nxc`)** with Windows hosts through **WinRM and SMB**.

The source note covers operations such as:

- Uploading files
- Downloading files
- Listing remote directories
- Executing commands
- Executing transferred files
- Running PowerShell scripts
- File cleanup
- SMB-based file operations
- WinRM-based file operations

This is particularly relevant for Windows environments during authorized security assessments and lab exercises.

---

## File Transfer Channels

The material can be grouped into several practical channels:

| Channel | Examples |
|---|---|
| Web | HTTP, HTTPS, PHP upload endpoints |
| Windows File Sharing | SMB, Samba |
| File Transfer Protocols | FTP, FTPS, TFTP, SFTP |
| Web-Based File Sharing | WebDAV |
| Raw Network Connections | Netcat, Socat, `/dev/tcp` |
| SSH | SCP, Rsync, SFTP |
| Built-in Utilities | Windows LOLBAS, Linux GTFOBins |
| Security Frameworks | Meterpreter, NetExec |
| Shell-Based | Base64 copy-paste |

---

## Choosing a Transfer Method

Select a method based on the **available services, network connectivity, permissions, and engagement scope**.

A practical decision process is:

**Identify available connectivity → Check permitted protocols → Select the least complex suitable channel → Transfer → Verify integrity → Clean up**

Examples:

- **HTTP/HTTPS** — useful when web connectivity is available.
- **SMB** — common in Windows environments.
- **SFTP/SCP** — useful where SSH is available.
- **FTP/FTPS** — suitable for environments that explicitly support it.
- **TFTP** — limited-use option for compatible systems.
- **WebDAV** — useful where HTTP-based file movement is required.
- **Netcat/Socat** — useful for controlled raw-socket transfers.
- **LOLBAS/GTFOBins** — useful for understanding file movement using existing host utilities.
- **NetExec** — useful for controlled remote file operations over SMB/WinRM.

---

## Verification & Integrity

A successful transfer should be verified before the next testing step.

The notes reference hash-based integrity verification using utilities such as:

- `sha256sum`
- `certutil -hashfile`
- `Get-FileHash`

A simple workflow is:

**Transfer → Calculate Hash → Compare Source & Destination → Continue Testing**

This helps confirm that the file arrived intact and was not altered during transfer.

---

## Cleanup

After a lab exercise or authorized test:

**Remove temporary files → Remove staged tooling → Close temporary services → Review logs**

Cleanup is especially important when files were placed in temporary Windows directories or shared folders.

---

## Security Best Practices

For defensive and operational safety:

- Prefer **SFTP, FTPS, or HTTPS** for sensitive transfers.
- Restrict SMB shares using appropriate users, groups, and permissions.
- Avoid unnecessary guest or anonymous access.
- Use strong authentication and SSH keys where appropriate.
- Keep transfer services patched and updated.
- Monitor transfer logs and endpoint activity.
- Verify file integrity after transfer.
- Remove temporary files and services after testing.
- Keep offensive testing inside the agreed scope.

---

## Detection & Defense

File movement can generate useful security signals across endpoints and networks.

Relevant defensive areas include:

**Network Monitoring**
- Unusual outbound connections
- Unexpected file-transfer protocols
- Large or unusual transfers
- Connections to unauthorized transfer servers

**Endpoint Monitoring**
- Creation of files in temporary or public directories
- Execution of newly transferred binaries
- Unusual PowerShell activity
- Abuse of built-in utilities

**Authentication Monitoring**
- Unexpected SMB/WinRM authentication
- Suspicious remote administrative activity
- Repeated authentication failures

**Artifact Analysis**
- Transferred executables
- Script files
- Temporary archives
- Unusual hashes or file locations

---

## Practical Workflow

A structured file-transfer workflow for authorized testing:

### 1. Identify the Environment

Determine the operating system, available services, network path, and access level.

### 2. Determine Available Channels

Use enumeration results to identify viable transfer mechanisms.

### 3. Select the Transfer Method

Choose an appropriate protocol or utility based on the environment and rules of engagement.

### 4. Transfer the File

Move the required file using the selected channel.

### 5. Verify

Compare hashes or otherwise confirm successful delivery.

### 6. Perform the Authorized Test

Use the transferred file only for the approved security assessment activity.

### 7. Clean Up

Remove temporary files and shut down temporary services when no longer required.

### 8. Document

Record the transfer method, affected host, evidence, and relevant security observations.

---

## Related Topics

This section connects naturally with:

**Enumeration**  
Identifies open ports and services that determine which transfer channel is available.

**Tunneling & Port Forwarding**  
Can provide connectivity between network segments when direct access is unavailable.

**Metasploit / Meterpreter**  
Provides file-transfer capabilities inside an established authorized session.

**Windows / Active Directory**  
SMB and WinRM are common components of Windows enterprise environments.

---

## Responsible Use

The material in this section is intended for:

**Cybersecurity Education · CTFs · Security Labs · Authorized Penetration Testing · Defensive Research**

Use file-transfer and remote-execution techniques only on systems you own or have explicit permission to assess.

Some techniques can move executables, scripts, or sensitive data and may trigger endpoint or network security controls. Test them only within an approved and controlled environment.

---

## Related Repository

This section is part of:

**[Ethical_Hacking_Fundamentals](../)**

Other areas of the repository include:

- Active Directory
- Enumeration Techniques for Penetration Testing
- Networking
- Privilege Escalation
- Tunneling & Port Forwarding
- Wireless Pentesting
- Information Security

---

## Author

**Kartik Yadav**

Cybersecurity | Penetration Testing | Ethical Hacking

GitHub: [KartikkYadav](https://github.com/KartikkYadav)

---

⭐ **A practical reference for understanding file movement across common protocols, Windows remote-management channels, and controlled offensive-security workflows.**
