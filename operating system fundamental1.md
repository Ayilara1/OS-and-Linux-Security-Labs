## International Cybersecurity and Digital Forensic
## Academy
## PROGRAMME: CYBERSECURITY AND ETHICAL
## HACKING INTERNSHIP
## ASSIGNMENT
## PRESENTED BY
## AYILARA BUSARI DARE
## IDEAS/24/28133
## COURSE CODE: INT30 1
## COURSE TITLE: Operating Systems Fundamentals

---

INT301: Operating Systems Fundamentals – Week 1 Labs : Investigate Kali Linux
An operating system (OS ) is the fundamental software that manages a computer's
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

---

shutdown Shuts down the computer or performs related tasks.
passwd Changes the password for the current user.
cat Lists the contents of a file.
Step 2: Create and Change Directories
In this step, you will use the cd, mkdir, and ls commands.
1. Print the Current Working Directory : pwd
2. Navigate to the /home/kali Directory : cd /home/kali
3. List Files in the Current Directory : ls - l

---

Create a New Directory : mkdir Test and Verify the Directory Creation : ls
Remove the Directory : rmdir Test and Verify the Directory Removal : ls
Part 3: Copying and Moving Files
Copy a File : To copy a file, use the cp command. For example, to copy
gvm_admin_passwd.txt to backup_gvm_passwd.txt: cp gvm_admin_passwd.txt

---

backup_gvm_passwd.txt
Part 4: Deleting Files
Delete a File : To delete backup_gvm_passwd.txt: rm backup_gvm_passwd.txt
Part 5: Viewing File Content
View File Contents : To view the contents of a file: cat gvm_admin_passwd.txt
Paginated Viewing : If the file is long, use less for paginated viewing: less
gvm_admin_passwd.txt

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

---

Verify the Installation :
- Check the version of curl to confirm the installation was successful:
curl -- version
- Explanation : This command displays the installed version of curl . If installed
correctly, it will show version information.

---

Part 3: Upgrading Packages
Upgrade All Installed Packages :
- Run the following command to upgrade all currently installed packages to their
latest versions:
sudo apt upgrade
- Explanation : This command checks for updates to all installed packages and
upgrades them to the latest versions available in the repository.

---

Part 5: Searching for Packages
Search for Networking Packages :
- Use the APT search functionality to find packages related to networking:
apt search networking
- Explanation : This command searches the package database for any packages that
have "networking" in their name or description, displaying a list of matching
packages.

---

Part 6: Managing Repositories
Edit Repositories :
- Open the sources.list file to view and manage your APT repositories:
sudo nano /etc/apt/sources.list
- Explanation : This file contains a list of repositories that APT uses to fetch packages.
Using nano opens the file in a text editor.

---

Explore Installed Packages :
- Use the following command to list all installed packages:
dpkg -- get - selections | grep - v deinstall
- Explanation : This command lists all installed packages, filtering out any that have
been marked for deinstallation.

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

---

- Use the following command to display the current network interfaces and their
configuration: ip addr show
List Routing Table :
- To view the routing table, run: ip route show
- Explanation : This command displays the routing table, which contains information
on how packets are routed through the network.
Part 2: Testing Network Connectivity

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

---

- Explanation : This command enables the specified interface, making it active.
Part 4: Monitoring Network Traffic
Install tcpdump :
- Use the following command to install tcpdump , a powerful packet analysis tool:
sudo apt install tcpdump
Explanation : This command installs tcpdump , allowing you to capture and analyze
network traffic.

---

Capture Network Traffic :
- Use tcpdump to capture packets on eth0 :
sudo tcpdump - i eth0 - c 10
Explanation : The - i option specifies the interface, and - c 10 limits the capture to 10
packets.

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

---

Explanation : This command provides a summary of all network interfaces, showing their
connection status.
Check Firewall Status :
- Check if the firewall is active and what rules are in place:
sudo ufw status verbose
- Explanation : This command shows the status of the Uncomplicated Firewall (UFW)
and its rules.
Lab 4: Linux File Permissions and Ownership
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
What to Observe :
- Notice the output showing permissions for testfile.txt
T h e file ( testfile.txt ) has permission of - rw - r w - r — for user, gro up and othe rs.
Part 2: Modifying Permissions
Step 2: Change File Permissions
Change the permissions of testfile.txt to 777 (full permissions for everyone): chmod 777
testfile.txt
Verify the changes : ls - l
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
Exercise 1: Experiment with Permissions
Part 3: Changing Ownership
Step 4: Change File Ownership
Create a new user for testing (this may require sudo privileges): sudo adduser testuser
Change the ownership of testfile.txt to testuser : sudo chown testuser:testuser testfile.txt
Verify ownership: ls - l

---

Exercise 2: Group Ownership
Change the group ownership of testfile.txt to another group (e.g., staff ): sudo chgrp staff
testfile.txt
Part 4: Practical Exercises

---

Exercise 3: Create and Modify Permissions
- Create three new files:
touch file1.txt file2.txt file3.txt
Set permissions as follows:
- file1.txt : Full permissions for owner, read and execute for group and others ( 755 ).
- file2.txt : Read and write for the owner, read for group and others ( 644 ).
- file3.txt : Full permissions for everyone ( 777 ).
Lab 5: Individual Research on Linux
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
•
Debian:
A stable and widely used distribution known for its strict adherence to free software
principles and extensive software repository.
•
Fedora:
A distribution sponsored by Red Hat, often used as a testing ground for new features in Red
Hat Enterprise Linux.
•
Linux Mint:
A community - driven distribution based on Ubuntu, offering a user - friendly experience and
excellent hardware support.
•

---

Red Hat Enterprise Linux:
A commercial distribution known for its reliability and enterprise - grade features.
•
CentOS:
A community - driven distribution based on Red Hat Enterprise Linux, offering a free
alternative.
•
Manjaro:
A distribution based on Arch Linux, known for its rolling release model and user - friendly
installation process.
- Arch Linux:
A distribution designed for experienced Linux users, offering a high degree of customization
but requiring more technical knowledge.
•
Kali Linux:
A Linux distribution specialized for penetration testing and security auditing.
•
Elementary OS:
A distribution based on Ubuntu, designed with usability and a minimalist look in mind.

---

•
Zorin OS:
A distribution based on Ubuntu, offering a familiar Windows - like interface for new Linux
users.
•
Slackware:
One of the oldest and most traditional Linux distributions, known for its command - line
focus.
•
MX Linux:
A Debian - based distribution that balances performance and ease of use.
•
Linux Lite:
A lightweight distribution based on Ubuntu LTS, designed for older hardware.
•
Lubuntu:

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

- Your preferences:
Consider factors like desktop environment, customization options, and community
support when choosing a distribution.
Exercise 4: Ownership Challenge
Create a directory named Project and set your current user as the owner:
mkdir Project
sudo chown $USER : $USER Project
Verify the ownership: ls - ld Project
