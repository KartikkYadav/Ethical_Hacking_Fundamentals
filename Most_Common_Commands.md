## NMAP =
- Master Command
  nmap -sC -sV -sT -O -A 192.168.1.1
  nmap -p 80,8080 -sV 192.168.1.1
  nmap --script  192.168.1.1


##Curl =

curl -IL https://www.inlanefreight.com

## Gobuster

     gobuster dir -u http://154.57.164.66:31906 -w /usr/share/seclists/Discovery/Web-Content/common.txt

## Netcat
    nc -nlvp 443

### FTP

- Ftp login

      ftp 127.0.0.1 2121

- Brute Force
  
      hydra -L users.list -P passwords.list ftp://10.129.57.179:2121 -v

- For single  usesrs 

      hydra -l bob -P passwords.list ftp://10.129.57.179:2121 -v

## DNS Enum

To find the subdomain of doamin we brute force subdomain and try to resolve from the DNS Server.

- dndenum tool

      dnsenum --enum inlanefreight.com -f /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt -r

- subfinder

     subfinder -d domain.com

  
