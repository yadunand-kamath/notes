
## Contents :-

#### [[#4.01 - Vulnerability Management]]
#### [[#4.02 - Defense in Depth Strategy]]
#### [[#4.03 - Common Vulnerabilities and Exposure (CVE)]]
#### [[#4.04 - OWASP]]
#### [[#4.05 - Open Source Intelligence]]
#### [[#4.06 - Vulnerability Assessments]]

#### [[#4.07 - Additional Information]]

---

#vulnerability 

## 4.01 - Vulnerability Management

- **Vulnerability** - a weakness that can be exploited by a threat
- **Exploit** - a way of taking advantage of a vulnerability
- **Vulnerability Management** - process of finding and patching vulnerabilities

### 4.01.01 - Vulnerability Management Process 

1. Identify vulnerabilities
2. Consider potential exploits
3. Prepare defenses against threats
4. Evaluate those defenses

- **Zero-day** - an exploit that was previously unknown

---

## 4.02 - Defense in Depth Strategy

**Defense in depth** is a layered approach to vulnerability management that reduces risk.

Defense in Depth Strategy:

1. Perimeter layer
2. Network layer
3. Endpoint layer
4. Application layer
5. Data layer

---

#cve

## 4.03 - Common Vulnerabilities and Exposure (CVE)

- **Exposure** - a mistake that can be exploited by a threat.
- **CVE List** - an openly accessible dictionary of known vulnerabilities and exposures.
- **MITRE** - a collection of non-profit research and development centers.
- **CNA**(***CVE Numbering Authority***) - an organization that volunteers to analyze and distribute information on eligible CVEs. 

### 4.03.01 - CVE List Criteria

1. Independent of other issues
2. Recognized as a potential security risk
3. Submitted with supporting evidence
4. Only affect one codebase

- **CVSS**(***Common Vulnerability Scoring System***) - a measurement system that scores the severity of a vulnerability.

---

#owasp 

## 4.04 - OWASP

OWASP stands for ***Open Web Application Security Project***, recently renamed ***Open Worldwide Application Security Project®***.
OWASP is a nonprofit foundation that works to improve the security of software. It is an open platform that security professionals from around the world use to share information, tools, and events that are focused on securing the web.

### 4.04.01 - OWASP Top 10

- One of OWASP’s most valuable resources is the OWASP Top 10. 
- The organization has published this list since 2003 as a way to spread awareness of the web’s most targeted vulnerabilities. 
- The Top 10 mainly applies to new or custom made software. 
- Many of the world's largest organizations reference the OWASP Top 10 during application development to help ensure their programs address common security mistakes.

***NOTE***: 
- OWASP’s Top 10 is updated every few years as technologies evolve. Rankings are based on how often the vulnerabilities are discovered and the level of risk they present.
- Auditors also use the OWASP Top 10 as one point of reference when checking for regulatory compliance.

### 4.04.02 - Common vulnerabilities

These are the most regularly listed vulnerabilities that appear in their rankings to know about:

#### 1. Broken access control

Access controls limit what users can do in a web application. For example, a blog might allow visitors to post comments on a recent article but restricts them from deleting the article entirely. Failures in these mechanisms can lead to unauthorized information disclosure, modification, or destruction. They can also give someone unauthorized access to other business applications.

#### 2. Cryptographic failures

Information is one of the most important assets businesses need to protect. Privacy laws such as General Data Protection Regulation (GDPR) require sensitive data to be protected by effective encryption methods. Vulnerabilities can occur when businesses fail to encrypt things like personally identifiable information (PII). For example, if a web application uses a weak hashing algorithm, like MD5, it’s more at risk of suffering a data breach.

#### 3. Injection

Injection occurs when malicious code is inserted into a vulnerable application. Although the app appears to work normally, it does things that it wasn’t intended to do. Injection attacks can give threat actors a backdoor into an organization’s information system. A common target is a website’s login form. When these forms are vulnerable to injection, attackers can insert malicious code that gives them access to modify or steal user credentials. 

#### 4. Insecure design

Applications should be designed in such a way that makes them resilient to attack. When they aren’t, they’re much more vulnerable to threats like injection attacks or malware infections. Insecure design refers to a wide range of missing or poorly implemented security controls that should have been programmed into an application when it was being developed.

#### 5. Security misconfiguration

Misconfigurations occur when security settings aren’t properly set or maintained. Companies use a variety of different interconnected systems. Mistakes often happen when those systems aren’t properly set up or audited. A common example is when businesses deploy equipment, like a network server, using default settings. This can lead businesses to use settings that fail to address the organization's security objectives.

#### 6. Vulnerable and outdated components

Vulnerable and outdated components is a category that mainly relates to application development. Instead of coding everything from scratch, most developers use open-source libraries to complete their projects faster and easier. This publicly available software is maintained by communities of programmers on a volunteer basis. Applications that use vulnerable components that have not been maintained are at greater risk of being exploited by threat actors.

#### 7. Identification and authentication failures

Identification is the keyword in this vulnerability category. When applications fail to recognize who should have access and what they’re authorized to do, it can lead to serious problems. For example, a home Wi-Fi router normally uses a simple login form to keep unwanted guests off the network. If this defense fails, an attacker can invade the homeowner’s privacy.

#### 8. Software and data integrity failures

Software and data integrity failures are instances when updates or patches are inadequately reviewed before implementation. Attackers might exploit these weaknesses to deliver malicious software. When that occurs, there can be serious downstream effects. Third parties are likely to become infected if a single system is compromised, an event known as a supply chain attack.

A famous example of a supply chain attack is the 
SolarWinds cyber attack (2020)
 where hackers injected malicious code into software updates that the company unknowingly released to their customers.

#### 9. Security logging and monitoring failures

- In security, it’s important to be able to log and trace back events. 
- Having a record of events like user login attempts is critical to finding and fixing problems. 
- Sufficient monitoring and incident response is equally important.

#### 10. Server-side request forgery

- Companies have public and private information stored on web servers. When you use a hyperlink or click a button on a website, a request is sent to a server that should validate who you are, fetch the appropriate data, and then return it to you.
- **SSRF**(***Server-side Request Forgery***) is when attackers manipulate the normal operations of a server to read or update other resources on that server. These are possible when an application on the server is vulnerable. Malicious code can be carried by the vulnerable app to the host server that will fetch unauthorized data.

---

#osint

## 4.05 - Open Source Intelligence

**OSINT**(***Open Source Intelligence***) is the collection and analysis of information from publicly available sources to generate usable intelligence. It's commonly used to support cybersecurity activities, like identifying potential threats and vulnerabilities. 

Some of the ways OSINT can be used to generate intelligence
- To provide insights into cyber attacks
- To detect potential data exposures
- To evaluate existing defenses
- To identify unknown vulnerabilities
- To develop profiles of potential targets and make data driven decisions on improving defenses

### Information vs Intelligence

The terms intelligence and information are often used interchangeably, making it easy to mix them up. Both are important aspects of cybersecurity that differ in their focus and objectives.

- Information refers to the collection of raw data or facts about a specific subject. Intelligence, on the other hand, refers to the analysis of information to produce knowledge or insights that can be used to support decision-making.

For example, new information might be released about an update to the operating system (OS) that's installed on your organization's workstations. Later, you might find that new cyber threats have been linked to this new update by researching multiple cybersecurity news resources. The analysis of this information can be used as intelligence to guide your organization's decision about installing the OS updates on employee workstations.

- In other words, intelligence is derived from information through the process of analysis, interpretation, and integration. Gathering information and intelligence are both important aspects of cybersecurity.

Intelligence improves decision-making 
Businesses often use information to gain insights into the behavior of their customers. Insights, or intelligence, can then be used to improve their decision making. In security, open-source information is used in a similar way to gain insights into threats and vulnerabilities that can pose risks to an organization.

OSINT plays a significant role in information security (InfoSec), which is the practice of keeping data in all states away from unauthorized users.

For example, a company's InfoSec team is responsible for protecting their network from potential threats. They might utilize OSINT to monitor online forums and hacker communities for discussions about emerging vulnerabilities. If they come across a forum post discussing a newly discovered weakness in a popular software that the company uses, the team can quickly assess the risk, prioritize patching efforts, and implement necessary safeguards to prevent an attack.


### OSINT tools

Collecting intelligence is sometimes part of the vulnerability management process. There's an enormous amount of open-source information online. Finding relevant information that can be used to gather intelligence is a challenge. Information can be gathered from a variety of sources, such as search engines, social media, discussion boards, blogs, and more. Several tools also exist that can be used in your intelligence gathering process. 

- [VirusTotal](https://www.virustotal.com/gui/home/upload) - a service that allows anyone to analyze suspicious files, domains, URLs, and IP addresses for malicious content.
- [MITRE ATT&CK®](https://attack.mitre.org/) - a knowledge base of adversary tactics and techniques based on real-world observations.
- [OSINT Framework](https://osintframework.com/) - a web-based interface where you can find OSINT tools for almost any kind of source or platform.
- [Have I been Pwned](https://haveibeenpwned.com/) - a tool that can be used to search for breached email accounts.

---
## 4.06 - Vulnerability Assessments

**Vulnerability assessment** is the internal review process of an organization's security systems, to identify weaknesses and prevent attacks.
It has the following process:
1. Identification
2. Vulnerability Analysis
3. Risk Assessment
4. Remediation

### Vulnerability Scanners

#vulnerability-scanner 

A vulnerability scanner is software that automatically compares known vulnerabilities and exposures against technologies on the network to find misconfigurations or programming flaws.

### Updates

- A **patch update** is a software and OS update that addresses security vulnerabilities within a program or product. 
- Patches usually contain bug fixes that address security vulnerabilities and exposures. 
- **EOL**(***End-of-life***) **software** - software for which updates are not available.
- Patches and updates are different from upgrades. **Upgrades** refer to completely new versions of hardware or software that can be purchased.

#### Update Strategies

- Manual Updates
- Automatic Updates - **CISA**(***Cybersecurity and Infrastructure Security Agency***) recommends using this.

### Performing scans

Vulnerability scanners are meant to be non-intrusive, i.e., they don’t break or take advantage of a system like an attacker would. Instead, they simply scan a surface and alert you to any potentially unlocked doors in your systems.

Note: While vulnerability scanners are non-intrusive, there are instances when a scan can inadvertently cause issues, like crash a system.

There are a few different ways that these tools are used to scan a surface. Each approach corresponds to the pathway a threat actor might take. 

#### Scan Types

1. **External vs Internal**
	- External and internal scans simulate an attacker's approach.
	- External scans test the perimeter layer outside of the internal network. They analyze outward facing systems, like websites and firewalls. These kinds of scans can uncover vulnerable things like vulnerable network ports or servers.
	- Internal scans start from the opposite end by examining an organization's internal systems. For example, this type of scan might analyze application software for weaknesses in how it handles user input.

2. **Authenticated vs Unauthenticated**
	- Authenticated and unauthenticated scans simulate whether or not a user has access to a system.
	- Authenticated scans might test a system by logging in with a real user account or even with an admin account. These service accounts are used to check for vulnerabilities, like broken access controls.
	- Unauthenticated scans simulate external threat actors that do not have access to your business resources. For example, a scan might analyze file shares within the organization that are used to house internal-only documents. Unauthenticated users should receive "access denied" results if they tried opening these files. However, a vulnerability would be identified if you were able to access a file.

3. **Limited vs Comprehensive**
	- Limited and comprehensive scans focus on particular devices that are accessed by internal and external users.
	- Limited scans analyze particular devices on a network, like searching for misconfigurations on a firewall.
	- Comprehensive scans analyze all devices connected to a network. This includes operating systems, user databases, and more.

***NOTE:*** Discovery scanning should be done prior to limited or comprehensive scans. Discovery scanning is used to get an idea of the computers, devices, and open ports that are on a network.

### Penetration testing

- A penetration test, or pen test, is a simulated attack that helps identify vulnerabilities in systems, networks, websites, applications, and processes. The simulated attack in a pen test involves using the same tools and techniques as malicious actors in order to mimic a real life attack. 
- Since a pen test is an authorized attack, it is considered to be a form of ethical hacking. 
- Unlike a vulnerability assessment that finds weaknesses in a system's security, a pen test exploits those weaknesses to determine the potential consequences if the system breaks or gets broken into by a threat actor.

***NOTE:*** Organizations that are regulated by PCI DSS, HIPAA, or GDPR must routinely perform penetration testing to maintain compliance standards.

- These authorized attacks are performed by pen testers who are skilled in programming and network architecture. Depending on their objectives, organizations might use a few different approaches to penetration testing:
1. **Red team** tests simulate attacks to identify vulnerabilities in systems, networks, or applications.
2. **Blue team** tests focus on defense and incident response to validate an organization's existing security systems.
3. **Purple team** tests are collaborative, focusing on improving the security posture of the organization by combining elements of red and blue team exercises.

#### Penetration Testing Strategies

1. **Open-box testing** is when the tester has the same privileged access that an internal developer would have—information like system architecture, data flow, and network diagrams. This strategy goes by several different names, including internal, full knowledge, white-box, and clear-box penetration testing.
2. **Closed-box testing** is when the tester has little to no access to internal systems—similar to a malicious hacker. This strategy is sometimes referred to as external, black-box, or zero knowledge penetration testing. ==Closed box testers tend to produce the most accurate simulations of a real-world attack.== 
3. **Partial knowledge testing** is when the tester has limited access and knowledge of an internal system—for example, a customer service representative. This strategy is also known as gray-box testing.

#### Becoming a Pentester

- Network and application security
- Experience with operating systems, like Linux
- Vulnerability analysis and threat modeling
- Detection and response tools
- Programming languages, like Python and BASH
- Communication skills

#### Bug Bounty programs

- Organization’s commonly run bug bounty programs which offer freelance pen testers financial rewards for finding and reporting vulnerabilities in their products. 
- ***HackerOne*** is a community of ethical hackers where you can find active bug bounties to participate in.

---

#additional-info 
## 4.07 - Additional Information

- [NIST National Vulnerability Database](https://nvd.nist.gov/)

---
