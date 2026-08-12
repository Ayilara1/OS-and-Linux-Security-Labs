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
<img width="953" height="345" alt="image" src="https://github.com/user-attachments/assets/6c4e56d6-00c6-4680-afac-10c29663155f" />
<img width="975" height="569" alt="image" src="https://github.com/user-attachments/assets/c84428fd-4353-4a25-8b37-5432dd9e3ef7" />
<img width="975" height="397" alt="image" src="https://github.com/user-attachments/assets/c1adff62-e2a8-45da-a332-a64910521b8a" />
<img width="964" height="323" alt="image" src="https://github.com/user-attachments/assets/80a615f9-06f6-4c2b-9b9f-34814f0e23b9" />
<img width="973" height="322" alt="image" src="https://github.com/user-attachments/assets/31e35a35-2a5b-4b61-9be5-476ec6596a1c" />

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
<img width="880" height="350" alt="image" src="https://github.com/user-attachments/assets/8d874d0a-b98d-448d-a775-0a6d3cd52380" />
<img width="861" height="236" alt="image" src="https://github.com/user-attachments/assets/da1b2e00-7077-4eda-9a7d-37f0c0c4dd13" />
<img width="795" height="491" alt="image" src="https://github.com/user-attachments/assets/aeb6f448-9799-4216-9272-e0026318e462" />
<img width="873" height="423" alt="image" src="https://github.com/user-attachments/assets/93149299-b189-48af-b838-e7870106ca9d" />
<img width="928" height="219" alt="image" src="https://github.com/user-attachments/assets/9a9827ba-3b57-46aa-b9ff-79b7116db419" />
<img width="852" height="208" alt="image" src="https://github.com/user-attachments/assets/25c5d04e-3d39-4a47-8bd9-6ff271b0a862" />
<img width="913" height="197" alt="image" src="https://github.com/user-attachments/assets/9b27bd2d-aab1-48db-944b-e35996a56be9" />
<img width="975" height="497" alt="image" src="https://github.com/user-attachments/assets/ae941f2e-b9c4-438b-b259-87c3b23b2c00" />

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
<img width="975" height="450" alt="image" src="https://github.com/user-attachments/assets/ef5bbde8-aa2a-43f6-9156-43cf9d34b869" />
<img width="975" height="603" alt="image" src="https://github.com/user-attachments/assets/688fb22d-cbd8-4367-96c8-450d7744d017" />
<img width="975" height="710" alt="image" src="https://github.com/user-attachments/assets/972d2f5c-9da4-4552-a0ff-0579168e801b" />
<img width="975" height="364" alt="image" src="https://github.com/user-attachments/assets/87d13e2c-c9b3-46d1-91ad-4c60f9fefaef" />


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
<img width="975" height="652" alt="image" src="https://github.com/user-attachments/assets/291c345d-bba8-4c16-9140-b59b0903815e" />
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
<img width="975" height="392" alt="image" src="https://github.com/user-attachments/assets/f7ab3802-d862-4158-8b48-a3439928a75d" />

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
<img width="958" height="428" alt="image" src="https://github.com/user-attachments/assets/74f062bf-cebd-4541-b1ab-8d1a85796821" />
<img width="975" height="757" alt="image" src="https://github.com/user-attachments/assets/ca66f1fa-c430-4948-8d2b-2b988b1e6984" />
<img width="975" height="1235" alt="image" src="https://github.com/user-attachments/assets/ea17e3a3-acd7-4085-8c28-d2f1d53fec86" />
<img width="975" height="454" alt="image" src="https://github.com/user-attachments/assets/586a5b6e-481b-4ac1-a073-f148ca560a09" />
<img width="975" height="407" alt="image" src="https://github.com/user-attachments/assets/da5fefaa-14db-4ffa-a082-e3d8bbb65b21" />

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
<img width="975" height="630" alt="image" src="https://github.com/user-attachments/assets/a17aeeef-f26c-4ff0-97d8-5ca7d5d1d4f3" />
<img width="975" height="767" alt="image" src="https://github.com/user-attachments/assets/0d71a680-e4f2-40e7-b798-84c97fae8547" />


# Exercise 7 – Two-Factor Authentication

Google Authenticator was configured for user authentication.

Security improvements:

- Password protection
- Time-based One-Time Password (TOTP)
- Multi-factor authentication

---
<img width="975" height="757" alt="image" src="https://github.com/user-attachments/assets/9475c08f-18cc-4fe8-bf56-3bef91a0f489" />

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
<img width="975" height="729" alt="image" src="https://github.com/user-attachments/assets/8d8e45a8-7a5d-4514-a5a5-189d732a7af7" />

<img width="975" height="736" alt="image" src="https://github.com/user-attachments/assets/5526d4da-c3aa-4978-ba98-7f446603619f" />


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
