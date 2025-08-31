
#linux 

## Contents :-

#### [[#2.01 - Linux Distributions]]
#### [[#2.02 - Package Managers]]

---

## 2.01 - Linux Distributions

- Different versions of Linux 

### Parent Distributions 

- Red Hat Enterprise Linux (CentOS)
- Slackware (SUSE)
- Debian (Ubuntu and KALI LINUX)

#### KALI LINUX ™

#kali-linux

- KALI LINUX ™ is an open-source distribution of Linux that is widely used in the security industry. 
- This is because KALI LINUX ™, which is Debian-based, is pre-installed with many useful tools for penetration testing and digital forensics. 
- A penetration test is a simulated attack that helps identify vulnerabilities in systems, networks, websites, applications, and processes. Digital forensics is the practice of collecting and analyzing data to determine what has happened after an attack. These are key activities in the security industry. 

#### Ubuntu

- Ubuntu is an open-source, user-friendly distribution that is widely used in security and other industries. 
- It has both a command-line interface (CLI) and a graphical user interface (GUI). 
- Ubuntu is also Debian-derived and includes common applications by default. Users can also download many more applications from a package manager, including security-focused tools. 
- Ubuntu is also widely used for cloud computing. As organizations migrate to cloud servers, cybersecurity work may more regularly involve Ubuntu derivatives.

#### Parrot

- Parrot is an open-source distribution that is commonly used for security. 
- Parrot comes with pre-installed tools related to penetration testing and digital forensics. Like both KALI LINUX ™ and Ubuntu, it is based on Debian.
- Parrot is also considered to be a user-friendly Linux distribution. This is because it has a GUI that many find easy to navigate. This is in addition to Parrot’s CLI.

#### Red Hat® Enterprise Linux®

- Red Hat Enterprise Linux is a subscription-based distribution of Linux built for enterprise use. 
- Red Hat is not free, which is a major difference from the previously mentioned distributions. 
- Because it’s built and supported for enterprise use, Red Hat also offers a dedicated support team for customers to call about issues.

#### CentOS

- CentOS is an open-source distribution that is closely related to Red Hat. 
- It uses source code published by Red Hat to provide a similar platform. However, CentOS does not offer the same enterprise support that Red Hat provides and is supported through the community.

---

#package-managers

## 2.02 - Package Managers

- A **package** is a piece of software that can be combined with other packages to form an application. Some packages may be large enough to form applications on their own. 
- Packages contain the files necessary for an application to be installed. These files include dependencies, which are supplemental files used to run an application. 
- **Package managers** can help resolve any issues with dependencies and perform other management tasks. A package manager is a tool that helps users install, manage, and remove packages or applications. Linux uses multiple package managers. 

***Note***: It’s important to use the most recent version of a package when possible. The most recent version has the most up-to-date bug fixes and security patches. These help keep your system more secure.

### Types of package managers

- Many commonly used Linux distributions are derived from the same parent distribution. For example, KALI LINUX ™, Ubuntu, and Parrot all come from Debian. CentOS comes from Red Hat.
- Different package managers typically use different file extensions. For example, Red Hat Package Manager (RPM) has files which use the .rpm file extension, such as Package-Version-Release_Architecture.rpm. Package managers for Debian-derived Linux distributions, such as dpkg, have files which use the .deb file extension, such as Package_Version-Release_Architecture.deb.
- **Package management tools** - In addition to package managers like RPM and dpkg, there are also package management tools that allow you to easily work with packages through the shell. Package management tools are sometimes utilized instead of package managers because they allow users to more easily perform basic tasks, such as installing a new package. 
	1. **APT** (***Advanced Package Tool***) - APT is a tool used with Debian-derived distributions. It is run from the command-line interface to manage, search, and install packages.
	2. **YUM** (***Yellowdog Updater Modified***) - YUM is a tool used with Red Hat-derived distributions. It is run from the command-line interface to manage, search, and install packages. YUM works with .rpm files.

---

#shell

## Shell

- Shell is the command-line interpreter

### Types of shells

1. Bourne-Again Shell (bash)
2. C Shell (csh)
3. Korn Shell (ksh)
4. Enhanced C shell (tcsh)
5. Z Shell (zsh)

All Linux shells use common Linux commands, but they can differ in other features. For example, ksh and bash use the dollar sign ($) to indicate where users type in their commands. Other shells, such as zsh, use the percent sign (%) for this purpose.

#### Bash

- Bash is the default shell in most Linux distributions. It’s considered a user-friendly shell. You can use bash for basic Linux commands as well as larger projects.
- Bash is also the most popular shell in the cybersecurity profession. 

---
