# 🔒 Fail2Ban SSH Hardening (Security+ Home Lab)

**Date:** July 2025  
**Platform:** Ubuntu Linux VM (VirtualBox on macOS)  
**Tools Used:** Nmap · Fail2Ban · Systemd · Nano · iptables

---

## 🎯 Project Goal

Set up a working host-based intrusion prevention system using Fail2Ban to detect and block SSH brute-force attacks. This project aligns with Security+ objectives for securing Linux systems and monitoring authentication logs.

---

Fail2Ban SSH Hardening (Security+ Home Lab)

Date: July 2025  
Platform: Ubuntu Linux VM (VirtualBox on macOS)  
Tools Used: Nmap · Fail2Ban · Systemd · Nano · iptables · Git · Logwatch · Crontab · msmtp

🎯 Project Goal

Set up a host-based intrusion prevention system (HIPS) using Fail2Ban to detect and block SSH brute-force attacks. Integrated logging and automated alerting to monitor and email system activity. This project aligns with CompTIA Security+ objectives focused on system hardening, log monitoring, and automated response.

🛠️ What I Did

- Scanned the VM with Nmap and found ports 21 and 22 open
- Installed Fail2Ban and configured a custom jail in /etc/fail2ban/jail.local:
  [sshd]  
  enabled = true  
  port = ssh  
  logpath = /var/log/auth.log  
  maxretry = 5
- Verified active jail using: sudo fail2ban-client status sshd
- Confirmed Fail2Ban was monitoring /var/log/auth.log and tracking failed SSH login attempts
- Performed simulated brute-force attacks using Hydra
- Observed Fail2Ban banning malicious IPs automatically
- Located and reviewed fail2ban-auth.log to verify blocked attempts
- Installed Logwatch and configured it to generate daily reports
- Automated daily logs at 7 AM using crontab to output to: /home/ubuntu/daily-logwatch.txt
- Set up msmtp to securely send both Fail2Ban logs and Logwatch reports to iCloud email
- Created .msmtprc configuration with proper authentication and TLS settings
- Linked project folder to GitHub and used Git for version control
- Added README.md documentation to summarize and track lab progress

✅ What I Learned

- How to detect and block SSH brute-force attacks
- How to configure Fail2Ban with custom jails for real-time intrusion prevention
- How to review authentication logs and test bans manually
- How to automate system log reports using Logwatch and crontab
- How to securely send logs to an external email address using msmtp
- How to organize and publish cybersecurity lab documentation with GitHub
