# OS Security Checklist (Linux & Windows)

## 1. User Account Management
### ✅ Linux
- [ ] Use `sudo` instead of logging in as root
- [ ] Create separate user accounts for different roles
- [ ] Set strong passwords with `passwd`
- [ ] Regularly review `/etc/passwd` and `/etc/shadow`
- [ ] Disable or remove unused accounts

### ✅ Windows
- [ ] Use Local Security Policy (`secpol.msc`) for password policies
- [ ] Create standard user accounts for daily use
- [ ] Rename default administrator account
- [ ] Disable guest account

## 2. File & Directory Permissions
### ✅ Linux
- [ ] Set restrictive permissions: `chmod 750` for sensitive directories
- [ ] Use `chown` and `chgrp` to set correct ownership
- [ ] Review sticky bit, SUID, SGID permissions
- [ ] Check `/tmp` and `/var/tmp` permissions (1777)

### ✅ Windows
- [ ] Apply NTFS permissions with principle of least privilege
- [ ] Disable inheritance where necessary
- [ ] Audit sensitive folders (Properties > Security > Advanced)

## 3. Firewall Configuration
### ✅ Linux (UFW)
- [ ] Enable UFW: `sudo ufw enable`
- [ ] Allow only necessary ports: `sudo ufw allow ssh`
- [ ] Deny all incoming by default: `sudo ufw default deny incoming`
- [ ] Check status: `sudo ufw status verbose`

### ✅ Windows Firewall
- [ ] Turn on Windows Defender Firewall
- [ ] Create inbound/outbound rules for required applications only
- [ ] Block unused ports via Advanced Settings

## 4. Services & Processes Management
### ✅ Linux
- [ ] List running services: `systemctl list-units --type=service`
- [ ] Disable unnecessary services (e.g., `bluetooth`, `cups`)
- [ ] Use `ps aux` to identify suspicious processes
- [ ] Enable `auditd` for logging

### ✅ Windows
- [ ] Review services via `services.msc`
- [ ] Disable unused services (e.g., `Remote Registry`, `Telnet`)
- [ ] Monitor Task Manager for unknown processes
- [ ] Enable Windows Event Logging

## 5. System Updates & Patches
### ✅ Linux
- [ ] Regular updates: `sudo apt update && sudo apt upgrade`
- [ ] Enable automatic security updates
- [ ] Subscribe to security mailing lists (e.g., Ubuntu Security Notices)

### ✅ Windows
- [ ] Enable Windows Update for automatic patches
- [ ] Check for updates manually via Settings
- [ ] Install driver updates from trusted sources only

## 6. Logging & Monitoring
### ✅ Linux
- [ ] Review `/var/log/` regularly
- [ ] Configure `rsyslog` or `journalctl`
- [ ] Set up log rotation
- [ ] Monitor auth logs: `/var/log/auth.log`

### ✅ Windows
- [ ] Enable Windows Event Viewer
- [ ] Configure audit policies (`auditpol`)
- [ ] Monitor Security and System logs

## 7. Network Security
### ✅ Linux
- [ ] Disable IPv6 if unused
- [ ] Configure `/etc/hosts.allow` and `/etc/hosts.deny`
- [ ] Use `netstat -tulpn` to check open ports
- [ ] Implement fail2ban for SSH protection

### ✅ Windows
- [ ] Disable SMBv1 if not needed
- [ ] Use `netstat -ano` to review connections
- [ ] Disable NetBIOS over TCP/IP if unnecessary

## 8. Additional Hardening Steps
### ✅ Both OS
- [ ] Enable disk encryption (BitLocker/LUKS)
- [ ] Configure screen lock with timeout
- [ ] Remove unnecessary software
- [ ] Implement antivirus/anti-malware (Windows Defender/ClamAV)
- [ ] Regular backups of critical data

## 9. Principle of Least Privilege (PoLP)
- [ ] Users only have access necessary for their role
- [ ] Use `sudo` for temporary elevation (Linux)
- [ ] Run services with minimal required privileges
- [ ] Separate admin and user accounts

## 10. Review & Audit
- [ ] Perform regular security audits
- [ ] Use tools like `lynis` (Linux) or `Microsoft Security Baseline Analyzer`
- [ ] Document changes and incidents
- [ ] Stay updated with CVEs and security advisories

---
## Summary
OS hardening is the process of securing an operating system by reducing its attack surface, applying patches, configuring security settings, and following best practices like least privilege and regular monitoring.

---
## References
- CIS Benchmarks: https://www.cisecurity.org/cis-benchmarks
- Microsoft Security Baselines: https://docs.microsoft.com/en-us/windows/security/
- Ubuntu Security: https://ubuntu.com/security
- NSA OS Hardening Guides