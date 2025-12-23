# Weekly CTFs

A collection of write-ups and documentation from my weekly penetration testing labs and Capture The Flag (CTF) challenges. This repository serves as a record of my technical growth in cybersecurity, focusing on vulnerability research, exploitation, and post-exploitation techniques.

## Laboratory Environment
* **Attacker OS:** Kali Linux (Docker Container/Native)
* **Targets:** * **Metasploitable 2:** A Linux-based vulnerable VM used for network-level exploitation.
    * **OWASP Juice Shop:** A modern web application designed for security training.
* **Tools Used:** Metasploit Framework, Nmap, Docker, Python PTY.

---

## Week 1: Initial Footholds & Authentication Bypass

### 1. OWASP Juice Shop - SQL Injection (Authentication Bypass)
* **Vulnerability:** SQL Injection (SQLi)
* **Objective:** Gain Administrative access without a valid password.
* **Method:** * Identified the admin email (`admin@juice-sh.op`) via product reviews.
    * Injected the payload `admin@juice-sh.op'--` into the email field.
* **Result:** Successfully bypassed the login logic by commenting out the password check in the backend database.

### 2. Metasploitable 2 - Samba Remote Root (RCE)
* **Vulnerability:** CVE-2007-2447 (Samba "username map script")
* **Service:** Samba (Port 445)
* **Method:**
    1.  Performed reconnaissance using `netstat -ant` to confirm Port 445 was listening.
    2.  Utilized Metasploit module `exploit/multi/samba/usermap_script`.
    3.  Set `RHOSTS` to the target container IP (`172.17.0.2`).
* **Post-Exploitation:**
    * Verified `root` privileges with `whoami`.
    * Stabilized the shell using: `python -c 'import pty; pty.spawn("/bin/bash")'`.
* **Result:** Gained full interactive Root access to the target system.

---

## Ethical Disclaimer
All activities documented in this repository were performed in a controlled, isolated laboratory environment for educational purposes. Unauthorized access to computer systems is illegal.
