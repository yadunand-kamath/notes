
## Contents:-

#### [[#3.01 - Incident Detection and Verification]]
#### [[#3.02 - Tools]]
#### [[#3.03 - Response and Recovery]]
#### [[#3.04 - Post-incident Activity]]
#### [[#3.05 - Additional Information]]

---

## 3.01 - Incident Detection and Verification

- **Detection** - the prompt discovery of security events
- **Analysis** - the investigation and validation of alerts
- **IoC** (***Indicators of Compromise***) are observable evidence that suggests signs of a potential security incident. IoCs help identify the *who* and *what* of an attack after it's taken place.
- **IoA** (***Indicators of Attack***) are the series of observed events that indicate a real-time incident. IoAs focus on finding the *why* and *how* of an ongoing or unknown attack.
- **Crowdsourcing** is the practice of gathering information using public input and collaboration.
- **ISACs** (***Information Sharing and Analysis Centers***) focus on collecting and sharing sector-specific threat intelligence to companies within specific industries like energy, healthcare, and others.
- **OSINT** (***Open-Source Intelligence***) is the collection and analysis of information from publicly available sources to generate usable intelligence. 
### 3.01.01 - Challenges in Detection and Analysis Phase

- impossible to detect everything
- high volumes of alerts
- detection tools are not perfect

### 3.01.02 - Methods of Detection

- **Threat Hunting** - it is the proactive search for threats on a network to uncover malicious activity and detect threats before they cause damage. Threat hunting specialists are known as *Threat Hunters*.
- **Threat Intelligence** - evidence-based threat information that provides context about existing or emerging threats. **TIP** (***Threat Intelligence Platform***) can be leveraged to collect, centralize, and analyze threat intelligence from different sources.
- **Cyber Deception** - involves techniques that deliberately deceive malicious actors with the goal of increasing detection and improving defense strategies. *Example:* **Honeypots** are systems or resources that are created as decoys vulnerable to attacks with the purpose of attracting potential intruders.

### 3.01.03 - Pyramid of Pain

Not all IoC's are equal in the value they provide to security teams. It’s important for security professionals to understand the different types of IoC's so that they can quickly and effectively detect and respond to them. This is why security researcher David J. Bianco created the concept of the Pyramid of Pain, with the goal of improving how indicators of compromise are used in incident detection.

![[pyramid of pain.png]]

The Pyramid of Pain captures the relationship between indicators of compromise and the level of difficulty that malicious actors experience when indicators of compromise are blocked by security teams. It lists the different types of indicators of compromise that security professionals use to identify malicious activity. 
Each type of indicator of compromise is separated into levels of difficulty. These levels represent the “pain” levels that an attacker faces when security teams block the activity associated with the indicator of compromise.

1. **Hash values** - Hashes that correspond to known malicious files. These are often used to provide unique references to specific samples of malware or to files involved in an intrusion.
2. **IP addresses** - An internet protocol address like 192.168.1.1
3. **Domain names** - A web address such as www.google.com 
4. **Network artifacts** - Observable evidence created by malicious actors on a network. For example, information found in network protocols such as User-Agent strings. 
5. **Host artifacts** - Observable evidence created by malicious actors on a host. A host is any device that’s connected on a network. For example, the name of a file created by malware.
6. **Tools** - Software that’s used by a malicious actor to achieve their goal. For example, attackers can use password cracking tools like John the Ripper to perform password attacks to gain access into an account.
7. **TTPs**(***Tactics, Techniques, and Procedures***) - This is the behavior of a malicious actor. Tactics refer to the high-level overview of the behavior. Techniques provide detailed descriptions of the behavior relating to the tactic. Procedures are highly detailed descriptions of the technique. TTPs are the hardest to detect.

---

## 3.02 - Tools

- [Virus Total](https://www.virustotal.com/gui/home/upload) is a service that allows anyone to analyze suspicious files, domains, URLs, and IP addresses for malicious content.
- [Jotti's Malware Scan](https://virusscan.jotti.org) is a free service that lets you scan suspicious files with several anti-virus programs.
- [urlscan.io](https://urlscan.io) is a free service that scans and analyzes URLs and provides a detailed report summarizing the URL information.
- CAPE Sandbox is an open source service used to automate the analysis of suspicious files. Using an isolated environment, malicious files such as malware are analyzed and a comprehensive report outlines the malware behavior.
- [MalwareBazaar](https://bazaar.abuse.ch/browse/) is a free repository for malware samples. Malware samples are a great source of threat intelligence that can be used for research purposes. 

---

## 3.03 - Response and Recovery

- **Triage** - the prioritizing of incidents according to their level of importance or urgency

### 3.03.01 - Triage Process

1. Receive and assess
2. Assign priority
3. Collect and analyze

- **Containment** - the act of limiting and preventing additional damage caused by an incident.
- **Eradication** - complete removal of the incident elements from all affected systems.
- **Recovery** - the process of returning affected systems back to normal operations.
- **BCP** (***Business Continuity Plan***) - a document that outlines the procedures to sustain business operations during and after a significant disruption.

---

## 3.04 - Post-incident Activity

The process of reviewing an incident to identify areas for improvement during incident handling.

- **Final Report** - documentation that provides a comprehensive review of an incident. It can include an executive summary, timeline, investigation and recommendations.

---

#additional-info 
## 3.05 - Additional Information

- [The Threat Hunting Project](https://www.threathunting.net/)
- [Threat Analysis Group(TAG)](https://blog.google/threat-analysis-group/)
- [Pyramid of Pain](http://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html)

---
