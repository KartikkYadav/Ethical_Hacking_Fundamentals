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
