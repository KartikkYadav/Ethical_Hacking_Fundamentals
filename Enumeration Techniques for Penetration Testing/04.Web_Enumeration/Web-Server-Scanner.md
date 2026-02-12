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
