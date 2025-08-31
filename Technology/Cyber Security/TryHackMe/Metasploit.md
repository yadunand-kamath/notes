
#metasploit

## Contents :-

#### [[#01 - Intro to Metasploit]]
#### [[#02 - Main Components]]
#### [[#03 - msfconsole]]

---

## 01 - Intro to Metasploit

- Metasploit is the most widely used exploitation framework. 
- It is a powerful tool that can support all phases of a penetration testing engagement, from information gathering to post-exploitation.
- Metasploit has two main versions:
	1. **Metasploit Pro** - The commercial version that facilitates the automation and management of tasks. This version has a graphical user interface (GUI).
	2. **Metasploit Framework** - The open-source version that works from the command line. 
- The Metasploit Framework is a set of tools that allow information gathering, scanning, exploitation, exploit development, post-exploitation, and more. While the primary usage of the Metasploit Framework focuses on the penetration testing domain, it is also useful for vulnerability research and exploit development.
- The main components of the Metasploit Framework can be summarized as follows:
	- **msfconsole** - main command-line interface. Launch it using `msfconsole` command.
	- **Modules** - small components that are built to perform specific tasks such as exploits, scanners, payloads, etc.
	- **Tools** - Stand-alone tools that will help vulnerability research, vulnerability assessment, or penetration testing. Some of these tools are *msfvenom*, *pattern_create* and *pattern_offset*.
- **Exploit** - A piece of code that uses a vulnerability present on the target system.
- **Vulnerability** - A design, coding, or logic flaw affecting the target system. The exploitation of a vulnerability can result in disclosing confidential information or allowing the attacker to execute code on the target system.
- **Payload** - An exploit will take advantage of a vulnerability. However, if we want the exploit to have the result we want (gaining access to the target system, read confidential information, etc.), we need to use a payload. Payloads are the code that will run on the target system.

---

## 02 - Main Components

- **Auxiliary** - Any supporting module, such as scanners, crawlers and fuzzers, can be found here.
- **Encoders** - Encoders will allow you to encode the exploit and payload in the hope that a signature-based antivirus solution may miss them. Signature-based antivirus and security solutions have a database of known threats. They detect threats by comparing suspicious files to this database and raise an alert if there is a match. Thus encoders can have a limited success rate as antivirus solutions can perform additional checks.
- **Evasion** - While encoders will encode the payload, they should not be considered a direct attempt to evade antivirus software. On the other hand, “evasion” modules will try that, with more or less success.
- **Exploits** - Exploits, neatly organized by target system.
- **NOPs** - **NOPs** (***No OPeration***) do nothing, literally. They are represented in the Intel x86 CPU family they are represented with 0x90, following which the CPU will do nothing for one cycle. They are often used as a buffer to achieve consistent payload sizes.
- **Payloads** - Payloads are codes that will run on the target system. Exploits will leverage a vulnerability on the target system, but to achieve the desired result, we will need a payload. Running command on the target system is already an important step but having an interactive connection that allows you to type commands that will be executed on the target system is better. Such an interactive command line is called a "shell". Metasploit offers the ability to send different payloads that can open shells on the target system.
	1. **Adapters** - An adapter wraps single payloads to convert them into different formats. 
	2. **Singles** - Self-contained payloads (add user, launch notepad.exe, etc.) that do not need to download an additional component to run.
	3. **Stagers** - Responsible for setting up a connection channel between Metasploit and the target system. Useful when working with staged payloads. “Staged payloads” will first upload a stager on the target system then download the rest of the payload (stage). This provides some advantages as the initial size of the payload will be relatively small compared to the full payload sent at once.
	4. **Stages** - Downloaded by the stager. This will allow you to use larger sized payloads.
	- Metasploit has a subtle way to help you identify single (also called “inline”) payloads and staged payloads.
		- `generic/shell_reverse_tcp`
		- `windows/x64/shell/reverse_tcp`
	- Both are reverse Windows shells. The former is an inline (or single) payload, as indicated by the “_” between “shell” and “reverse”. While the latter is a staged payload, as indicated by the “/” between “shell” and “reverse”.
- **Post** - Post modules will be useful on the final stage of the penetration testing process listed above, post-exploitation.
- These can be found under the modules folder of your Metasploit installation: `/metasploit-framework/embedded/framework/modules`

---

## 03 - msfconsole

- It can be used like a regular command-line shell.
- It will support most Linux commands, including `clear` (to clear the terminal screen), but will not allow you to use some features of a regular command line (e.g. does not support output redirection).
- Msfconsole is managed by context; this means that unless set as a global variable, all parameter settings will be lost if you change the module you have decided to use.
- The **SMB** (***Server Message Block***) is widely used in Windows networks for file sharing and even for sending files to printers. The "*EternalBlue*" is an exploit allegedly developed by the U.S. National Security Agency (N.S.A.) for a vulnerability affecting the SMBv1 server on numerous Windows systems.
- `show options`: will print options related to the exploit chosen
- `back`: leave context
- `info`: further information about a module within its context
- `search`: will search the Metasploit Framework database for modules relevant to the given search parameter. You can conduct searches using CVE numbers, exploit names (eternalblue, heartbleed, etc.), or target system.
- Exploits are rated based on their reliability - [Exploit-Ranking](https://github.com/rapid7/metasploit-framework/wiki/Exploit-Ranking)

---

## 04 - Working with Modules

- After entering the context of a module using the `use` command, parameters need to be set.
- `show options`: command to list the required parameters.
- `set PARAMETER_NAME VALUE`: command to set parameters.
- Clear any parameter value using the `unset` command or clear all set parameters with the `unset all` command.
- `setg/unset`: set/unset values globally for all modules.
- `exploit -z/run`: launch the module. `z` will run the exploit and background the session as soon as it opens.
- `check`: check if the target system is vulnerable without exploiting it.
- **Sessions** - Once a vulnerability has been successfully exploited, a session will be created. This is the communication channel established between the target system and Metasploit.
- `background`: command to background the session prompt and go back to the msfconsole prompt.
- `sessions`: used from the msfconsole prompt or any context to see the existing sessions.
- `sessions -i`: command to interact with sessions followed by the desired session number.

### Common Parameters

Parameters you will often use are:

- **RHOSTS** - *Remote host* is the IP address of the target system. A single IP address or a network range can be set. This will support the CIDR (Classless Inter-Domain Routing) notation (/24, /16, etc.) or a network range (10.10.10.x – 10.10.10.y). You can also use a file where targets are listed.
- **RPORT** - *Remote port* is the port on the target system the vulnerable application is running on.
- **PAYLOAD** - The payload to be used with the exploit.
- **LHOST** - *Localhost* is the attacking machine IP address.
- **LPORT** - *Local port* is the port you will use for the reverse shell to connect back to. This is a port on your attacking machine, and you can set it to any port not used by any other application.
- **SESSION** - Each connection established to the target system using Metasploit will have a session ID. You will use this with post-exploitation modules that will connect to the target system using an existing connection.




