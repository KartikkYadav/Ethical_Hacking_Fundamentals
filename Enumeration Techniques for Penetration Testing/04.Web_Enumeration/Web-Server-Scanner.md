# Web-Server-Scanner

## Web Server Scanner

---

## WhatWeb Usage

### Install WhatWeb
            
Install WhatWeb using apt package manager:

    apt install whatweb

## Basic Scans (WhatWeb)
### Scan a Simple Website

    whatweb http://192.168.1.211

### Scan a Website on Custom Port

    whatweb http://192.168.1.211:2222

### Scan a Specific Page

    whatweb http://192.168.1.44/dvwa/login.php

### Scan Web App on Port 8080

    whatweb http://192.168.1.211:8080

## Nmap HTTP Enumeration Script
Enumerate website technologies and vulnerabilities:

    nmap -v -Pn -sT -sV -p 80 --script=http-enum.nse 192.168.1.211

Another example:

    nmap -v -Pn -sT -sV -p 80 --script=http-enum.nse 192.168.1.239

## Nikto
### Install Nikto

    apt install nikto

### Nikto Basic Commands
View Help

    nikto -H

### Check Version

    nikto -Version

### Update Nikto

    nikto -update

### Check Database

    nikto -dbcheck

### List Plugins

    nikto -list-plugins

### Basic Scanning (Nikto)
Basic Scan

    nikto -h 192.168.1.239

### Scan Full URL

    nikto -h http://192.168.1.239/

### Scan Port 8080

    nikto -h http://192.168.1.239:8080

### Scan CGI-BIN Directory

    nikto -h http://192.168.1.239/cgi-bin/

### Scan All CGI Directories

    nikto -h http://192.168.1.239 -C all

### Specify Port Explicitly

    nikto -h 192.168.1.239 -port 2222

### Scan Non-Standard Port

    nikto -h 192.168.1.239 -port 2222

## Using Proxy (Nikto)
### Scan Through Proxy

    nikto -host 192.168.1.35 -useproxy http://127.0.0.1:8080

### Scan Target Through Proxy

    nikto -host 192.168.1.239 -useproxy http://127.0.0.1:8080

### Scan Specific URL Through Proxy

    nikto -host http://192.168.1.239/phpmyadmin -useproxy http://127.0.0.1:8080

### Proxy Scan Example

    nikto -h http://192.168.1.239/ -useproxy http://127.0.0.1:8080

### Scanning CGI Directories
### Scan All Common CGI Directories

    nikto -C all -h 192.168.1.239

### Scan CGI Directories on Specific Port

    nikto -C all -h 192.168.1.239 -port 2222


## 🔍 Nikto Scanning Guide
### 🧪 Scan CGI Directories
    
    nikto -Cgidirs all -h 192.168.1.239
    nikto -Cgidirs all -h 192.168.1.239 -port 2222

### 📄 Scan Targets from File

    nikto -h targets.txt

### 📢 Verbose Output
- Perform scan with verbose output:

      nikto -h http://192.168.1.239 -Display V

- Verbose CGI scanning:

      nikto -Cgidirs all -h 192.168.1.239 -port 2222 -Display V

### ❌ Disabling SSL, DNS Lookups, 404 Detection
- Disable DNS lookup and SSL:

      nikto -h 192.168.1.239 -nolookup -nossl

- Disable HTTP 404 detection:

      nikto -h 192.168.1.239 -no404

### 🌐 Scanning Different Ports and HTTPS Sites
- Scan server on port 81:

      nikto -h http://192.168.1.239:81

- Scan HTTPS site:

      nikto -h https://192.168.1.239/demosite/

### 🔌 Using Specific Plugins
- Apache XSS expectation plugin:

      nikto -Plugins "apache_expect_xss(verbose,debug)" -h 192.168.1.239 -port 2222

- Shellshock vulnerability plugin:
            
      nikto -Plugins "shellshock(verbose)" -h 192.168.1.239 -port 2222
      nikto -Plugins "shellshock" -h 192.168.1.239 -port 2222

### ⚙️ Nikto Tuning Options

- Tuning allows targeting specific vulnerabilities during scans.

            Code	Type
            1	Interesting File / Seen in Logs
            2	Misconfiguration / Default File
            3	Information Disclosure
            4	Injection (XSS/Script/HTML)
            5	Remote File Retrieval - Inside Web Root
            6	Denial of Service
            7	Remote File Retrieval - Server Wide
            8	Command Execution / Remote Shell
            9	SQL Injection
            0	File Upload
            a	Authentication Bypass
            b	Software Identification
            c	Remote Source Inclusion
            x	Reverse Tuning Options

### 🧪 Tuning Examples
- Scan for interesting files:

      nikto -h http://192.168.1.239/ -Tuning 1

- Scan for misconfigurations:

      nikto -h http://192.168.1.239/ -Tuning 2

- Scan for information disclosure:

      nikto -h http://192.168.1.239/ -Tuning 3

- Scan all except specific tuning:

      nikto -C all -h 192.168.1.239 -port 80 -Tuning x

### 🕵️ Custom User-Agent & Proxy Usage
- Set custom user-agent:

      nikto -h http://192.168.1.239 -useragent "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:15.0) Gecko/20100101 Firefox/15.0.1"

- Use proxy with custom user-agent:

      nikto -h http://192.168.1.236:2222 \
      -useragent "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:15.0) Gecko/20100101 Firefox/15.0.1" \
      -useproxy http://127.0.0.1:8080

### 💡 Extra Tips

- Always run Nikto and WhatWeb with -ssl when testing HTTPS endpoints
- Keep Nikto updated for latest vulnerability checks
- Avoid DoS tuning on live/sensitive systems without permission
