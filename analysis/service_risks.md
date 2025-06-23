# ⚠️ Security Risks from Open Ports

This document outlines the potential security risks identified from the open services running on the target machine (`192.168.1.5`), and suggested mitigation steps.

---

##  High-Risk Services

###  Port 21 – FTP
- **Risk**: Transmits credentials in cleartext, vulnerable to sniffing and brute-force attacks.
- **Fix**: Use SFTP or FTPS, disable anonymous login.

###  Port 23 – Telnet
- **Risk**: Unencrypted remote shell, vulnerable to interception and credential theft.
- **Fix**: Disable Telnet, use SSH instead.

###  Port 25 – SMTP
- **Risk**: Can be misused for spamming or open relays.
- **Fix**: Restrict mail relaying, enforce authentication.

###  Ports 512, 513, 514 – R Services (exec, login, shell)
- **Risk**: Insecure and outdated; allow plaintext credential exchange and trust-based access.
- **Fix**: Completely disable these services.

###  Port 445 / 139 – SMB
- **Risk**: Exploitable by EternalBlue; enables lateral movement and file sharing abuse.
- **Fix**: Disable SMBv1, apply OS patches, restrict access to internal use only.

###  Port 1099 – Java RMI Registry
- **Risk**: Can be exploited to run arbitrary code remotely.
- **Fix**: Use firewall rules to restrict access, disable if unused.

###  Port 1524 – Ingreslock
- **Risk**: Often left open by backdoors (e.g., netcat shells).
- **Fix**: Remove unauthorized software and monitor traffic.

###  Port 2049 – NFS
- **Risk**: If misconfigured, can expose sensitive files over the network.
- **Fix**: Restrict NFS access to trusted IPs, use `no_root_squash` carefully.

###  Port 6000 – X11
- **Risk**: Allows GUI access over network; vulnerable to screen sniping and keystroke logging.
- **Fix**: Disable remote X access or use SSH tunneling with authentication.

---

##  Moderate-Risk Services

###  Port 22 – SSH
- **Risk**: Can be brute-forced if using weak passwords.
- **Fix**: Use key-based authentication, change default port, implement fail2ban.

###  Port 3306 / 5432 – MySQL / PostgreSQL
- **Risk**: Exposed databases may leak sensitive data if misconfigured.
- **Fix**: Bind to localhost only, use strong DB credentials, limit privileges.

###  Port 5900 – VNC
- **Risk**: If unencrypted or weakly authenticated, allows screen takeover.
- **Fix**: Use strong passwords, enable encryption, tunnel over SSH.

###  Port 8009 – AJP13 (Apache JServ)
- **Risk**: Vulnerable to Ghostcat (CVE-2020-1938), which can expose files or RCE.
- **Fix**: Restrict AJP access, upgrade Tomcat, disable if unused.

---

##  Unknown / Less Common Services

###  Port 8180 – Unknown
- **Risk**: Unknown service could be custom or misconfigured software.
- **Fix**: Investigate the process running on this port and apply necessary controls.

---

## ✅ General Recommendations

- Close unused ports/services immediately.
- Apply firewall rules to allow only trusted IPs.
- Use encryption where possible (SSH, HTTPS).
- Keep systems patched and up to date.
- Run vulnerability scans regularly.

---

📝 **Note**: Since this system is intentionally vulnerable (Metasploitable2), the purpose is to demonstrate risk identification and secure configurations.

