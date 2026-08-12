## Operating Systems Fundamentals

---
## Executive Summary
 Investigate Kali Linux, An operating system (OS ) is the fundamental software that manages a computer's
hardware and software resources, providing a user interface and enabling
communication between hardware and software.
Key Concepts:
- Kernel: The core of the OS that manages hardware and software resources at a
low level.
- Shell: The user interface that allows users to interact with the OS.
- Process Management: The OS manages the execution of programs (processes)
and allocates resources to them.
- Memory Management: The OS allocates and manages memory space for
running programs.
- File System: The OS organizes and manages files and directories on storage
devices
Linux i s an open - source operating system known for its speed, reliability, and efficiency. It
can run on minimal hardware resources and is highly customizable. Unlike proprietary
systems like Windows and Mac OS X, Linux is maintained by a community of developers,
making it adaptable for various applications, from embedded devices to supercomputers.
Kali Linux is a specialized distribution designed for security auditing and penetration
testing. It includes numerous tools for these tasks, but it is not intended for everyday use
like gaming or general development. As a cybersecurity professional, it’s c rucial to be
adept at navigating both the graphical user interface (GUI) and the command line in Kali
Linux.
Step 1: Command Documentation
1. Learn About the Man Page :

---

Command Description
mv Moves or renames files and directories.
chmod Modifies file permissions.
chown Changes the ownership of a file.
dd Copies data from an input to an output.
pwd Displays the name of the current directory.
ps Lists the processes currently running in the system.
su Simulates a login as another user or to become a superuser.
sudo Runs a command as a superuser or another named user.
grep Searches for specific strings of characters within a file.
ifconfig Displays or configures network card information (deprecated; use ip
address).
apt - get Installs, configures, and removes packages on Debian - based systems.
iwconfig Displays or configures wireless network card information.

<img width="970" height="508" alt="image" src="https://github.com/user-attachments/assets/4c3f9b1e-03ea-4e1a-ab9c-18bc17495055" />

---

shutdown Shuts down the computer or performs related tasks.
passwd Changes the password for the current user.
cat Lists the contents of a file.
Step 2: Create and Change Directories
In this step, you will use the cd, mkdir, and ls commands.
1. Print the Current Working Directory : pwd
2. Navigate to the /home/kali Directory : cd /home/kali
3. List Files in the Current Directory : ls - l

<img width="645" height="183" alt="image" src="https://github.com/user-attachments/assets/972c5243-26e7-4037-a9aa-127f4efc089d" />

<img width="962" height="429" alt="image" src="https://github.com/user-attachments/assets/afb17227-deee-4842-9375-eb0b9e7af851" />

---

Create a New Directory : mkdir Test and Verify the Directory Creation : ls
Remove the Directory : rmdir Test and Verify the Directory Removal : ls
Part 3: Copying and Moving Files
Copy a File : To copy a file, use the cp command. For example, to copy
gvm_admin_passwd.txt to backup_gvm_passwd.txt: cp gvm_admin_passwd.txt

<img width="887" height="419" alt="image" src="https://github.com/user-attachments/assets/39ea6f17-80f2-4ab8-97e5-fca69b5fb3d4" />

---

backup_gvm_passwd.txt
Part 4: Deleting Files
Delete a File : To delete backup_gvm_passwd.txt: rm backup_gvm_passwd.txt
Part 5: Viewing File Content
View File Contents : To view the contents of a file: cat gvm_admin_passwd.txt
Paginated Viewing : If the file is long, use less for paginated viewing: less
gvm_admin_passwd.txt

<img width="945" height="348" alt="image" src="https://github.com/user-attachments/assets/bbbc3e91-2fc4-41b4-9b0a-33bfc4ae20e7" />

<img width="940" height="551" alt="image" src="https://github.com/user-attachments/assets/b5ad9ff0-8918-4f6e-8575-b7aeb1ac227e" />

<img width="2148" height="1488" alt="Picture1" src="https://github.com/user-attachments/assets/aad8256b-4808-420e-b9b0-522f5578d51b" />

---

---

Installing Packages and Applications - Lab 2: Installing Packages and Applications
Update the Package List :
- Run the following command to update the list of available packages and their
versions: sudo apt update
- Explanation :
o The sudo command allows you to run programs with the security privileges of
another user (typically the superuser).
o apt is the command - line tool for managing packages.


<img width="967" height="572" alt="image" src="https://github.com/user-attachments/assets/4c1de1cf-c5cb-40f1-8ce7-0cf9544b77de" />



---

o update fetches the latest package information from the repositories
configured on your system. This ensures you have the most current
information about the software available for installation.
Part 2: Installing Packages
Install curl :
- Use APT to install curl , a command - line tool for transferring data with URLs:
sudo apt install curl
- Explanation :
o install tells APT to fetch the specified package and any required
dependencies from the repository and install them.
o curl is a useful tool for testing endpoints and downloading files.
<img width="975" height="741" alt="image" src="https://github.com/user-attachments/assets/4e7649d2-8e9f-43c8-a306-23caddc622e5" />
---

Verify the Installation :
- Check the version of curl to confirm the installation was successful:
curl -- version
- Explanation : This command displays the installed version of curl . If installed
correctly, it will show version information.
<img width="975" height="579" alt="image" src="https://github.com/user-attachments/assets/cdf21454-a642-445b-b8fa-1146872da240" />

---

Part 3: Upgrading Packages
Upgrade All Installed Packages :
- Run the following command to upgrade all currently installed packages to their
latest versions:
sudo apt upgrade
- Explanation : This command checks for updates to all installed packages and
upgrades them to the latest versions available in the repository.

<img width="975" height="759" alt="image" src="https://github.com/user-attachments/assets/8da6b9dd-6f1a-47c4-8ca8-44c3eab96039" />

---

Part 5: Searching for Packages
Search for Networking Packages :
- Use the APT search functionality to find packages related to networking:
apt search networking
- Explanation : This command searches the package database for any packages that
have "networking" in their name or description, displaying a list of matching
packages.
<img width="975" height="720" alt="image" src="https://github.com/user-attachments/assets/57b54925-9d33-4f78-b041-deacea6a6786" />

---

Part 6: Managing Repositories
Edit Repositories :
- Open the sources.list file to view and manage your APT repositories:
sudo nano /etc/apt/sources.list
- Explanation : This file contains a list of repositories that APT uses to fetch packages.
Using nano opens the file in a text editor.
<img width="975" height="775" alt="image" src="https://github.com/user-attachments/assets/c7db446e-3c86-4115-ae02-33a9679ff6e7" />

---

Explore Installed Packages :
- Use the following command to list all installed packages:
dpkg -- get - selections | grep - v deinstall
- Explanation : This command lists all installed packages, filtering out any that have
been marked for deinstallation.

<img width="975" height="758" alt="image" src="https://github.com/user-attachments/assets/c5050125-a225-464f-9c2d-5e74d030e28b" />

---

Lab 3: Networking Commands
Networking is a fundamental aspect of cybersecurity and system administration.
Familiarity with networking commands allows you to configure, manage, and troubleshoot
network connections effectively. Kali Linux includes a range of powerful tools for
network ing, making it an essential skill for ethical hackers and security professionals.
Part 1: Displaying Network Configuration
Open a Terminal :
- Start your Kali Linux VM.
- Open a terminal by clicking the terminal icon.
Check Network Interfaces :
<img width="975" height="666" alt="image" src="https://github.com/user-attachments/assets/69321cac-a961-4d1c-be65-ad4c11064159" />

---

- Use the following command to display the current network interfaces and their
configuration: ip addr show
List Routing Table :
- To view the routing table, run: ip route show
- Explanation : This command displays the routing table, which contains information
on how packets are routed through the network.
Part 2: Testing Network Connectivity
<img width="939" height="200" alt="image" src="https://github.com/user-attachments/assets/d66956f9-e787-40c5-bb5d-8ce5a4b89e3f" />

---

Ping a Host :
- Use the ping command to test connectivity to a remote host, such as Google: ping -
c 4 google.com
Explanation : The - c 4 option sends 4 packets. The ping command checks if the host is
reachable and measures the round - trip time for messages sent.
Trace Route to a Host :
- Use the traceroute command to see the path packets take to a destination:
traceroute google.com
- Explanation : traceroute shows the sequence of hops between your machine and
the destination, helping diagnose where delays or failures occur.
<img width="920" height="433" alt="image" src="https://github.com/user-attachments/assets/bfe94d10-eb42-4591-a4db-0eb0f565c872" />
<img width="953" height="383" alt="image" src="https://github.com/user-attachments/assets/aa5d4c8b-f49f-40df-9b4e-8c0e4482e5d6" />

---

Part 3: Configuring Network Interfaces
View Current Interface Configuration :
- Use the following command to see the current settings for your network interfaces:
ifconfig
Explanation : The ifconfig command displays the configuration of all active network
interfaces.
Manually Configure an Interface :
- To assign a static IP address to an interface (for example, eth0 ), use:
sudo ip addr add 192.168.1.20/24 dev eth0
- Explanation : This command assigns the IP address 192.168.1.20 with a subnet
mask of 255.255.255.0 to the interface eth0 .
Bring the Interface Up :
- Activate the configured interface with:
sudo ip link set eth0 up
<img width="975" height="633" alt="image" src="https://github.com/user-attachments/assets/83e1c072-6499-447d-93f5-7fa1a1f73fd5" />

---

- Explanation : This command enables the specified interface, making it active.
Part 4: Monitoring Network Traffic
Install tcpdump :
- Use the following command to install tcpdump , a powerful packet analysis tool:
sudo apt install tcpdump
Explanation : This command installs tcpdump , allowing you to capture and analyze
network traffic.
<img width="975" height="672" alt="image" src="https://github.com/user-attachments/assets/51f12fb6-0846-431d-acac-a9c222577cf4" />

---

Capture Network Traffic :
- Use tcpdump to capture packets on eth0 :
sudo tcpdump - i eth0 - c 10
Explanation : The - i option specifies the interface, and - c 10 limits the capture to 10
packets.
<img width="975" height="614" alt="image" src="https://github.com/user-attachments/assets/55c2fcef-90b8-46c1-bbf0-967abd04dfcf" />
<img width="944" height="189" alt="image" src="https://github.com/user-attachments/assets/fc5d3f1c-e959-4b54-bb2b-1c15bd815d9a" />

---

Analyze Network Traffic :
- To see live traffic, run:
sudo tcpdump - i eth0
- Explanation : This command captures and displays all traffic on eth0 in real - time.
Use Ctrl + C to stop the capture.
Part 5: Final Review
Check Network Status :
- Use the following command to see the status of all interfaces:
nmcli device status
<img width="883" height="272" alt="image" src="https://github.com/user-attachments/assets/80dfda94-b56f-4d86-b815-6f01d4ccfa79" />

---

Explanation : This command provides a summary of all network interfaces, showing their
connection status.
Check Firewall Status :
- Check if the firewall is active and what rules are in place:
sudo ufw status verbose
- Explanation : This command shows the status of the Uncomplicated Firewall (UFW)
and its rules.
<img width="886" height="164" alt="image" src="https://github.com/user-attachments/assets/c1c19fae-6f96-480e-804e-1d092a8fee83" />

# Lab 4: Linux File Permissions and Ownership
Linux employs a robust permission system that controls access to files and directories.
Understanding and managing these permissions is crucial for system security. Each file
and directory has an owner and a group associated with it, determining who can re ad,
write, or execute the file.
1. File Permissions
Linux file permissions determine who can read, write, or execute files. Permissions are
divided into three types:
- Read ( r ) : Permission to read the file.
- Write ( w ) : Permission to modify or delete the file.
- Execute ( x ) : Permission to run the file as a program.
2. User Types

---

- Owner : The user who created the file.
- Group : Users who belong to the same group as the file's group.
- Others : All other users.
3. Permission Representation
Permissions are displayed as a string of ten characters:
- Example: - rwxr - xr --
o The first character indicates the type ( - for file, d for directory).
o The next three characters are for the owner, the following three for the group,
and the last three for others.
4. Permission Codes Table
Symbol Meaning Octal Value
r Read permission 4
w Write permission 2
x Execute permission 1
- No permission 0
5. Permissions Breakdown Table
Permissions String Owner Group Others
rwxrwxrwx rwx rwx rwx
Octal Equivalent 777
Commands to Learn
- ls - l : List files with permissions.
- chmod : Change file permissions.
- chown : Change file ownership.
- chgrp : Change group ownership.

---

art 1: Viewing File Permissions
Step 1: Check Current Permissions
1. Open your terminal.
2. Create a new directory: mkdir PermissionTes t
3. Navigate into the directory: cd PermissionTest
4. Create a new file: touch testfile.txt
5. List the permissions: ls - l

<img width="886" height="500" alt="image" src="https://github.com/user-attachments/assets/79be0823-b979-4c69-9361-6171a711e794" />

What to Observe :
- Notice the output showing permissions for testfile.txt
T h e file ( testfile.txt ) has permission of - rw - r w - r — for user, gro up and othe rs.
Part 2: Modifying Permissions
Step 2: Change File Permissions
Change the permissions of testfile.txt to 777 (full permissions for everyone): chmod 777
testfile.txt
Verify the changes : ls - l

<img width="686" height="411" alt="image" src="https://github.com/user-attachments/assets/c0de0e4d-9c0c-46e5-bff6-d5ca5dfd72c7" />

Explanation :
- 777 means that the owner, group, and others all have read ( r ), write ( w ), and execute
( x ) permissions.

---

- This is useful for sharing files, but it poses security risks, as anyone can modify or
delete the file.
Step 3: Revert Permissions
Revert the permissions to 644 (owner can read/write, group and others can read): chmod
644 testfile.txt
Check permissions again : ls - l

<img width="859" height="209" alt="image" src="https://github.com/user-attachments/assets/825f8175-ed58-45da-938f-20f1e9f133f9" />

Exercise 1: Experiment with Permissions
Part 3: Changing Ownership
Step 4: Change File Ownership
Create a new user for testing (this may require sudo privileges): sudo adduser testuser
Change the ownership of testfile.txt to testuser : sudo chown testuser:testuser testfile.txt
Verify ownership: ls - l
<img width="941" height="569" alt="image" src="https://github.com/user-attachments/assets/b37d3f7d-d556-4ae3-8f47-41155a289dce" />

---

Exercise 2: Group Ownership
Change the group ownership of testfile.txt to another group (e.g., staff ): sudo chgrp staff
testfile.txt
Part 4: Practical Exercises
<img width="930" height="520" alt="image" src="https://github.com/user-attachments/assets/ee6fc67b-12dd-416f-93ac-693430e38b8d" />

---

Exercise 3: Create and Modify Permissions
- Create three new files:
touch file1.txt file2.txt file3.txt
Set permissions as follows:
- file1.txt : Full permissions for owner, read and execute for group and others ( 755 ).
- file2.txt : Read and write for the owner, read for group and others ( 644 ).
- file3.txt : Full permissions for everyone ( 777 ).
<img width="858" height="613" alt="image" src="https://github.com/user-attachments/assets/661d8933-ec55-42a4-8f80-d565320628b6" />

Lab 5: Research on Linux
Linux distributions are operating systems built upon the Linux kernel and include various
software packages, applications, and tools. They are developed by communities and
businesses, and examples include Debian, Ubuntu, Fedora, and Red Hat Enterprise
Linu x. Linux distributions come in various flavors, including desktop distributions with GUI
environments like GNOME or KDE Plasma, and server distributions with a command - line
interface, according to Zenarmor .
Popular Linux Distributions:

---

•
Ubuntu:
A popular desktop and server distribution known for its user - friendly interface and
extensive community support.
<img width="138" height="138" alt="image" src="https://github.com/user-attachments/assets/d3d2be98-ac1e-4f93-bba0-fe6fc542164f" />

•
Debian:
A stable and widely used distribution known for its strict adherence to free software
principles and extensive software repository.
<img width="138" height="138" alt="image" src="https://github.com/user-attachments/assets/c3fd3837-141d-4898-a87e-04bb8206c8d2" />

•
Fedora:
A distribution sponsored by Red Hat, often used as a testing ground for new features in Red
Hat Enterprise Linux.
<img width="138" height="138" alt="image" src="https://github.com/user-attachments/assets/2828201e-3f0b-4256-9912-381385ab993a" />

•
Linux Mint:
A community - driven distribution based on Ubuntu, offering a user - friendly experience and
excellent hardware support.
•

<img width="138" height="138" alt="image" src="https://github.com/user-attachments/assets/7b53204f-1199-4063-b2da-b36d26403b41" />

---

Red Hat Enterprise Linux:
A commercial distribution known for its reliability and enterprise - grade features.

<img width="138" height="138" alt="image" src="https://github.com/user-attachments/assets/bcfba0f4-ad8c-425f-b74e-9e854d7ee07b" />

•
CentOS:
A community - driven distribution based on Red Hat Enterprise Linux, offering a free
alternative.

<img width="138" height="138" alt="image" src="https://github.com/user-attachments/assets/078474f4-5ae7-480b-95ce-53e022f31fc0" />

•
Manjaro:
A distribution based on Arch Linux, known for its rolling release model and user - friendly
installation process.

<img width="138" height="138" alt="image" src="https://github.com/user-attachments/assets/9270ab09-ac2c-4102-835b-db7831187d95" />

- Arch Linux:
A distribution designed for experienced Linux users, offering a high degree of customization
but requiring more technical knowledge.
•
Kali Linux:
A Linux distribution specialized for penetration testing and security auditing.

<img width="138" height="138" alt="image" src="https://github.com/user-attachments/assets/0f0274b1-88b8-4e46-917c-3984c1578a81" />

•
Elementary OS:
A distribution based on Ubuntu, designed with usability and a minimalist look in mind.

<img width="138" height="138" alt="image" src="https://github.com/user-attachments/assets/467150ac-58d6-4495-94df-f754460f8e07" />

---

•
Zorin OS:
A distribution based on Ubuntu, offering a familiar Windows - like interface for new Linux
users.

<img width="138" height="138" alt="image" src="https://github.com/user-attachments/assets/ce79cad0-b8be-4d4e-967a-500763f6c34c" />

•
Slackware:
One of the oldest and most traditional Linux distributions, known for its command - line
focus.

<img width="138" height="138" alt="image" src="https://github.com/user-attachments/assets/6871c9d8-adbd-4c94-befe-8a7ecf047b72" />

•
MX Linux:
A Debian - based distribution that balances performance and ease of use.

<img width="138" height="138" alt="image" src="https://github.com/user-attachments/assets/c8045725-f1de-471e-9cff-bef0ef5655d1" />

•
Linux Lite:
A lightweight distribution based on Ubuntu LTS, designed for older hardware.

<img width="138" height="138" alt="image" src="https://github.com/user-attachments/assets/0202cbd3-655a-4271-ba2f-e4cf3a9c3ec9" />

•
Lubuntu:

<img width="138" height="138" alt="image" src="https://github.com/user-attachments/assets/552638ae-6eb3-4c8d-ae46-730480789b10" />

---

A lightweight distribution based on Ubuntu and LXQT, offering a minimal resource
footprint.
Key Features of Linux Distributions:
- Customization:
Many distributions offer a wide range of customization options, allowing users to tailor their
operating system to their needs.
- Community Support:
Strong community support is a hallmark of many Linux distributions, providing users with
resources and assistance.
- Free and Open - Source Software:
Linux distributions are typically based on free and open - source software, meaning they are
freely distributable and can be modified by users.
- Variety of Desktop Environments:
Distributions often come with a variety of desktop environments, such as GNOME, KDE
Plasma, XFCE, and others, offering different user interfaces.
- Security and Privacy:
Some distributions prioritize security and privacy, offering features like built - in drive
encryption and robust authentication.
Choosing a Linux Distribution:
When selecting a Linux distribution, consider factors like:
- Your technical expertise:
Some distributions are easier to install and use than others, catering to beginners and
experienced users alike.
- Your hardware:
Some distributions are designed for older hardware, while others are optimized for newer
systems.
- Your software needs:
Determine which software you need to use and whether the distribution supports it.

---


