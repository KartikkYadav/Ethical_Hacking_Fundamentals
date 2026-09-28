Sure — here is the **last command reference directly here**:

# File Transfer & Service Commands — Linux + Windows

## Quick Reference

| Method   | Linux Server             | Windows Client      | Windows Server | Linux Client    |
| -------- | ------------------------ | ------------------- | -------------- | --------------- |
| FTP      | `pyftpdlib`              | `ftp`               | IIS FTP        | `ftp` / `curl`  |
| HTTP     | `python3 -m http.server` | `curl` / PowerShell | IIS / Python   | `wget` / `curl` |
| SCP/SFTP | `sshd`                   | `scp` / `sftp`      | OpenSSH        | `scp` / `sftp`  |
| SMB      | Samba                    | `net use`           | SMB            | `smbclient`     |
| Netcat   | `nc`                     | `ncat`              | `ncat`         | `nc`            |
| TFTP     | `tftpd-hpa`              | `tftp`              | TFTP Server    | `tftp`          |

---

# 🐧 Linux

## 1. FTP

### Server



Start temporary FTP server:

```bash
python3 -m pyftpdlib -p 2121
```

Allow write access:

```bash
python3 -m pyftpdlib -p 2121 -w
```

### Client

```bash
ftp <SERVER_IP> 2121
```

Inside FTP:

```text
binary
ls
get file.zip
put file.txt
bye
```

Using `curl`:

```bash
curl ftp://<SERVER_IP>:2121/file.txt -o file.txt
```

Upload:

```bash
curl -T file.txt ftp://<SERVER_IP>:2121/
```

---

# 2. HTTP

### Server

```bash
python3 -m http.server 8000
```

Bind to all interfaces:

```bash
python3 -m http.server 8000 --bind 0.0.0.0
```

### Client

```bash
wget http://<SERVER_IP>:8000/file.txt
```

```bash
curl http://<SERVER_IP>:8000/file.txt -o file.txt
```

---

# 3. SCP / SFTP

### SSH Server

```bash
sudo apt install openssh-server -y
sudo systemctl enable --now ssh
```

Check:

```bash
sudo systemctl status ssh
```

### SCP

Upload:

```bash
scp file.txt user@<SERVER_IP>:/tmp/
```

Download:

```bash
scp user@<SERVER_IP>:/tmp/file.txt .
```

Directory:

```bash
scp -r directory/ user@<SERVER_IP>:/tmp/
```

### SFTP

```bash
sftp user@<SERVER_IP>
```

Inside:

```text
ls
get file.txt
put file.txt
cd /tmp
lcd /home/kali
bye
```

---

# 4. Netcat

### Receiver

```bash
nc -lvnp 9001 > received.txt
```

### Sender

```bash
nc <SERVER_IP> 9001 < file.txt
```

For ZIP/binary files:

```bash
nc <SERVER_IP> 9001 < file.zip
```

---

# 5. SMB

### Server

```bash
sudo apt install samba -y
mkdir -p ~/share
```

Edit:

```bash
sudo nano /etc/samba/smb.conf
```

Add:

```ini
[share]
   path = /home/kali/share
   browseable = yes
   read only = no
   guest ok = yes
```

Restart:

```bash
sudo systemctl restart smbd
```

Check:

```bash
sudo systemctl status smbd
```

### Client

```bash
sudo apt install smbclient -y
```

List shares:

```bash
smbclient -L //<SERVER_IP>/ -N
```

Connect:

```bash
smbclient //<SERVER_IP>/share -N
```

Inside:

```text
ls
get file.txt
put file.txt
exit
```

---

# 6. TFTP

Install:

```bash
sudo apt install tftpd-hpa tftp-hpa -y
```

Check:

```bash
sudo systemctl status tftpd-hpa
```

Client:

```bash
tftp <SERVER_IP>
```

Then:

```text
get file.txt
put file.txt
quit
```

---

# 🪟 Windows

## 1. FTP

### Client

CMD:

```cmd
ftp <SERVER_IP> 2121
```

Inside:

```text
binary
dir
get file.zip
put file.txt
bye
```

Test connection:

```powershell
Test-NetConnection <SERVER_IP> -Port 2121
```

### Server

Windows Server can use **IIS FTP Server**:

```text
Server Manager
→ Add Roles and Features
→ Web Server (IIS)
→ FTP Server
```

---

# 2. HTTP

### Client — PowerShell

```powershell
Invoke-WebRequest http://<SERVER_IP>:8000/file.txt -OutFile file.txt
```

Or:

```powershell
curl.exe http://<SERVER_IP>:8000/file.txt -o file.txt
```

### Server — Python

```powershell
cd C:\Users\Public\Downloads
python -m http.server 8000
```

---

# 3. SCP / SFTP

Check OpenSSH:

```powershell
ssh -V
```

Upload:

```powershell
scp file.zip user@<SERVER_IP>:/tmp/
```

Download:

```powershell
scp user@<SERVER_IP>:/tmp/file.zip .
```

SFTP:

```powershell
sftp user@<SERVER_IP>
```

### OpenSSH Server

```powershell
Get-Service sshd
```

Start:

```powershell
Start-Service sshd
```

Enable at startup:

```powershell
Set-Service -Name sshd -StartupType Automatic
```

---

# 4. SMB

Map a share:

```cmd
net use Z: \\<SERVER_IP>\share
```

With credentials:

```cmd
net use Z: \\<SERVER_IP>\share /user:USERNAME PASSWORD
```

Copy:

```cmd
copy file.txt Z:\
```

Robocopy:

```cmd
robocopy C:\source \\<SERVER_IP>\share
```

Remove mapping:

```cmd
net use Z: /delete
```

---



# 🔄 Linux ↔ Windows

## Kali → Windows — HTTP

### Kali

```bash
cd ~/Downloads
python3 -m http.server 8000
```

### Windows

```powershell
curl.exe http://<KALI_IP>:8000/file.zip -o file.zip
```

---

## Kali → Windows — FTP

### Kali

```bash
cd ~/Downloads
python3 -m pyftpdlib -p 2121
```

### Windows

```cmd
ftp <KALI_IP> 2121
```

Then:

```text
binary
get file.zip
bye
```

---

## Windows → Kali — SCP

### Kali

```bash
sudo systemctl enable --now ssh
```

### Windows

```powershell
scp file.zip kali@<KALI_IP>:/tmp/
```

---

## Windows → Kali — SMB

### Kali

```bash
sudo apt install samba -y
mkdir -p ~/share
```

Configure `/etc/samba/smb.conf`:

```ini
[share]
   path = /home/kali/share
   read only = no
   guest ok = yes
```

Restart:

```bash
sudo systemctl restart smbd
```

### Windows

```cmd
net use Z: \\<KALI_IP>\share
```

Then:

```cmd
copy file.txt Z:\
```

---

# 🔐 Verify File Transfer

### Linux

```bash
sha256sum file.zip
```

### Windows

```powershell
Get-FileHash .\file.zip -Algorithm SHA256
```

The hashes should be **identical**.

Check file size:

### Linux

```bash
ls -lh file.zip
```

### Windows

```cmd
dir file.zip
```

---

# 🛠️ Troubleshooting

### Check listening ports — Linux

```bash
sudo ss -lntup
```

### Check listening ports — Windows

```powershell
Get-NetTCPConnection -State Listen
```

### Test Windows → Linux port

```powershell
Test-NetConnection <LINUX_IP> -Port <PORT>
```

### Check Linux firewall

```bash
sudo ufw status
```

Temporary port:

```bash
sudo ufw allow 8000/tcp
```

Remove afterward:

```bash
sudo ufw delete allow 8000/tcp
```

### ZIP transferred incorrectly

Linux:

```bash
unzip -t file.zip
sha256sum file.zip
```

Windows:

```powershell
Get-FileHash .\file.zip -Algorithm SHA256
```

If hashes differ, transfer the file again.

For FTP, use:

```text
binary
```

before transferring ZIP/EXE/DLL/image/PDF files.

---
      |
