
## Contents :-

#### [[#1.01 - Introduction to OS]]
#### [[#1.02 - Linux Architecture]]
#### [[#1.03 - Additional Information]]

---

#os

## 1.01 - Introduction to OS

**OS** (***Operating systems***) make connections between applications and hardware to allow users to perform tasks. 

### Booting the computer

- When you boot, or turn on, your computer, either a BIOS or UEFI microchip is activated. 
- The **BIOS **(***Basic Input/Output System***) is a microchip that contains loading instructions for the computer and is prevalent in older systems. 
- The **UEFI** (***Unified Extensible Firmware Interface***) is a microchip that contains loading instructions for the computer and replaces BIOS on more modern systems.
- The BIOS and UEFI chips both perform the same function for booting the computer. BIOS was the standard chip until 2007, when UEFI chips increased in use. Now, most new computers include a UEFI chip. UEFI provides enhanced security features.
- The BIOS or UEFI microchips contain a variety of loading instructions for the computer to follow. 
- The last instruction from the BIOS or UEFI activates the bootloader. 
- The bootloader is a software program that boots the operating system. Once the operating system has finished booting, your computer is ready for use.

### Process Flow
 
1. **User** - initiates the process by having something they want to accomplish on the computer. 
2. **Application** - the software program that users interact with to complete a task. 
3. **Operating system** - the OS receives the user’s request from the application. It’s the operating system’s job to interpret the request and direct its flow. In order to complete the task, the OS sends it on to applicable components of the hardware. 
4. **Hardware** - the hardware is where all the processing is done to complete the tasks initiated by the user. After the work is done by the hardware, it sends the output back through the operating system to the application so that it can display the results to the user.

### CLI vs. GUI

- A **GUI** (***Graphical User Interface***) is a user interface that uses icons on the screen to manage different tasks on the computer. 
- A **CLI** (***Command-Line Interface***) is a text-based user interface that uses commands to interact with the computer. 

![[GUI vs CLI.png]]

### Types of OS

1. **Windows and macOS**
	- The Windows operating system was introduced in 1985, and macOS was introduced in 1984. Both operating systems are used in personal and enterprise computers. 
	- Windows is a closed-source operating system, which means the source code is not shared freely with the public. 
	- macOS is partially open source. It has some open-source components, such as macOS’s kernel. macOS also has some closed-source components. 

2. **Linux**
	- The first version of Linux was released in 1991, and other major releases followed in the early 1990s. 
	- Linux is a completely open-source operating system, which means that anyone can access Linux and its source code. The open-source nature of Linux allows developers in the Linux community to collaborate.
	- Linux is particularly important to the security industry. There are some distributions that are specifically designed for security.

3. **ChromeOS**
	- ChromeOS launched in 2011. 
	- It’s partially open source and is derived from Chromium OS, which is completely open source. 
	- ChromeOS is frequently used in the education field.

4. **Android and iOS**
	- Android and iOS are both mobile operating systems. 
	- Unlike the other operating systems mentioned, mobile operating systems are typically used in mobile devices, such as phones, tablets, and watches. 
	- Android was introduced for public use in 2008, and iOS was introduced in 2007. 
	- Android is open source, and iOS is partially open source.

5. **Legacy operating systems**
	- A legacy operating system is an operating system that is outdated but still being used.
	- Some organizations continue to use legacy operating systems because software they rely on is not compatible with newer operating systems. 
	- This can be more common in industries that use a lot of equipment that requires embedded software—software that’s placed inside components of the equipment.
	- Legacy operating systems can be vulnerable to security issues because they’re no longer supported or updated. This means that legacy operating systems might be vulnerable to new threats. 

---

#linux

## 1.02 - Linux Architecture

### User

- The user is the person interacting with a computer. They initiate and manage computer tasks. 
- Linux is a multi-user system, which means that multiple users can use the same resources at the same time.

### Applications

- An application is a program that performs a specific task. 
- Some applications typically come pre-installed on your computer, such as calculators or calendars. Other applications might have to be installed, such as some web browsers or email clients. 
- In Linux, you'll often use a package manager to install applications. 
- A package manager is a tool that helps users install, manage, and remove packages or applications. 
- A package is a piece of software that can be combined with other packages to form an application.

### Shell
 
- The shell is the command-line interpreter. 
- Everything entered into the shell is text based. 
- The shell allows users to give commands to the kernel and receive responses from it. The shell translates the commands you enter so that the computer can perform the tasks you want.

### Filesystem Hierarchy Standard

- The **FHS** (***Filesystem Hierarchy Standard***) is the component of the Linux OS that organizes data. It specifies the location where data is stored in the operating system. 
- A directory is a file that organizes where other files are stored. Directories are sometimes called “folders,” and they can contain files or other directories. The FHS defines how directories, directory contents, and other storage is organized so the operating system knows where to find specific data. 

### Kernel

- The kernel is the component of the Linux OS that manages processes and memory. 
- It communicates with the applications to route commands. 
- The Linux kernel is unique to the Linux OS and is critical for allocating resources in the system.
- The kernel controls all major functions of the hardware, which can help get tasks expedited more efficiently.

### Hardware

- The hardware is the physical components of a computer. 
- Hardware is categorized as either peripheral or internal.

#### Peripheral devices

- Peripheral devices are hardware components that are attached and controlled by the computer system. 
- They are not core components needed to run the computer system. Peripheral devices can be added or removed freely. 
- Examples of peripheral devices include monitors, printers, the keyboard, and the mouse.

#### Internal hardware

- Internal hardware are the components required to run the computer. 
- Internal hardware includes a main circuit board and all components attached to it. This main circuit board is also called the motherboard. 
- Internal hardware includes the following: 
	1. The **CPU** (***Central Processing Unit***) is a computer’s main processor, which is used to perform general computing tasks on a computer. The CPU executes the instructions provided by programs, which enables these programs to run. 
	2. **RAM** (***Random Access Memory***) is a hardware component used for short-term memory. It’s where data is stored temporarily as you perform tasks on your computer. Information in RAM cannot be accessed once the computer has been turned off. The CPU takes the data from RAM to run programs. 
	3. The **hard drive** is a hardware component used for long-term memory. It’s where programs and files are stored for the computer to access later. Information on the hard drive can be accessed even after a computer has been turned off and on again. A computer can have multiple hard drives.

### Standard Input & Output

- Standard input is information received by the OS via the command line.
- Standard output is information returned by the OS through the shell.

---

#additional-info 

##  1.03 - Additional Information

- [List of known vulnerabilities affecting Microsoft products and services](https://msrc.microsoft.com/update-guide/vulnerability) 
- [List of security updates and information for Apple® operating systems, including macOS and iOS, and other products](https://support.apple.com/en-us/HT201222) 
- [List of known vulnerabilities affecting Ubuntu, which is a specific distribution of Linux](https://ubuntu.com/security/cves) 
- [List of known vulnerabilities affecting Google Cloud products and services](https://cloud.google.com/support/bulletins) 

---
