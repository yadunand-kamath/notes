
#attacks

## Contents :-

#### [[#2.01 - Common Attacks]]
#### [[#2.02 - CISSP Security Domains]]
#### [[#2.03 - Attack Types]]
#### [[#2.04 - Threat Actor Types]]
#### [[#2.05 - Hacker Types]]
#### [[#2.06 - Additional Information]]

---

## 2.01 - Common Attacks

### 2.01.01 - Phishing

#phishing

Phishing is the use of digital communications to trick people into revealing sensitive data or deploying malicious software. 

Some of the most common types of phishing attacks today include: 

- **BEC**(***Business Email Compromise***): A threat actor sends an email message that seems to be from a known source to make a seemingly legitimate request for information, in order to obtain a financial advantage.

- **Spear phishing**: A malicious email attack that targets a specific user or group of users. The email seems to originate from a trusted source.

- **Whaling**: A form of spear phishing. Threat actors target company executives to gain access to sensitive data.

- **Vishing**: The exploitation of electronic voice communication to obtain sensitive information or to impersonate a known source.

- **Smishing**: The use of text messages to trick users, in order to obtain sensitive information or to impersonate a known source.

### 2.01.02 - Malware

#malware

Malware is software designed to harm devices or networks. The primary purpose of malware is to obtain money, or in some cases, an intelligence advantage that can be used against a person, an organization, or a territory.  

Some of the most common types of malware attacks: 

- **Viruses**: Malicious code written to interfere with computer operations and cause damage to data, software, and hardware. A virus attaches itself to programs or documents, on a computer. It then spreads and infects one or more computers in a network.

- **Worms**: Malware that can duplicate and spread itself across systems on its own. 

- **Ransomware**: A malicious attack where threat actors encrypt an organization's data and demand payment to restore access. 

- **Spyware**: Malware that’s used to gather and sell information without consent. Spyware can be used to access devices. This allows threat actors to collect personal data, such as private emails, texts, voice and image recordings, and locations.

### 2.01.03 - Social Engineering 

#socialengineering

Social engineering is a manipulation technique that exploits human error to gain private information, access, or valuables. Human error is usually a result of trusting someone without question. It’s the mission of a threat actor, acting as a social engineer, to create an environment of false trust and lies to exploit as many people as possible. 

Some of the most common types of social engineering attacks today include:

- **Social media phishing**: A threat actor collects detailed information about their target from social media sites. Then, they initiate an attack.

- **Watering hole attack**: A threat actor attacks a website frequently visited by a specific group of users.

- **USB baiting**: A threat actor strategically leaves a malware USB stick for an employee to find and install, to unknowingly infect a network. 

- **Physical social engineering**: A threat actor impersonates an employee, customer, or vendor to obtain unauthorized access to a physical location.

#### Social engineering principles 

Social engineering is incredibly effective. This is because people are generally trusting and conditioned to respect authority. The number of social engineering attacks is increasing with every new social media application that allows public access to people's data. Although sharing personal data—such as your location or photos—can be convenient, it’s also a risk.

Reasons why social engineering attacks are effective include:

- **Authority**: Threat actors impersonate individuals with power. This is because people, in general, have been conditioned to respect and follow authority figures. 

- **Intimidation**: Threat actors use bullying tactics. This includes persuading and intimidating victims into doing what they’re told. 

- **Consensus/Social proof**: Because people sometimes do things that they believe many others are doing, threat actors use others’ trust to pretend they are legitimate. For example, a threat actor might try to gain access to private data by telling an employee that other people at the company have given them access to that data in the past. 

- **Scarcity**: A tactic used to imply that goods or services are in limited supply. 

- **Familiarity**: Threat actors establish a fake emotional connection with users that can be exploited. 

- **Trust**: Threat actors establish an emotional relationship with users that can be exploited over time. They use this relationship to develop trust and gain personal information.

- **Urgency**: A threat actor persuades others to respond quickly and without questioning

---

#cissp #securitydomains

## 2.02 - CISSP Security Domains

**CISSP**(***Certified Information Systems Security Professional***) security domains categorize a security analyst's job duties.

1. **Security and Risk Management**
	- define security goals and objectives, risk mitigation, compliance, business continuity, and the law
2. **Asset Security** 
	- secure digital and physical assets 
	- also related to storage, maintenance, retention and destruction of data
3. **Security Architecture and Engineering**
	- optimize data security by ensuring effective tools, systems and processes in place
4. **Communications and Network Security**
	- manage and secure physical networks and wireless communications
5. **Identity and Access Management**
	- keep data secure by ensuring users follow established policies to control and manage physical assets, like office spaces, and logical assets, such as networks and applications
6. **Security Assessment and Testing**
	- conduct security control testing, collect and analyze data, and conduct security audits to monitor for risks, threats and vulnerabilities
7. **Security Operations**
	- conduct investigations and implement preventative measures
8. **Software Development Security**
	- use secure coding practices, which are a set of recommended guidelines that are used to create secure applications and services

---

## 2.03 - Attack Types

### 2.03.01 - Password attack

A password attack is an attempt to access password-secured devices, systems, networks, or data. 

Some forms of password attacks are:  
- Brute force
- Rainbow table

Password attacks fall under the communication and network security domain. 

### 2.03.02 - Social engineering attack

Social engineering is a manipulation technique that exploits human error to gain private information, access, or valuables. 

Some forms of social engineering attacks are: 
- Phishing
- Smishing
- Vishing
- Spear phishing
- Whaling
- Social media phishing
- Business Email Compromise (BEC)
- Watering hole attack
- USB (Universal Serial Bus) baiting
- Physical social engineering 

Social engineering attacks are related to the security and risk management domain.

### 2.03.03 - Physical attack

A physical attack is a security incident that affects not only digital but also physical environments where the incident is deployed. 

Some forms of physical attacks are:
- Malicious USB cable
- Malicious flash drive
- Card cloning and skimming

Physical attacks fall under the asset security domain. 

### 2.03.04 - Adversarial artificial intelligence

- Adversarial artificial intelligence is a technique that manipulates artificial intelligence and machine learning  technology to conduct attacks more efficiently. 
- Adversarial artificial intelligence falls under both the communication and network security and the identity and access management domains.

[NIST - Adversarial Machine Learning](https://www.nccoe.nist.gov/ai/adversarial-machine-learning)

### 2.03.05 - Supply-chain attack

A supply-chain attack targets systems, applications, hardware, and/or software to locate a vulnerability where malware can be deployed. Because every item sold undergoes a process that involves third parties, this means that the security breach can occur at any point in the supply chain. These attacks are costly because they can affect multiple organizations and the individuals who work for them. 

Supply-chain attacks can fall under several domains, including but not limited to the security and risk management, security architecture and engineering, and security operations domains.

### 2.03.06 - Cryptographic attack

A cryptographic attack affects secure forms of communication between a sender and intended recipient. 

Some forms of cryptographic attacks are: 
- Birthday
- Collision
- Downgrade

Cryptographic attacks fall under the communication and network security domain. 

---

#threat-actor

## 2.04 - Threat Actor Types

### 2.04.01 - Advanced persistent threats

Advanced persistent threats (APTs) have significant expertise accessing an organization's network without authorization. APTs tend to research their targets (e.g., large corporations or government entities)  in advance and can remain undetected for an extended period of time. 
Their intentions and motivations can include:
- Damaging critical infrastructure, such as the power grid and natural resources
- Gaining access to intellectual property, such as trade secrets or patents

### 2.04.02 - Insider threats

Insider threats abuse their authorized access to obtain data that may harm an organization. 
Their intentions and motivations can include: 
- Sabotage
- Corruption
- Espionage
- Unauthorized data access or leaks 

### 2.04.03 - Hacktivists

Hacktivists are threat actors that are driven by a political agenda. They abuse digital technology to accomplish their goals, which may include: 
- Demonstrations
- Propaganda
- Social change campaigns
- Fame

---

#hackers

## 2.05 - Hacker Types

A hacker is any person who uses computers to gain access to computer systems, networks, or data. They can be beginner or advanced technology professionals who use their skills for a variety of reasons. 

There are three main categories of hackers:

**Authorized hackers** are also called **ethical hackers**. They follow a code of ethics and adhere to the law to conduct organizational risk evaluations. They are motivated to safeguard people and organizations from malicious threat actors.

**Semi-authorized hackers** are considered **researchers**. They search for vulnerabilities but don’t take advantage of the vulnerabilities they find.

**Unauthorized hackers** are also called **unethical hackers**. They are malicious threat actors who do not follow or respect the law. Their goal is to collect and sell confidential data for financial gain. 

Note: There are multiple hacker types that fall into one or more of these three categories.

New and unskilled threat actors have various goals, including: 
- To learn and enhance their hacking skills
- To seek revenge
- To exploit security weaknesses by using existing malware, programming scripts, and other tactics 

Other types of hackers are not motivated by any particular agenda other than completing the job they were contracted to do. These types of hackers can be considered unethical or ethical hackers. They have been known to work on both illegal and legal tasks for pay.

There are also hackers who consider themselves vigilantes. Their main goal is to protect the world from unethical hackers.

---

#additional-info 

## 2.06 - Additional Information

![[gcat_threathorizons_full_sept2022.pdf]]


---
