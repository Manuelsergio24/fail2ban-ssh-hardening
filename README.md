# 🔒 Fail2Ban SSH Hardening (Security+ Home Lab)

**Date:** July 2025  
**Platform:** Ubuntu Linux VM (VirtualBox on macOS)  
**Tools Used:** Nmap · Fail2Ban · Systemd · Nano · iptables

---

## 🎯 Project Goal

Set up a working host-based intrusion prevention system using Fail2Ban to detect and block SSH brute-force attacks. This project aligns with Security+ objectives for securing Linux systems and monitoring authentication logs.

---

## 🛠️ What I Did

1. Scanned the server with Nmap to identify open ports (found ports 21 and 22 open)
2. Installed Fail2Ban to protect SSH from brute-force attacks
3. Created a custom jail configuration in `/etc/fail2ban/jail.local`:
   ```ini
   [sshd]
   enabled = true
   port = ssh
   logpath = /var/log/auth.log
   maxretry = 5


4.	Restarted and tested the Fail2Ban service, ensuring the sshd jail was active and watching for intrusion attempts.


5.	Verified the setup using: sudo fail2ban-client status sshd

Output confirmed it was watching /var/log/auth.log and tracking failed SSH logins

✅ What I Learned
	•	How to detect and defend against SSH brute-force attacks
	•	How to configure host-based intrusion prevention tools (Fail2Ban)
	•	How to troubleshoot log files and system services (systemctl, journalctl)
	•	Why log-based security is essential for real-world systems
