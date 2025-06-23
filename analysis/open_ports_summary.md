# 🛠 Open Ports Summary

This table lists the open ports detected on the target IP `192.168.1.5` using a TCP SYN scan (`nmap -sS`).

| Port | State | Service         | Description                            |
|------|-------|------------------|----------------------------------------|
| 21   | open  | ftp              | File Transfer Protocol (insecure)      |
| 22   | open  | ssh              | Secure Shell for remote login          |
| 23   | open  | telnet           | Unencrypted remote login (high risk)   |
| 25   | open  | smtp             | Mail server (can allow spam relaying)  |
| 53   | open  | domain           | DNS service                            |
| 80   | open  | http             | Web server                             |
| 111  | open  | rpcbind          | Remote Procedure Call service          |
| 139  | open  | netbios-ssn      | NetBIOS session service (SMB)          |
| 445  | open  | microsoft-ds     | SMB over TCP                           |
| 512  | open  | exec             | Remote command execution (insecure)    |
| 513  | open  | login            | Remote login service (plaintext)       |
| 514  | open  | shell            | RSH service (insecure)                 |
| 1099 | open  | rmiregistry      | Java RMI Registry                      |
| 1524 | open  | ingreslock       | Often used by backdoors/malware        |
| 2049 | open  | nfs              | Network File System                    |
| 2121 | open  | ccproxy-ftp      | Proxy FTP server                       |
| 3306 | open  | mysql            | MySQL database                         |
| 5432 | open  | postgresql       | PostgreSQL database                    |
| 5900 | open  | vnc              | Virtual Network Computing (remote desktop) |
| 6000 | open  | X11              | X Window System (unsecured GUI access) |
| 6667 | open  | irc              | Internet Relay Chat                    |
| 8009 | open  | ajp13            | Apache JServ Protocol (Tomcat backend) |
| 8180 | open  | unknown          | Unknown service (may need further analysis) |

---

**Scan Performed:** `nmap -sS 192.168.1.5`  
**System Scanned:** Metasploitable2  
**MAC Address:** 08:00:27:F9:BD:FA  
**Scanned at:** 2025-06-23 06:09 EDT

