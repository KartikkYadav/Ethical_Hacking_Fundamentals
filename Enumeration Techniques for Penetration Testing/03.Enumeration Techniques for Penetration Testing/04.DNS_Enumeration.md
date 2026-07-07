# DNS Enumeration

**DNS Enumeration** is the process of collecting information about a domain and its DNS records to map out the domain's infrastructure. It helps identify subdomains, mail servers, name servers, and other publicly available information that could reveal potential attack vectors.

## Domain Co-relation

### Vertical Domain Co-relation
Examples of vertical domain co-relation, where subdomains are associated with the main domain:

* **armourinfosec.com**
  * `admin.armourinfosec.com`
  * `mail.armourinfosec.com`
* **tesla.com**
  * `admin.tesla.com`
  * `mail.tesla.com`
  * `cp.tesla.com`
  * `test.tesla.com`

### Horizontal Domain Co-relation
Examples of horizontal domain co-relation, where domains are associated across different TLDs or organizations:

* **armourinfosec domains**
  * `thehackersworld.com`
  * `infosecwarrior.com`
  * `armourinfosec.io`
* **tesla domains**
  * `tesla.cn`
  * `teslamotors.com`
  * `tesla.services`

---

## Why DNS Enumeration is Important

* **Information Gathering**: It allows attackers and security testers to gather data about the target's network.
* **Identifying Attack Surfaces**: Misconfigured DNS records, exposed subdomains, and outdated infrastructure can be potential entry points.
* **Social Engineering**: Collected data can be used to craft more targeted phishing or social engineering attacks.
* **Pentesting & Red Teaming**: Understanding the DNS infrastructure helps in simulating real-world attack scenarios.

## Types of DNS Enumeration

1. **Direct Domain Enumeration**: Identifying subdomains and associated records through direct queries.
2. **Reverse DNS Lookup**: Resolving an IP address back to its domain name.
3. **Zone Transfer (AXFR) Enumeration**: Attempting to transfer the entire DNS zone file from a misconfigured DNS server.
4. **Brute-Force Subdomain Discovery**: Trying common subdomain names to identify valid ones.
5. **PTR Record Lookup**: Resolving IP addresses to domain names.
6. **Certificate Transparency Logs**: Checking for subdomains and domains listed in publicly available SSL/TLS certificates.
7. **WHOIS Lookup**: Gathering domain registration and ownership details.

---

## Target Range

IP Address to Domain Name mapping within a specified range:
* `192.168.1.1/24`
* `192.31.242.107`
* `192.31.242.107/32`
* `2620:134:b000::/40`
* `192.31.243.0/26`
* `192.31.243.64/28`
* `192.31.243.96/27`

## Common DNS Record Types

| Record Type | Description |
| :--- | :--- |
| **A** | Maps a domain to an IPv4 address |
| **AAAA** | Maps a domain to an IPv6 address |
| **CNAME** | Alias of one domain to another |
| **MX** | Mail server records |
| **NS** | Name server records |
| **SOA** | Start of Authority, contains domain admin and refresh info |
| **TXT** | Text records, used for SPF, DKIM, and other metadata |
| **PTR** | Maps an IP address to a domain (reverse lookup) |

---

## Key DNS Enumeration Tools

| Tool | Purpose | Example Command |
| :--- | :--- | :--- |
| **nslookup** | Query DNS records | `nslookup armourinfosec.com` |
| **dig** | Detailed DNS lookup | `dig armourinfosec.com ANY` |
| **host** | Simple DNS lookup | `host armourinfosec.com` |
| **nmap** | DNS and port scanning | `nmap -p 53 --script-dns-brute armourinfosec.com` |
| **dnsrecon** | Automated DNS enumeration | `dnsrecon -d armourinfosec.com` |
| **dnsenum** | Brute force DNS enumeration | `dnsenum armourinfosec.com` |
| **sublist3r** | Subdomain enumeration | `sublist3r -d armourinfosec.com` |
| **crt.sh** | Certificate search for subdomains | `https://crt.sh/?q=armourinfosec.com` |

## Example DNS Enumeration Commands

1. **Find all DNS records using `dig`**:

       dig armourinfosec.com ANY


2. **Reverse lookup for PTR records using `dig`**:

        dig -x 192.168.1.43


3. **Find subdomains using `dnsrecon`**:

        dnsrecon -d armourinfosec.com -t std


4. **Find subdomains using `sublist3r`**:

        sublist3r -d armourinfosec.com


5. **Perform zone transfer using `dig`**:

        dig axfr @ns1.armourinfosec.com armourinfosec.com

### 4. Find subdomains using `sublist3r`

    sublist3r -d armourinfosec.com

### 5. Perform zone transfer using `dig`

    dig axfr @ns1.armourinfosec.com armourinfosec.com


### 6. Identify DNS servers using `nslookup`

    nslookup -type=NS armourinfosec.com


### 7. Enumerate DNS records with `nmap`

    nmap -p 53 --script dns-brute armourinfosec.com

---

## Port scan for Domain Name Enumeration with nmap

Perform a port scan to identify open DNS ports:

    nmap -v -Pn -sT -sU -sV -p T:53,U:53 -il ip.txt



* `-v`: Verbose mode
* `-Pn`: Treat all hosts as online
* `-sT`: TCP connect scan
* `-sU`: UDP scan
* `-sV`: Version detection
* `-p T:53,U:53`: Scan TCP and UDP port 53 (DNS)
* `-il ip.txt`: Input list of IP addresses

---

## SSL and Redirection

### Check SSL Certificate
You can check the SSL certificate using the following OpenSSL command:

    openssl s_client -connect domain.com:443


### Follow HTTP Redirection
To follow HTTP and HTTPS redirection:

    curl -IL http://domain.com

text
* `-I`: Show headers only
* `-L`: Follow redirects

---

## Find PTR Records & Internal DNS

To find PTR records and identify internal DNS servers:

1. **Using `nmap`**:

        nmap -v -sV -sC -A -O -p 80,443 192.168.1.43 --dns-servers 192.168.1.43


2. **Using `nslookup`**:

        nslookup 192.168.1.43 192.168.1.43


3. **Using `dig`**:

        dig -x 192.168.1.43 @192.168.1.43


4. **Using `dnsx`**:
        
        dnsx -silent -resp-only -ptr -l /home/armour/Documents/ip.txt
        dnsx -silent -resp-only -ptr -l /tmp/ip.txt

---

## Advanced Enumeration

### Find ASN (Autonomous System Number) using `nmap`

      nmap --script targets-asn --script-args targets-asn.asn=394151


### Query domain using `nslookup`

    nslookup ipsacademy.org
---

## IP Address History

You can find the historical IP address records of a domain using the following online services:
* `https://viewdns.info/iphistory/`
* **Example**: `https://viewdns.info/iphistory/?domain=armourinfosec.com`

---

## Common Subdomains

### Common Google Subdomains
* `myaccount.google.com`
* `maps.google.co.in`
* `play.google.com`
* `news.google.com`
* `mail.google.com`
* `meet.google.com`
* `chat.google.com`

### Common Facebook Subdomains
* `pay.facebook.com`

### Common Godaddy Subdomains
* `in.godaddy.com`
* `kr.godaddy.com`
* `pe.godaddy.com`
* `pl.godaddy.com`
* `id.godaddy.com`

### Common Government Subdomains
* `www.incredibleindia.org`
* `www.india.gov.in`
* `services.india.gov.in`
* `rti.india.gov.in`
* `covid19.india.gov.in`

---

## Public DNS Servers

1. `8.8.8.8`   - Google DNS
2. `8.8.4.4`   - Google DNS
3. `64.6.64.6` - Verisign DNS
