# Protocols and Ports List
## Application / Web Servers

| Name      | Port No.             | Protocol | Notes                                   |
|-----------|----------------------|----------|-----------------------------------------|
| HTTP      | 80, 8080, 8081, 8000 | TCP      | Standard web servers (Apache, Nginx)    |
| HTTPS     | 443, 8443, 4143      | TCP      | Secure web servers                      |
| Tomcat    | 8080, 8443, 8005, 8009 | TCP    | Java-based web server                   |
| GlassFish | 4848, 8080, 8181     | TCP      | Java EE server                          |
| Jetty     | 8080                 | TCP      | Java-based HTTP server                  |
| WebLogic  | 7001                 | TCP      | Oracle middleware server                |
| JBoss     | 8080, 9990           | TCP      | Java-based application server           |
| WildFly   | 9990                 | TCP      | JBoss successor                         |
| WebSphere | 9043, 9060, 9080, 9443 | TCP    | IBM application server                  |
| IIS       | 80, 443              | TCP      | Microsoft web server                    |
| Liferay   | 8080                 | TCP      | Java-based portal server                |
| Zope      | 8080                 | TCP      | Python-based application server         |
| Alfresco  | 8080                 | TCP      | Enterprise content management           |

## Panel Ports

| Name                                | Port No. | Protocol | Notes                              |
|-------------------------------------|----------|----------|------------------------------------|
| cPanel                              | 2082     | TCP      | Standard cPanel interface          |
| cPanel - SSL                        | 2083     | TCP      | Secure cPanel interface            |
| WHM                                 | 2086     | TCP      | WebHost Manager                    |
| WHM - SSL                           | 2087     | TCP      | Secure WebHost Manager             |
| Webmail                             | 2095     | TCP      | Web-based email                    |
| Webmail - SSL                       | 2096     | TCP      | Secure web-based email             |
| Plesk Control Panel                 | 8880     | TCP      | Plesk admin panel                  |
| Plesk Control Panel - SSL           | 8443     | TCP      | Secure Plesk panel                 |
| Plesk Linux Webmail                 | N/A      | TCP      | Not assigned by default            |
| Plesk Windows Webmail (SmarterMail) | 9998     | TCP      | Windows webmail                    |
| Virtuozzo                           | 4643     | TCP      | VPS management                     |
| DotNet Panel                        | 9001     | TCP      | Windows hosting panel              |
| DotNet Panel Login                  | 80       | TCP      | Insecure login over HTTP           |
| RDP (Remote Desktop Protocol)       | 4489     | TCP      | Alternative to standard RDP (3389) |
| SFTP Shared/Reseller Servers        | 2222     | TCP      | Secure file transfer for resellers |
| Webdisk                             | 2077     | TCP      | Web-based file storage             |
| Webdisk - SSL                       | 2078     | TCP      | Secure web-based file storage      |

## Database / Datastore Protocols

| Name                 | Port No. | Protocol | Notes                           |
|----------------------|----------|----------|---------------------------------|
| MySQL                | 3306     | TCP      | Open-source relational database |
| MariaDB              | 3306     | TCP      | MySQL fork                      |
| PostgreSQL           | 5432     | TCP      | Open-source relational database |
| Microsoft SQL Server | 1433     | TCP      | Microsoft database              |
| Oracle DB            | 1521     | TCP      | Oracle database listener        |
| MongoDB              | 27017    | TCP      | NoSQL database                  |
| Redis                | 6379     | TCP      | In-memory database              |
| Cassandra            | 9042     | TCP      | NoSQL database                  |
| CouchDB              | 5984     | TCP      | REST-based NoSQL database       |
| DB2                  | 50000    | TCP      | IBM database                    |

## Message Queues / Transfer Protocols

| Name            | Port No. | Protocol | Notes                     |
|-----------------|----------|----------|---------------------------|
| RabbitMQ        | 15672    | TCP      | AMQP-based message broker |
| Kafka           | 9092     | TCP      | Distributed messaging     |
| ActiveMQ        | 61616    | TCP      | Java message broker       |
| Redis Pub/Sub   | 6379     | TCP      | In-memory pub/sub         |
| Mosquitto       | 1883     | TCP      | MQTT broker               |
| ZeroMQ          | Varies   | TCP/UDP  | Messaging library         |
| Tibco RV Daemon | 7474     | TCP/UDP  | Enterprise messaging      |
| IBM MQ Listener | 1414     | TCP      | Message broker            |

## File Transfer Protocols

| Name     | Port No.                | Protocol | Notes                     |
|----------|-------------------------|----------|---------------------------|
| FTP      | 20, 21, 2121            | TCP      | Unencrypted file transfer |
| FTPS     | 21, 990, 989            | TCP      | Secure FTP                |
| SFTP     | 22                      | TCP      | SSH-based file transfer   |
| SCP      | 22                      | TCP      | Secure copy over SSH      |
| TFTP     | 69                      | UDP      | Trivial file transfer     |
| RSYNC    | 873                     | TCP      | File synchronization      |
| SMB/CIFS | 139, 445                | TCP/UDP  | Windows file sharing      |
| NFS      | 111, 2049, 4045         | TCP/UDP  | Unix file sharing         |
| AFP      | 548                     | TCP      | Apple file sharing        |
| WebDAV   | 80, 443                 | TCP      | HTTP-based file sharing   |
| MooseFS  | 9419, 9420, 9421, 9422, 9425 | TCP | Distributed file system   |

## Remote Connection Protocols

| Name       | Port No.                              | Protocol | Notes                       |
|------------|---------------------------------------|----------|-----------------------------|
| SSH        | 22, 2222                              | TCP      | Secure remote shell         |
| Telnet     | 23                                    | TCP      | Insecure remote shell       |
| RDP        | 3389                                  | TCP      | Remote Desktop Protocol     |
| VNC        | 5900, 5901, 5902, 6002, 6003, 6000–6005 | TCP/UDP | Virtual Network Computing   |
| X11        | 1494                                  | TCP      | Remote GUI display          |
| Citrix ICA | 1494                                  | TCP      | Citrix virtual app delivery |
| NX         | 7000                                  | TCP      | Remote desktop over SSH     |
| TeamViewer | 5938                                  | TCP/UDP  | Remote desktop              |
| LogMeIn    | 2002, 443                             | TCP      | Remote control              |
| Anydesk    | 7070                                  | TCP      | Remote access tool          |

## Mail Transfer Protocols

| Name     | Port No.                | Protocol | Notes              |
|----------|-------------------------|----------|--------------------|
| SMTP     | 25, 26, 587, 465        | TCP/UDP  | Outgoing mail      |
| POP3     | 110, 995                | TCP/UDP  | Incoming mail      |
| IMAP     | 143, 993                | TCP/UDP  | Incoming mail      |
| Exchange | 135, 102, 110, 143, 993, 25, 587, 465 | TCP/UDP | Microsoft Exchange |
| Postfix  | 25, 587                 | TCP/UDP  | Mail transfer agent |
| Exim     | 25, 587                 | TCP/UDP  | Mail transfer agent |

## VPN / Secure Tunneling

| Name      | Port No. | Protocol | Notes                |
|-----------|----------|----------|----------------------|
| OpenVPN   | 1194     | UDP/TCP  | SSL VPN              |
| IPsec/IKE | 500, 4500| UDP      | VPN tunneling        |
| L2TP      | 1701     | UDP      | VPN tunneling        |
| PPTP      | 1723     | TCP      | VPN tunneling        |
| WireGuard | 51820    | UDP      | Modern VPN tunneling |

## VoIP / Conferencing

| Name  | Port No.      | Protocol | Notes                       |
|-------|---------------|----------|-----------------------------|
| SIP   | 5060, 5061    | TCP/UDP  | VoIP signaling              |
| RTP   | 5004, 5005    | UDP      | Real‑time media transport   |
| H.323 | 1720          | TCP      | Video conferencing          |
| Jitsi | 5280, 5347    | TCP/UDP  | Open‑source conferencing    |
| Zoom  | 8801–8810     | TCP      | Video conferencing          |

## Miscellaneous

| Name        | Port No.    | Protocol | Notes                 |
|-------------|-------------|----------|-----------------------|
| SNMP        | 161, 162    | UDP      | Network monitoring    |
| NTP         | 123         | UDP      | Network time protocol |
| Syslog      | 514         | UDP      | Logging               |
| DNS         | 53          | UDP/TCP  | Domain name resolution|
| mDNS        | 5353        | UDP      | Multicast DNS         |
| LPD         | 515         | TCP      | Line printer daemon   |
| Docker API  | 2375, 2376  | TCP      | Container management  |
| Kubernetes API | 6443     | TCP      | Cluster management    |
| Consul      | 8500        | TCP      | Service discovery     |
