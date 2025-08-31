
#linux 

## Contents :-

#### [[#01 - Additional Information]]
#### [[#02 - SSH]]
#### [[#03 - Filesystem]]
#### [[#04 - Common Directories]]
#### [[#05 - Useful Utilities]]
#### [[#06 - Processes]]
#### [[#07 - Automation]]
#### [[#08 - Package Management]]
#### [[#09 - Linux Modules]]

---

#additional-info 

## 01 - Additional Information

- [Updog - replacement for Python's `SimpleHTTPServer`.](https://github.com/sc0tfree/updog)
- [Crontab Guru](https://crontab.guru/)
- [Crontab Generator](https://crontab-generator.org/)
- [ExploitDB](https://www.exploit-db.com/) - contains exploits that can be downloaded and used straight out of the box. If you're inclined towards the CLI on Linux, Kali comes pre-installed with a tool called "searchsploit" which allows you to search ExploitDB from your own machine. This is offline, and works using a downloaded version of the database, meaning that you already have all of the exploits already on your Kali Linux!
- [NVD](https://nvd.nist.gov/vuln/search) - keeps track of **CVEs** (***Common Vulnerabilities and Exposures***) -- whether or not there is an exploit publicly available. CVEs take the form: *CVE-YEAR-IDNUMBER*
- [CVE Mitre](https://cve.mitre.org/)
- [tr command](https://www.geeksforgeeks.org/tr-command-in-unix-linux-with-examples/)
- [tr command with examples](https://linuxize.com/post/linux-tr-command/)

---

## 02 - SSH

- **SSH** (***Secure Shell***)
- SSH allows us to remotely execute commands on another device remotely.
- Any data sent between the devices is encrypted when it is sent over a network such as the Internet.
- *SSH Syntax:* `ssh username@IP`
	1. The IP address of the remote machine
	2. Correct credentials to a valid account to login with on the remote machine

---

#file-system 

## 03 - Filesystem

- A majority of commands allow for arguments to be provided. These arguments are identified by a hyphen and a certain keyword known as flags or switches.
- Files and folders with "**.**" are hidden files.
- Use `--help` option or `man`(ual) pages for more description on commands usage

![[Linux File Commands.png]]

---

## 04 - Common Directories

### /etc

- The etc folder (short for etcetera) is a commonplace location to store system files that are used by your operating system.

### /var

- The "/var" directory, with "var" being short for variable data,  is one of the main root folders found on a Linux install. 
- This folder stores data that is frequently accessed or written by services or applications running on the system. 
- For example, log files from running services and applications are written here (**/var/log**), or other data that is not necessarily associated with a specific user (i.e., databases and the like).

### /root

- Unlike the **/home** directory, the **/root** folder is actually the home for the "root" system user.
- There isn't anything more to this folder other than just understanding that this is the home directory for the "root" user. 
- But, it is worth a mention as the logical presumption is that this user would have their data in a directory such as "**/home/root**" by default.

### /tmp

- Short for "temporary", the /tmp directory is volatile and is used to store data that is only needed to be accessed once or twice. 
- Similar to the memory on your computer, once the computer is restarted, the contents of this folder are cleared out.
- What's useful for us in pentesting is that any user can write to this folder by default. Meaning once we have access to a machine, it serves as a good place to store things like our enumeration scripts.

---

## 05 - Useful Utilities

- `nano filename`: terminal text editor
- `wget URL`: allows us to download files from the web via HTTP
- `scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt`: **SCP**(***Secure Copy***) is a means of securely copying files between two computers using the SSH protocol to provide both authentication and encryption. The IP address of the remote system:- *192.168.1.30*; User on the remote system:- *ubuntu*; Name of the file on the local system:- *important.txt*; Name that we wish to store the file as on the remote system:- *transferred.txt*
- `python3 -m  http.server`: Python3's "**HTTPServer**" will serve the files in the directory that you run the command, but this can be changed by providing options that can be found in the manual pages.

---

## 06 - Processes

- Processes are the programs that are running on your machine. 
- They are managed by the kernel, where each process will have an ID associated with it, also known as its PID. The PID increments for the order In which the process starts. I.e. the 60th process will have a PID of 60.
- `ps`: view a list of the running processes
- `ps aux`: see the processes run by other users and those that don't run from a session (i.e. system processes)
- `top`: gives real-time statistics about the processes running on the system

### 06.01 - Managing Processes

- `kill PID`: kill a process
- Some of the signals that we can send to a process when it is killed:
	- **SIGTERM** - Kill the process, but allow it to do some cleanup tasks beforehand
	- **SIGKILL** - Kill the process - doesn't do any cleanup after the fact
	- **SIGSTOP** - Stop/suspend a process

### 06.02 - How Processes Start

- The **OS** (***Operating System***) uses namespaces to ultimately split up the resources available on the computer to (such as CPU, RAM and priority) processes. 
- Processes within a namespace will have access to a certain amount of computing power, however, it will be a small portion of what is actually available to every process overall.
- Namespaces are great for security as it is a way of isolating processes from another -- only those that are in the same namespace will be able to see each other.
- The process with an ID of 0 is a process that is started when the system boots. This process is the system's init on Ubuntu, such as **systemd**, which is used to provide a way of managing a user's processes and sits in between the operating system and the user.
- Any program or piece of software that we want to start will start as what's known as a child process of **systemd**. This means that it is controlled by **systemd**, but will run as its own process (although sharing the resources from **systemd**) to make it easier for us to identify and the likes.

### 06.03 - Start Processes on Boot

- `systemctl [option] [service]`: allows us to interact with the **systemd** process/daemon. 
- 4 Options of `systemctl`:
	- Start
	- Stop
	- Enable (start service on system boot-up)
	- Disable

### 06.04 - Backgrounding & Foregrounding

- Processes can run in two states: in the background and in the foreground.
- Process can be backgrounded using either `Ctrl + Z` or the `&` operator.
- Processes such as copying files can be backgrounded while we continue with our work without having to wait for it to finish.
- `fg`: bring backgrounded process back to focus

---

## 07 - Automation

- `cron` process is used to schedule a certain action or task to take place after the system has booted.
- **Crontab** is one of the processes that is started during boot, which is responsible for facilitating and managing `cron` jobs. A crontab is simply a special file with formatting that is recognized by the `cron` process to execute each line step-by-step.
- Crontabs require 6 specific values:

|   |   |
|---|---|
|**Value**|**Description**|
|MIN|What minute to execute at|
|HOUR|What hour to execute at|
|DOM|What day of the month to execute at|
|MON|What month of the year to execute at|
|DOW|What day of the week to execute at|
|CMD|The actual command that will be executed.|

- If we do not wish to provide a value for that specific field, we simply just place an asterisk (`*`).
- `crontab -e`: edit crontab

---

## 08 - Package Management

- When developers wish to submit software to the community, they will submit it to an  "apt" repository. If approved, their programs and tools will be released into the wild.
- `add-apt-repository`: adding additional repositories
- The `apt` command is a part of the package management software also named apt. Apt contains a whole suite of tools that allows us to manage the packages and sources of our software, and to install or remove software at the same time.
- Whilst you can install software through the use of package installers such as `dpkg`, the benefits of apt means that whenever we update our system -- the repository that contains the pieces of software that we add also gets checked for updates.
- When adding software, the integrity of what we download is guaranteed by the use of what is called **GPG** (***Gnu Privacy Guard***) keys.
- Removing packages:
```
add-apt-repository --remove ppa:PPA_Name/ppa
apt remove [software-name-here]
```

---

## 09 - Linux Modules

### du

- `du`: disk usage - helps identify what files/directories are consuming how much space.
- `du --time -d 1 .`: alternate `ls` command. It won't specify you the user ownership though, so you can use `stat`command on the file you want to know who is the owner of that particular file.

|   |   |
|---|---|
|Flag|Description|
|-a|Will list files as well with the folder.|
|-h|Will list the file sizes in human readable format(B,MB,KB,GB)|
|-c|Using this flag will print the total size at the end. Jic you want to find the size of directory you were enumerating|
|-d (number)|Flag to specify the depth-ness of a directory you want to view the results for (eg. -d 2)|
|--time|To get the results with time stamp of last modified.|

### String Operations

#### tr

- Translate command (`tr`) can help in a number of ways, ranging from changing character cases in a string to replacing characters in a string.
- *Syntax:* `tr [flags] [source]/[find]/[select] [destination]/[replace]/[change]`
- `tr` command works in sets of character.

|   |   |
|---|---|
|Flags|Description|
|-d|To delete a given set of characters|
|-t|To concat source set with destination set(destination set comes first; t stands for truncate)|
|-s|To replace the source set with the destination set(s stands for squeeze)|
|-c|This is the REVERSE card in this game, for eg. If you specify -c with -d to delete a set of characters then it will delete the rest of the characters leaving the source set which we specified (c stands for complement; as in doing reverse of something)|

#### AWK

- Awk is a scripting language used for manipulating data and generating reports. The awk command programming language requires no compiling, and allows the user to use variables, numeric functions, string functions, and logical operators.
- *Syntax:* `awk [flags] [select pattern/find(sort)/commands] [input file]`
- ***Note:*** awk does support getting output via piping.
- To search for a pattern inside a file you enclose the pattern in forward slashes `/pattern/`
- 

---



