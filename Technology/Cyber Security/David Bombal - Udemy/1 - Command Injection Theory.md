
#command-injection

## Contents :-

#### [[#1.1 - Command Injection]]
#### [[#1.2 - Finding Command Injection Vulnerabilities]]
#### [[#1.3 - Preventing Command Injection Vulnerabilities]]
#### [[#1.4 - Additional Information]]

---

## 1.1 - Command Injection

- **OS Command Injection** - a vulnerability that consists of an attacker executing commands on the host OS via a vulnerable application.

### 1.1.1 - Types of Command Injection

1. **In-band Command Injection** - consists of an attacker executing commands on the host OS via a vulnerable application and ==receiving the response of the command in the application==.
2. **Blind Command Injection** - consists of an attacker executing commands on the host OS via a vulnerable application that ==does not return the output from the command within its HTTP response==.

### 1.1.2 - Impact {CRITICAL}

- unauthorized access to application and host OS
- can be used to view sensitive information, alter and delete content in application; thus violating CIA triad
- remote code execution on the OS

---

## 1.2 - Finding Command Injection Vulnerabilities

- **Black Box Testing** - tester is given limited information and access to system
- **White Box Testing** - tester is given complete information and access to system

### 1.2.1 - Black-Box Testing 

1. Map the application.
	- identify all instances where the web app appears to be interacting with the underlying OS.
2. Fuzz the application.
	- shell metacharacters: &, &&, |, ||, ;, \n, `, $()
3. For in-band command injection, analyze the response of the application to determine if it's vulnerable.
4. For blind command injection:
	- trigger a time delay using the ping delay or sleep command.
	- output the response of the command in the web root and retrieve the file directly using a browser.
	- open an out-of-band channel back to a server you control.

### 1.2.2 - White-Box Testing

1. Perform combination of black box and white box testing.
2. Map all input vectors in the application.
3. Review source code to determine if any of the input vectors are added as parameters to functions that execute system commands.
4. Once a vulnerability is identified, test it to confirm that it is exploitable.

---

## 1.3 - Preventing Command Injection Vulnerabilities

- most effective way: ==never call out OS commands from application-layer code==. Instead, implement required functionality using safer platform APIs. *Example:* use `mkdir()` instead of `system("mkdir /dir_name")`
- to perform OS commands using user-supplied input, then ==strong input validation== must be performed.
	- validate against a whitelist of permitted values
	- validate that the input is as expected

---

#additional-info 
## 1.4 - Additional Information

- **TTL**(***Time to Live***) 
	- TTL for Linux = 64
	- TTL for Windows = 128
- [OS Command Injection - PortSwigger](https://portswigger.net/web-security/os-command-injection)

---
