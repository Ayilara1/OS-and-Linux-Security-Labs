# 👤 Linux User Management and File Permissions Lab

![Linux](https://img.shields.io/badge/Linux-Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-Scripting-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white)
![User Management](https://img.shields.io/badge/User-Management-blue?style=for-the-badge)
![Permissions](https://img.shields.io/badge/File-Permissions-red?style=for-the-badge)

---

# 📖 Overview

This lab focuses on Linux user account management and file permission administration. The exercises demonstrate how to create and verify user accounts, assign file ownership, and configure file permissions using standard Linux administration commands.

These are fundamental system administration skills used by Linux Administrators, SOC Analysts, and Security Engineers to secure operating systems and enforce access control.

---

# 🎯 Objectives

- Create and manage Linux user accounts
- Verify user account information
- Understand Linux file ownership
- Modify file permissions
- Assign ownership to users and groups
- Apply the Principle of Least Privilege

---

# 🖥️ Lab Environment

| Component | Details |
|-----------|---------|
| Operating System | Kali Linux / Ubuntu |
| Shell | Bash |
| Commands Used | adduser, id, chmod, chown, ls |

---

# Lab 1 – User Management

## Objective

Create and verify a new Linux user account.

### Create a New User

```bash
sudo adduser student1
```

This command creates a new user named **student1**, along with its home directory and default configuration files.

---

### Verify User Information

```bash
id student1
```

Example Output

```text
uid=1001(student1)
gid=1001(student1)
groups=1001(student1)
```

### Result

- User account created successfully.
- Unique User ID (UID) assigned.
- Primary Group ID (GID) created.
- Home directory generated automatically.

---

# Lab 2 – File and Directory Permissions

## Objective

Manage Linux file permissions and ownership.

---

## Create a File

```bash
touch manage.txt
```

---

## View File Permissions

```bash
ls -l manage.txt
```

Example Output

```text
-rw-r--r-- 1 kali kali 0 Dec 8 10:25 manage.txt
```

---

## Modify File Permissions

```bash
chmod 755 manage.txt
```

Permission Breakdown

| User | Permission |
|------|------------|
| Owner | Read, Write, Execute |
| Group | Read, Execute |
| Others | Read, Execute |

Equivalent Permission

```text
rwxr-xr-x
```

---

## Change File or Directory Ownership

General Syntax

```bash
sudo chown owner:group directory_name
```

Example

```bash
sudo chown student1:students project
```

This command changes:

- Owner → **student1**
- Group → **students**

---

## Verify Ownership

```bash
ls -l
```

Example Output

```text
drwxr-xr-x 2 student1 students 4096 Dec 8 10:40 project
```

---

# Security Concepts Demonstrated

- Linux User Management
- User Identification (UID/GID)
- File Ownership
- File Permissions
- Access Control
- Principle of Least Privilege
- Linux System Administration

---

# Commands Used

```bash
sudo adduser student1

id student1

touch manage.txt

ls -l manage.txt

chmod 755 manage.txt

sudo chown student1:students project
```

---

# Key Takeaways

- Successfully created and verified a Linux user account.
- Applied file permission settings using `chmod`.
- Assigned ownership to users and groups with `chown`.
- Verified file permissions and ownership using `ls -l`.
- Reinforced the importance of proper access control in securing Linux systems.

---

# Skills Demonstrated

- Linux Administration
- User Management
- File Permission Management
- Access Control
- Command-Line Operations
- System Security Fundamentals

---

# Conclusion

This lab provided hands-on experience with Linux user administration and permission management. Proper configuration of user accounts, ownership, and file permissions is essential for maintaining secure Linux environments and enforcing least-privilege access. These foundational skills are critical for system administrators, SOC analysts, and cybersecurity professionals.

---

## 👨‍💻 Author

**Ayilara Busari Dare**

Electrical Engineer | Cybersecurity Analyst | Linux Security Enthusiast | SOC Analyst
