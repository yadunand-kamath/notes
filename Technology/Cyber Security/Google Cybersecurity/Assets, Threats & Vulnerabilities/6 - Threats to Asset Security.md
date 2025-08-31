
#socialengineering 

## Contents :-

#### [[#6.01 - Social Engineering]]
#### [[#6.02 - Phishing]]

#### [[#6.03 - Web-based Exploits]]

#### [[#6.04 - Malware]]

#### [[#6.05 - Threat Modeling]]

---

## 6.01 - Social Engineering

- **Social Engineering** is a manipulation technique that exploits human error to gain private information, access, or valuables. Each technique is designed to capitalize on the trusting nature of people and their willingness to help.
- Social engineering is a form of deception that takes advantage of the way people think. It preys on people’s natural feelings of curiosity, generosity, and excitement. Threat actors turn those feelings against their targets by affecting their better judgment. 

### Stages of Social Engineering

1. Prepare 
2. Establish trust
3. Use persuasion tactics 
4. Disconnect from target 

### Preventing Social Engineering 

- Implementing managerial controls 
- Staying informed ahead of trends
- Sharing your knowledge with others 

### Common types of social engineering

- **Baiting** is a social engineering tactic that tempts people into compromising their security. A common example is USB baiting that relies on someone finding an infected USB drive and plugging it into their device.
- **Phishing** is the use of digital communications to trick people into revealing sensitive data or deploying malicious software. It is one of the most common forms of social engineering, typically performed via email.
- **Quid pro quo** is a type of baiting used to trick someone into believing that they’ll be rewarded in return for sharing access, information, or money. For example, an attacker might impersonate a loan officer at a bank and call customers offering them a lower interest rate on their credit card. They'll tell the customers that they simply need to provide their account details to claim the deal.
- **Tailgating** is a social engineering tactic in which unauthorized people follow an authorized person into a restricted area. This technique is also sometimes referred to as piggybacking.
- **Watering hole** is a type of attack when a threat actor compromises a website frequently visited by a specific group of users. Oftentimes, these watering hole sites are infected with malicious software. An example is the Holy Water attack of 2020 that infected various religious, charity, and volunteer websites.

---

#phishing 

## 6.02 - Phishing

**Phishing** is the use of digital communications to trick people into revealing sensitive data or deploying malicious software.

### Types of Phishing

- **Email Phishing** - attack sent via email in which threat actors send messages pretending to be a trusted person or entity.
- **Smishing** - attack that uses **SMS**(***Short Message Service***), a technology that powers text messaging.
- **Vishing** - uses voice calls or voice messages to trick targets into providing personal information over the phone.
- **Spear Phishing** - subset of email phishing in which specific people are purposefully targeted.
- **Whaling** - category of spear phishing attempts that are aimed at high-ranking executives in an organization.
- **Angler Phishing** - attackers impersonate customer service representatives on social media.

---

## 6.03 - Web-based Exploits

**Web-based exploits** - malicious code or behavior that's used to take advantage of coding flaws in a web application.

- **Injection Attack** - malicious code inserted into a vulnerable application
- **XSS**(***Cross-site scripting***) - an injection attack that inserts code into a vulnerable website or web application

### Types of XSS Attacks

1. **Reflected** - an instance when a malicious script is sent to server and activated during server's response.
2. **Stored** - an instance when malicious script is injected directly on the server.
3. **DOM-based** - an instance when malicious script exists in the webpage a browser loads.

### SQL injection categories

- **SQL Injection** - an attack that executes unexpected queries on a database.

1. **In-band** - An in-band injection is one that uses the same communication channel to launch the attack and gather the results. For example, this might occur in the search box of a retailer's website that lets customers find products to buy. If the search box is vulnerable to injection, an attacker could enter a malicious query that would be executed in the database, causing it to return sensitive information like user passwords. The data that's returned is displayed back in the search box where the attack was initiated.

2. **Out-of-band** - An out-of-band injection is one that uses a different communication channel  to launch the attack and gather the results. For example, an attacker could use a malicious query to create a connection between a vulnerable website and a database they control. This separate channel would allow them to bypass any security controls that are in place on the website's server, allowing them to steal sensitive data.

Note: Out-of-band injection attacks are very uncommon because they'll only work when certain features are enabled on the target server.

3. **Inferential** - Inferential SQL injection occurs when an attacker is unable to directly see the results of their attack. Instead, they can interpret the results by analyzing the behavior of the system. For example, an attacker might perform a SQL injection attack on the login form of a website that causes the system to respond with an error message. Although sensitive data is not returned, the attacker can figure out the database's structure based on the error. They can then use this information to craft attacks that will give them access to sensitive data or to take control of the system.

#### Injection Prevention

A key to preventing SQL injection attacks is to escape user inputs—preventing someone from inserting any code that a program isn't expecting. There are several ways to escape user inputs:

- **Prepared statements**: a coding technique that executes SQL statements before passing them on to a database
- **Input sanitization**: programming that removes user input which could be interpreted as code.
- **Input validation**: programming that ensures user input meets a system's expectations.

---

#malware 
## 6.04 - Malware

- **Malware** is software designed to harm devices or networks.

1. **Virus** - malicious code written to interfere with computer operations and cause damage to data and software. This type of malware must be installed by the target user before it can spread itself and cause damage. One of the many ways that viruses are spread is through phishing campaigns where malicious links are hidden within links or attachments.
2. **Worm** - malware that can duplicate and spread itself across systems on its own. Similar to a virus, a worm must be installed by the target user and can also be spread with tactics like malicious email. Given a worm's ability to spread on its own, attackers sometimes target devices, drives, or files that have shared access over a network.
3. **Trojan** - also called a Trojan horse, is malware that looks like a legitimate file or program. This characteristic relates to how trojans are spread. Similar to viruses, attackers deliver this type of malware hidden in file and application downloads. Attackers rely on tricking unsuspecting users into believing they’re downloading a harmless file, when they’re actually infecting their own device with malware that can be used to spy on them, grant access to other devices, and more.
4. **Adware** - Advertising-supported software, or adware, is a type of legitimate software that is sometimes used to display digital advertisements in applications. Software developers often use adware as a way to lower their production costs or to make their products free to the public—also known as freeware or shareware. In these instances, developers monetize their product through ad revenue rather than at the expense of their users. Malicious adware falls into a sub-category of malware known as a potentially unwanted application (PUA). A PUA is a type of unwanted software that is bundled in with legitimate programs which might display ads, cause device slowdown, or install other software. Attackers sometimes hide this type of malware in freeware with insecure design to monetize ads for themselves instead of the developer. This works even when the user has declined to receive ads.
5. **Spyware** - malware that's used to gather and sell information without consent. It's also considered a PUA. Spyware is commonly hidden in bundleware, additional software that is sometimes packaged with other applications. PUAs like spyware have become a serious challenge in the open-source software development ecosystem. That’s because developers tend to overlook how their software could be misused or abused by others.
6. **Scareware** - Another type of PUA is scareware. This type of malware employs tactics to frighten users into infecting their own device. Scareware tricks users by displaying fake warnings that appear to come from legitimate companies. Email and pop-ups are just a couple of ways scareware is spread. Both can be used to deliver phony warnings with false claims about the user's files or data being at risk.
7. **Fileless malware** - Fileless malware does not need to be installed by the user because it uses legitimate programs that are already installed to infect a computer. This type of infection resides in memory where the malware never touches the hard drive. This is unlike the other types of malware, which are stored within a file on disk. Instead, these stealthy infections get into the operating system or hide within trusted applications.

Pro tip: Fileless malware is detected by performing memory analysis, which requires experience with operating systems. 

8. **Rootkits** - A rootkit is malware that provides remote, administrative access to a computer. Most attackers use rootkits to open a backdoor to systems, allowing them to install other forms of malware or to conduct network security attacks. This kind of malware is often spread by a combination of two components: a dropper and a loader. A dropper is a type of malware that comes packed with malicious code which is delivered and installed onto a target system. For example, a dropper is often disguised as a legitimate file, such as a document, an image, or an executable to deceive its target into opening, or dropping it, onto their device. If the user opens the dropper program, its malicious code is executed and it hides itself on the target system.

Multi-staged malware attacks, where multiple packets of malicious code are deployed, commonly use a variation called a loader. A loader is a type of malware that downloads strains of malicious code from an external source and installs them onto a target system. Attackers might use loaders for different purposes, such as to set up another type of malware---a botnet.

9. **Botnet** - a botnet, short for “robot network,” is a collection of computers infected by malware that are under the control of a single threat actor, known as the “bot-herder.” Viruses, worms, and trojans are often used to spread the initial infection and turn the devices into a bot for the bot-herder. The attacker then uses file sharing, email, or social media application protocols to create new bots and grow the botnet. When a target unknowingly opens the malicious file, the computer, or bot, reports the information back to the bot-herder, who can execute commands on the infected computer.

10. **Ransomware** - Ransomware describes a malicious attack where threat actors encrypt an organization's data and demand payment to restore access. According to the Cybersecurity and Infrastructure Security Agency (CISA), ransomware crimes are on the rise and becoming increasingly sophisticated. Ransomware infections can cause significant damage to an organization and its customers.

11. Cryptojacking - a form of malware that installs software to illegally mine cryptocurrencies.
		Signs of Cryptojacking:
	- slowdown 
	- increased CPU usage 
	- sudden system crashes 
	- fast draining batteries
	- unusually high electric costs 

![[malware.png]]

---

## 6.05 - Threat Modeling

**Threat Modeling** is the process of identifying assets, their vulnerabilities, and how each is exposed to threats.

### 6.05.01 - Threat Modeling Steps

1. Define the scope
2. Identify threats
	- **Attack tree** - a diagram that maps threats to assets
3. Characterize the environment
4. Analyze threats
5. Mitigate risks
6. Evaluate findings

### 6.05.02 -Threat Modeling Frameworks

#### STRIDE 

- developed by Microsoft
- commonly used to identify vulnerabilities in six specific attack vectors. 
- The acronym represents each of these vectors: spoofing, tampering, repudiation, information disclosure, denial of service, and elevation of privilege.

#### PASTA

- The **PASTA**(***Process of Attack Simulation and Threat Analysis***) is a risk-centric threat modeling process developed by two OWASP leaders and supported by a cybersecurity firm called VerSprite. 
- Its main focus is to discover evidence of viable threats and represent this information as a model. 
- PASTA's evidence-based design can be applied when threat modeling an application or the environment that supports that application. 
1. Define business and security objectives
2. Define the technical scope
3. Decompose the application
4. Perform a threat analysis
5. Perform a vulnerability analysis
6. Conduct attack modeling 
7. Analyze risk and impact

#### Trike 

- Trike is an open source methodology and tool that takes a security-centric approach to threat modeling. 
- It's commonly used to focus on security permissions, application use cases, privilege models, and other elements that support a secure environment.

#### VAST
- The **VAST**(***Visual, Agile, and Simple Threat***) Modeling framework is part of an automated threat-modeling platform called ThreatModeler®. 
- Many security teams opt to use VAST as a way of automating and streamlining their threat modeling assessments.

---

#additional-info 

## Additional Information

- [Phising.org](https://www.phishing.org) - reports on latest phishing trends
- [Anti-Phishing Working Group](https://apwg.org) - non-profit group that publishes a quarterly report on phishing trends.

---
