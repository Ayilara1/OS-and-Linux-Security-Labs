# 🛡️ Strengthening System Security on Linux Servers

![Linux](https://img.shields.io/badge/Linux-Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-Scripting-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white)
![Linux Security](https://img.shields.io/badge/Linux-Security-red?style=for-the-badge)
![ACL](https://img.shields.io/badge/Access-Control-blue?style=for-the-badge)

---

# 📖 Overview

This lab demonstrates practical techniques for strengthening Linux server security through user management, access control, privilege management, SSH hardening, system auditing, and security monitoring.

The exercises simulate common administrative tasks performed by Linux system administrators, SOC analysts, and security engineers to improve the confidentiality, integrity, and availability of Linux systems.

---

# 🎯 Objectives

- Secure Linux user account creation
- Configure secure default account settings
- Implement Access Control Lists (ACLs)
- Configure least-privilege sudo access
- Secure SSH remote access
- Manage Linux network services
- Configure password policies
- Implement multi-factor authentication (MFA)
- Configure Linux auditing using auditd

---

# 🖥️ Lab Environment

| Component | Details |
|-----------|---------|
| Operating System | Kali Linux / Ubuntu |
| Shell | Bash |
| Authentication | Google Authenticator |
| SSH | OpenSSH |
| Auditing | auditd |
| ACL Tool | setfacl / getfacl |

---

# Exercise 1 – Configuring adduser.conf

## Objective

Review and customize the default configuration used when creating new Linux user accounts.

## Commands Used

```bash
sudo nano /etc/adduser.conf
```

## Configuration Changes

| Parameter | New Value | Purpose |
|-----------|-----------|---------|
| DHOME | /mnt/users | Default home directory |
| FIRST_UID | 2000 | Starting UID |
| LAST_UID | 2999 | Ending UID |
| FIRST_GID | 3000 | Starting Group ID |
| LAST_GID | 3999 | Ending Group ID |
| USERGROUPS | no | Disable user-specific groups |
| DSHELL | /bin/sh | Default login shell |

---

## Custom Skeleton File

```bash
echo "Welcome to your new account!" | sudo tee /etc/skel/welcome.txt
```

This automatically places a welcome file inside every newly created user's home directory.

---

# Verification

A new account was created.

```bash
sudo adduser testuser
```

Verification commands:

```bash
ls /mnt/users/testuser

grep testuser /etc/passwd
```

### Results

- Home directory created successfully.
- UID/GID assigned from the configured ranges.
- Default shell changed successfully.
- welcome.txt copied automatically.

---

# Exercise 2 – Access Control Lists (ACL)

## Objective

Implement fine-grained file permissions for multiple users.

---

## Project Setup

```bash
sudo mkdir /projects/team_project

sudo touch /projects/team_project/file1.txt

sudo touch /projects/team_project/file2.txt
```

Ownership

```bash
sudo chown -R root:developers /projects/team_project
```

Permissions

```bash
sudo chmod 770 /projects/team_project
```

---

## User Permissions

| User | Permission |
|-------|------------|
| Alice | Read, Write, Execute |
| Bob | Read and Execute |
| Charlie | Read and Write |

Commands:

```bash
sudo setfacl -m u:alice:rwx /projects/team_project

sudo setfacl -m u:bob:rx /projects/team_project

sudo setfacl -m u:charlie:rw /projects/team_project
```

Sticky Bit

```bash
sudo chmod +t /projects/team_project
```

Display ACL

```bash
getfacl /projects/team_project
```

---

## Testing

### Alice

Successfully created and modified files.

### Bob

Successfully viewed files but could not modify them.

### Charlie

Successfully edited files but could not delete them due to the sticky bit.

---

# Exercise 3 – Sudo Privilege Management

## User Creation

```bash
sudo useradd -m john

sudo useradd -m mary

sudo useradd -m paul
```

---

## Privilege Assignment

### John

Full administrative privileges.

```bash
sudo usermod -aG sudo john
```

Verification

```bash
sudo whoami
```

Output

```text
root
```

---

### Mary

Restricted to package management.

```text
mary ALL=(ALL) NOPASSWD:
/usr/bin/apt update,
/usr/bin/apt upgrade
```

---

### Paul

Allowed to restart Apache and MySQL services only.

```text
paul ALL=(ALL) NOPASSWD:
/bin/systemctl restart apache2,
/bin/systemctl restart mysql
```

---

# Removing Sudo Access

List sudo users

```bash
getent group sudo
```

Remove user

```bash
sudo deluser username sudo
```

---

# Exercise 4 – Network Service Hardening

Open ports

```bash
sudo ss -tuln
```

Disable unnecessary services

```bash
sudo systemctl stop apache2

sudo systemctl disable apache2
```

---

# Exercise 5 – SSH Hardening

Changed SSH port

```
22 → 2222
```

Restart service

```bash
sudo systemctl restart ssh
```

Configured

- Public Key Authentication
- Disabled password authentication
- Disabled root login

SSH key generation

```bash
ssh-keygen -t rsa -b 4096
```

Copy key

```bash
ssh-copy-id kali@192.168.92.30
```

---

# Exercise 6 – Password Policy

File

```bash
/etc/login.defs
```

| Setting | Value |
|----------|------|
| PASS_MAX_DAYS | 90 |
| PASS_MIN_DAYS | 7 |
| PASS_WARN_AGE | 14 |

Verification

```bash
sudo chage -l testuser
```

---

# Exercise 7 – Two-Factor Authentication

Google Authenticator was configured for user authentication.

Security improvements:

- Password protection
- Time-based One-Time Password (TOTP)
- Multi-factor authentication

---

# Exercise 8 – System Auditing

Installed auditd

```bash
sudo apt install auditd
```

Enabled

```bash
sudo systemctl enable auditd
```

Audit Rules

Monitor logins

```text
-w /var/log/auth.log -p wa -k user-logins
```

Monitor passwd

```text
-w /etc/passwd -p wa -k passwd-modifications
```

Restart

```bash
sudo service auditd restart
```

Search logs

```bash
sudo ausearch -k user-logins

sudo ausearch -k passwd-modifications
```

---

# Skills Demonstrated

- Linux Administration
- User Management
- Access Control Lists
- Sudo Administration
- SSH Hardening
- MFA Deployment
- Password Policy Management
- Linux Auditing
- System Hardening
- Network Security

---

# Security Impact

This lab demonstrates several industry best practices:

- Principle of Least Privilege
- Defense in Depth
- Secure Remote Administration
- Strong Authentication
- System Monitoring
- Audit Logging
- Access Control
- Secure Configuration Management

---

# Lessons Learned

This exercise reinforced the importance of securing Linux systems through proper user management, least-privilege access, secure authentication, auditing, and proactive system hardening. These controls reduce the attack surface and improve an organization's ability to detect and respond to security incidents.

---

## 👨‍💻 Author

**Ayilara Busari Dare**

Cybersecurity Analyst | SOC Analyst | Linux Security Enthusiast
