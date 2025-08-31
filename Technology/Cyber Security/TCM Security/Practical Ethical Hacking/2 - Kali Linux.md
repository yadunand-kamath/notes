
#linux 

## Contents :-

#### [[#2.01 - Basics]]
#### [[#2.02 - File System]]
#### [[#2.03 - Users and Privileges]]
#### [[#2.04 - Network Commands]]
#### [[#2.05 - Starting and Stopping Services]]
#### [[#2.06 - Updating Tools]]
#### [[#2.07 - Bash Scripting]]

---

## 2.01 - Basics

* Kali Linux is a specialized ==Debian-based== Linux distribution designed for *digital forensics*, *penetration testing*, and *ethical hacking* purposes.
* It provides a comprehensive set of pre-installed tools and software packages specifically tailored for various security testing and hacking purposes.

---

#file-system

## 2.02 - File System

* use TAB to auto-complete

- `kali@kali) - [~]`: value before '@' is username; value before '@' is is hostname; value inside square brackets represents current working directory.
- `sudo`: (superuser do) allows a user with appropriate privileges to execute commands as a superuser or another user.
- `sudo su -`: (switch user) switch to root user
- `pwd`: prints working directory
- `ls -la`: lists hidden files & directories along with normal files
- `cd ..`: go to the parent directory
- `man [command_name]`: manual page for a command
- `[command_name] --help`: help page for a command
- `updatedb`: updates database
- `locate [file_name]`: locates file

### Creating/Editing/Viewing Files

- `touch file.txt`: create new file
- `nano file.txt`: create/edit file
- `mousepad file.txt`: opens file in Mousepad editor
- `cat file.txt`: prints file contents on terminal
- `>`: redirection operator, overwrites a file
- `>>`: appends a file

---

#file-system 

## 2.03 - Users and Privileges

- `[d (or) -][rwx][r--][r--]`: *First Square Bracket* - `d` = directory, `-` = file; *Second Square Bracket* - read, write, execute permissions for owner; *Third Square Bracket* - read permissions for groups; *Fourth Square Bracket* - read permissions for other users.
- `chmod +rwx file.txt (or) chmod 777 file.txt`: change mode of permissions for a file.

![[filemode-notations.png]]

- `sudo adduser username`: add new user
- `sudo -l`: lists the commands a user is allowed to run with `sudo` privileges.

### Important Files 

#files 

- `/etc/passwd`
- `/etc/shadow`
- `/etc/sudoers` - contains configuration information for the `sudo` command.

---

#network 

## 2.04 - Network Commands

- `ip a (or) ifconfig`: IP address, MAC address and other details
- `iwconfig`: wireless interface details
- `ip n (or) arp -a`: displays Neighbor table/ARP cache which contains IP-to-MAC address mappings for devices in the local network
- `ip r (or) route`: displays IP routing table
- `ping [IP address]`: check if a machine is active/alive. Sends ICMP echo requests to a specified IP address to check network connectivity and measure round-trip time.
- `netstat`: check for active/open ports and services

---

## 2.05 - Starting and Stopping Services

- `service servicename start (or) service servicename stop`: starts/stops a service
- `systemctl enable service (or) systemctl disable service`: enables/disables a service automatically when system is booted
- `/var/www/html`: stores files that can be hosted
- `python -m http.server 80` : starts and hosts a simple HTTP server using Python on port 80
- `sudo service apache2 start`: starts the Apache web server service
- `sudo systemctl enable ssh`: enables the SSH (Secure Shell) service to start automatically on system boot

---

## 2.06 - Updating Tools

- Install packages into `/opt` directory	
- Updating packages can break Kali. Instead use [PimpMyKali]([Dewalt-arch/pimpmykali: Kali Linux Fixes for Newly Imported VM's (github.com)](https://github.com/Dewalt-arch/pimpmykali)) tool:
	`sudo git clone https://github.com/Dewalt-arch/pimpmykali.git`
- `sudo apt update && sudo apt upgrade`: updates the package lists and upgrades installed packages on a Debian-based Linux system using the APT package manager
- `sudo apt install packagename`: installs a package using APT
- `git clone gitrepourl.git`: clones a Git repository from the specified URL using the Git version control system and creates a local copy of the repository's files and version history

---

#bash

## 2.07 - Bash Scripting

- helps automate tasks
- `grep`: used for filtering output based on patterns
- `cut`: remove sections from each line of files
- `tr`: translate or delete characters

### Bash Script for IP Sweeping (ipsweep.sh)

```
#!/bin/bash 
if [ "$1" == "" ] 
then echo "You forgot an IP address!" 
echo "Syntax: ./ipsweep.sh 192.168.1"  
else 
for ip in `seq 1 254`; 
do 
ping -c 1 $1.$ip | grep "64 bytes" | 
cut -d " " -f 4 | tr -d ":" & 
done 
fi
```


- `./ipsweep.sh 192.168.54 > ips.txt`: run file against IP and store results in a text file
- `for ip in $(cat ips.txt); do nmap $ip & done`

---

#additional-info 

## Additional Information

- [Get explanations for commands](https://explainshell.com/)	

---