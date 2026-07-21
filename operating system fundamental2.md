# 🐧 Linux Operating System Fundamentals & Bash Scripting Labs

![Linux](https://img.shields.io/badge/Linux-Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-Scripting-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white)
![Shell](https://img.shields.io/badge/Shell-Automation-blue?style=for-the-badge)
![Cybersecurity](https://img.shields.io/badge/Cybersecurity-Linux%20Administration-red?style=for-the-badge)

---

# 📖 Overview

This project was completed as part of the **Cybersecurity and Ethical Hacking Internship** at the **International Cybersecurity and Digital Forensic Academy**.

The objective was to develop practical Linux administration skills through Bash scripting, file management, directory automation, permission management, and backup automation.

---

# 🎯 Learning Objectives

Upon completing these labs, I was able to:

- Write Bash scripts
- Use variables and conditional statements
- Create loops for automation
- Accept user input
- Automate file management
- Navigate Linux directories programmatically
- Manage file permissions
- Configure Access Control Lists (ACLs)
- Automate backups
- Handle scripting errors

---

# 🖥️ Lab Environment

| Component | Details |
|-----------|---------|
| Operating System | Ubuntu Linux |
| Shell | Bash |
| Editor | Nano |
| Terminal | Linux Terminal |
| Archive Tool | tar |
| Permission Tools | chmod, chown, setfacl |

---

# 📂 Lab 1 – Introduction to Bash Scripting

## Objective

Learn the fundamentals of Bash scripting.

---

## Task 1 – Hello World Script

### Script

```bash
#!/bin/bash

echo "Hello, World!"
```

### Result

Successfully created and executed the first Bash script.

---

## Task 2 – Variables

### Script

```bash
#!/bin/bash

name="Ayilara"

echo "Hello, $name!"
```

### Result

Verified that variables can store and display values dynamically.

---

## Task 3 – Conditional Statements

### Script

```bash
#!/bin/bash

read -p "Enter your age: " age

if [ "$age" -ge 18 ]; then
    echo "You are an adult."
else
    echo "You are a minor."
fi
```

### Result

Implemented decision-making using `if-else`.

---

## Task 4 – Loops

### For Loop

```bash
for i in {1..5}
do
    echo "Iteration $i"
done
```

### While Loop

```bash
count=1

while [ $count -le 5 ]
do
    echo "Loop $count"
    ((count++))
done
```

### Result

Successfully automated repetitive tasks.

---

# 📂 Lab 2 – Linux Command Automation

## Objective

Automate directory navigation and file operations.

---

## Activities

- Directory navigation
- File creation
- File movement
- File copying
- File deletion
- Recursive traversal
- Error handling
- Cleanup automation
- Backup creation

---

## Sample Script

```bash
#!/bin/bash

cd /home

pwd

ls -la
```

---

## Skills Demonstrated

- Directory management
- File automation
- Error handling
- Backup scripting

---

# 📂 Lab 3 – Linux Permissions & Access Control

## Objective

Automate Linux permission management.

---

## Topics Covered

- chmod
- chown
- ACL
- Recursive permissions
- Ownership management
- Backup preservation

---

## Example

```bash
chmod -R 755 /home/labdir
```

---

## ACL Example

```bash
setfacl -m u:john:r /home/labfile.txt
```

---

# 📊 Skills Acquired

- Linux Administration
- Bash Scripting
- File System Management
- Permission Management
- Access Control Lists
- Backup Automation
- Shell Automation
- Error Handling

---

# 🔐 Cybersecurity Relevance

These labs demonstrate foundational Linux administration skills essential for cybersecurity roles, including:

- SOC Analyst
- Blue Team Operations
- Linux System Administration
- DevSecOps
- Cloud Security
- Penetration Testing
- Incident Response

Understanding Bash scripting enables security professionals to automate log analysis, perform system audits, and streamline incident response workflows.

---

# 🧠 Lessons Learned

- Bash scripting significantly improves operational efficiency.
- Automation reduces manual errors and increases consistency.
- Linux permissions and ACLs are critical for securing systems.
- Backup automation is an important component of disaster recovery.
- Error handling improves script reliability.

---

# 📚 Key Linux Commands Used

| Command | Purpose |
|----------|---------|
| `chmod` | Change file permissions |
| `chown` | Change file ownership |
| `setfacl` | Manage Access Control Lists |
| `getfacl` | View ACLs |
| `tar` | Archive files |
| `find` | Search files |
| `mkdir` | Create directories |
| `rmdir` | Remove directories |
| `touch` | Create files |
| `cp` | Copy files |
| `mv` | Move files |
| `rm` | Delete files |
| `pwd` | Print working directory |
| `ls` | List directory contents |

---

# 🏆 Outcome

This project strengthened my practical Linux administration skills and improved my ability to automate system management tasks using Bash scripting. The knowledge gained forms a solid foundation for SOC operations, incident response, DevSecOps, and Linux server administration.

---

## 👨‍💻 Author

**Ayilara Busari Dare**

Cybersecurity Analyst | SOC Analyst | Linux Enthusiast | DevSecOps Learner
