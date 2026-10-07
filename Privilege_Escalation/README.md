# Privilege Escalation

A practical collection of notes covering **Windows privilege-escalation fundamentals, Windows administration commands, local enumeration, permissions, services, registry, networking, PowerShell, security controls, automation, and winPEAS-based assessment**.

This section is part of the [Ethical_Hacking_Fundamentals](../) repository and is intended for cybersecurity education, CTFs, isolated labs, and authorized penetration testing.

---

## Overview

Privilege escalation is the process of obtaining privileges beyond those originally assigned to a user or process.

The notes in this section focus primarily on **Windows environments**, while the introductory material also explains the broader distinction between horizontal and vertical privilege escalation.

The collection progresses from Windows command-line fundamentals into system and network enumeration, configuration discovery, writable locations, security-control management, scripting, and automated privilege-escalation enumeration.

---

## Learning Path

**Privilege Escalation Fundamentals → Windows Shell & Commands → System/Network Enumeration → Registry & Services → Permissions & Writable Locations → PowerShell → Windows Security Controls → Automated Enumeration**

---

## Contents

### 01. Windows Basic Commands for Privilege Escalation

**[Windows Basic Commands for Privilege Escalation](./01.Windows_Basic_commands_For_Priviledge_Escalation)**

This is the main section and contains practical Windows notes used for local enumeration and security assessment.

| # | Topic | Reference |
|---|---|---|
| 01 | Privilege Escalation Fundamentals | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/01.Privilege%20escalation.md) |
| 02 | Windows Shell | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/02.%20Windows%20Shell.md) |
| 03 | Windows Basic Commands | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/03.%20Windows%20Basic%20Commands.md) |
| 04 | 8.3 Filename | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/04.8.3%20Filename.md) |
| 05 | Windows Registry | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/05.Windows%20Registry.md) |
| 06 | REG Command | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/06.Reg_Command.md) |
| 07 | PowerShell Commands for Penetration Testing | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/07.PowerShell%20Commands%20for%20Penetration%20Testing.md) |
| 08 | NET Services Suite | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/08.Net%20Services%20Suite.md) |
| 09 | Service Controller Utility | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/09.Service%20Controller%20Utility%20Commands.md) |
| 10 | WMIC Commands | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/10.WMIC%20Commands.md) |
| 11 | NETSH Command | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/11.NETSH%20Command.md) |
| 12 | Network Enumeration | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/12.Network%20Enumeration.md) |
| 13 | Windows Firewall & AV Commands | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/13.Windows%20Firewall%20and%20AV%20Commands.md) |
| 14 | BCDEDIT Command | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/14.BCDEDIT%20Command.md) |
| 15 | DISKPART Command | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/15.DISKPART%20Command.md) |
| 16 | ROBOCOPY Command | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/16.ROBOCOPY%20Command.md) |
| 17 | XCOPY Command | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/17.XCOPY%20Command.md) |
| 18 | ATTRIB Command | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/18.ATTRIB%20Command.md) |
| 19 | Windows Batch Scripting | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/19.Windows%20Batch%20Scripting.md) |
| 20 | Windows Advanced Boot Options | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/20.Windows%20Advanced%20Boot%20Options.md) |
| 21 | 8.3 Filename / Short File Name | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/21.8.3%20Filename%20(Short%20File%20Name).md) |
| 22 | Non-Administrator Writable Locations | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/22.Non%20Administrator%20User%20Write%20Permission%20Locations%20in%20Windows.md) |
| 23 | rlwrap | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/23.rlwrap.md) |
| 24 | Win11Debloat | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/24.Win11Debloat.md) |
| 25 | Windows Defender Remover | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/25.Windows%20Defender%20Remover.md) |
| 26 | Non-Administrator Writable Locations (Additional) | [Open note](./01.Windows_Basic_commands_For_Priviledge_Escalation/26.Non-Administrator%20User%20Writable%20Locations%20in%20Windows.md) |

---

## Privilege Escalation Fundamentals

The introductory note distinguishes between two major forms of privilege escalation:

### Vertical Privilege Escalation

Moving from a lower privilege level to a higher one.

Example:

**Standard User → Administrator**

### Horizontal Privilege Escalation

Accessing another user's resources while remaining at the same privilege level.

Example:

**User A → User B resources**

---

## Windows Privilege Escalation Areas

The notes cover several common assessment areas.

### Kernel & Patch-Level Issues

The collection references Windows kernel vulnerabilities and CVE-based privilege-escalation research.

### Service Misconfiguration

Areas include:

- Unquoted service paths
- Weak service permissions
- Writable service executables
- Service configuration inspection

### Registry

The notes cover Windows Registry concepts and registry locations relevant to service configuration and security assessment.

### Scheduled Tasks

The collection includes scheduled-task enumeration and assessment of writable task-related resources.

### Credentials & Secrets

The material references credential-related areas such as:

- SAM
- LSA Secrets
- LSASS memory
- Stored credentials
- Credential Manager
- Registry-stored secrets

### Token Impersonation

The notes reference Windows token-abuse concepts and related tools.

### Startup Applications

Writable startup locations are included as an area for privilege-escalation assessment.

### Writable Locations

The collection contains dedicated notes for identifying locations writable by non-administrator users.

---

## Windows Shell & Command-Line Administration

The Windows shell notes cover both major command-line environments:

| Shell | Purpose |
|---|---|
| Command Prompt (cmd.exe) | Traditional Windows command interpreter |
| PowerShell | Scriptable shell and automation environment |

The collection also distinguishes between internal shell commands and external executable commands.

---

## PowerShell for Security Testing

**[PowerShell Commands for Penetration Testing](./01.Windows_Basic_commands_For_Priviledge_Escalation/07.PowerShell%20Commands%20for%20Penetration%20Testing.md)**

The PowerShell notes cover a broad host-assessment workflow, including:

- PowerShell execution-policy behavior
- User and system reconnaissance
- Network enumeration
- File-system discovery
- Credential and privilege checks
- Process enumeration
- Service enumeration
- Scheduled tasks
- File download/upload
- Command execution
- Cleanup

PowerShell is also presented as a native Windows administration capability that can be relevant to both offensive security and defensive monitoring.

---

## Windows Network Enumeration

**[Network Enumeration](./01.Windows_Basic_commands_For_Priviledge_Escalation/12.Network%20Enumeration.md)**

The network-enumeration note uses built-in Windows utilities to inspect:

- IP configuration
- DNS configuration
- DNS cache
- ARP cache
- Routing
- Network connectivity
- Active connections
- Listening services
- Associated process IDs

### Core Commands

**ipconfig · ping · tracert · pathping · arp · nslookup · route · netstat**

These commands provide a first-pass picture of the host's network environment.

---

## Registry & System Administration

The collection includes references for:

**Registry → REG → WMIC → NETSH → BCDEDIT → DISKPART → ROBOCOPY → XCOPY → ATTRIB**

These utilities are useful for understanding Windows system configuration, storage, networking, permissions, file operations, and administrative behavior.

---

## Windows Security Controls

The collection contains notes related to:

- Windows Firewall
- Windows Defender / AV configuration
- Security-control inspection
- Lab-specific security-control changes

> Security-control changes should be restricted to isolated laboratories or explicitly authorized assessment environments. Avoid weakening production security controls without documented authorization.

---

## Writable Locations & File Permissions

The notes contain dedicated material on locations writable by non-administrator users.

When assessing privilege escalation, an important question is:

**Can a lower-privileged user modify a file, directory, service, scheduled task, or configuration that executes with higher privileges?**

Common assessment categories include:

- Writable service binaries
- Writable service directories
- Writable scheduled-task targets
- Writable startup locations
- Weak file permissions
- Misconfigured application directories

---

## Automated Privilege Escalation Enumeration

### 04. Final Automated Tools for Privilege Escalation

**[Automated Privilege Escalation Tools](./4.Final_Automated_Tools_For_Privilege_Escalation)**

This section currently contains:

**[winPEAS](./4.Final_Automated_Tools_For_Privilege_Escalation/01.winPeas.md)**

The winPEAS notes cover automated local enumeration for Windows privilege-escalation assessment.

### Areas Referenced

- Operating-system information
- Installed patches
- User and group information
- Token privileges
- Services and service permissions
- Registry permissions
- Credentials and secrets
- Scheduled tasks
- AutoRuns
- Potential privilege-escalation vectors

The note also describes output modes and the security-detection footprint of automated enumeration tools.

---

## 02. Windows Defender Removal / Disable

**[Windows Defender Firewall Remove / Disable](./02.WIndows_Defender_Remove/01.Windows%20Defender%20Firewall%20%20Remove-Disable%20for%20Privilege%20Escalation.md)**

This folder contains lab-oriented material related to disabling or removing Windows security controls during privilege-escalation practice.

Use these configurations only in isolated training systems where changing security controls is intentionally part of the exercise.

---

## Practical Windows Privilege Escalation Workflow

A structured assessment process can be:

### 1. Identify the Current Context

Determine:

- Current username
- Group memberships
- Integrity level / privileges
- Operating-system version
- Architecture

### 2. Enumerate the Host

Inspect:

**Processes → Services → Scheduled Tasks → Registry → Files → Permissions → Environment Variables**

### 3. Enumerate the Network

Inspect:

**Interfaces → Routes → ARP → DNS → Listening Ports → Active Connections**

### 4. Review Security Configuration

Check:

**Services → Firewall → AV/Defender → UAC-related configuration → Security policies**

### 5. Search for Weak Permissions

Look for:

**Writable files → Writable directories → Weak service permissions → Writable scheduled-task targets → Writable startup locations**

### 6. Validate a Finding

Only validate the relevant security weakness within the approved scope and minimize system impact.

### 7. Document the Path

Record:

**Initial Access → Misconfiguration / Weakness → Validation → Privilege Impact → Evidence → Remediation**

---

## Key Tools & Utilities

The section references a combination of native Windows utilities and security tools.

### Windows Built-ins

**CMD · PowerShell · REG · WMIC · NET · NETSH · SC · SCHTASKS · IPCONFIG · ARP · NSLOOKUP · ROUTE · NETSTAT · ROBOCOPY · XCOPY · ATTRIB · DISKPART · BCDEDIT**

### Security / Assessment Tools

**winPEAS · accesschk · Mimikatz · secretsdump · Incognito · JuicyPotato · PrintSpoofer · RoguePotato**

The exact use of each tool should depend on the authorized test objective and environment.

---

## Reporting Checklist

For each privilege-escalation finding, document:

| Field | Description |
|---|---|
| Current User | Initial security context |
| Target Privilege | Administrator / SYSTEM or other privileged context |
| Weakness | Misconfiguration, permission issue, credential exposure, etc. |
| Affected Component | Service, task, registry key, file, directory, etc. |
| Evidence | Commands, screenshots, output, hashes, or other proof |
| Exploitation Status | Confirmed or suspected |
| Impact | Resulting security impact |
| Remediation | Corrective action |
| Retest | Verification after remediation |

---

## Recommended Study Order

For a strong Windows privilege-escalation foundation:

**Windows Shell → Basic Commands → User/Group Enumeration → System Enumeration → Network Enumeration → Services → Scheduled Tasks → Registry → File Permissions → Writable Locations → PowerShell → Security Controls → winPEAS → Manual Validation**

Once the Windows fundamentals are comfortable, connect them with the repository's **Active Directory, Networking, Enumeration, File Transfer, and Tunneling** sections.

---

## Lab Safety

Privilege-escalation techniques can alter services, files, registry settings, security controls, and system state.

Use this material only in:

**CTFs · Isolated Windows Labs · Test Machines · Authorized Penetration Tests**

Keep production systems protected and follow the engagement's rules of engagement.

---

## Responsible Use

This section is intended for:

**Cybersecurity Education · CTFs · Security Labs · Authorized Penetration Testing · Defensive Security Research**

Do not attempt privilege escalation on systems without explicit authorization.

---

## Related Repository

This section is part of:

**[Ethical_Hacking_Fundamentals](../)**

Related areas include:

- [Active Directory](../AD)
- [Networking](../Networking)
- [Enumeration Techniques for Penetration Testing](../Enumeration%20Techniques%20for%20Penetration%20Testing)
- [File Transfer](../File_Transfer)
- [Information Security](../Information_Security)
- Tunneling & Port Forwarding

---

## Author

**Kartik Yadav**

Cybersecurity | Windows Security | Penetration Testing

GitHub: [KartikkYadav](https://github.com/KartikkYadav)

---

⭐ **A practical reference for understanding Windows privilege escalation, local enumeration, permissions, services, PowerShell, and automated assessment techniques.**
