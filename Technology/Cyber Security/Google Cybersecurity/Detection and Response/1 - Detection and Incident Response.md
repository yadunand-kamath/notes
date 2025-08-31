
#incident-response

## Contents:-

#### [[#1.01 - Incident Response Lifecycle]]
#### [[#1.02 - Incident Response Operations]]
#### [[#1.03 - Incident Response Tools]]
#### [[#1.04 - Additional Information]]

---

## 1.01 - Incident Response Lifecycle

1. Preparation
2. Detection and Analysis
3. Containment, Eradication and Recovery
4. Post-incident Activity

- **Incident** - an occurrence that actually or imminently jeopardizes, without lawful authority, the confidentiality, integrity or availability of information or an information system; or constitutes a violation or imminent threat of violation of law, security policies or procedures.
- **Event** - an observable occurrence on a network, system or device. All incidents are events but not all events are incidents.
- **Incident handler's journal** - a form of documentation used in incident response

### 5 W's of an Incident

- Who triggered the event
- What happened
- When the incident took place
- Where the incident took place 
- Why the incident occurred

---

## 1.02 - Incident Response Operations

### 1.02.01 - Computer Security Incident Response Team

- **CSIRT**(***Computer Security Incident Response Team***) - a specialized group of security professionals that are trained in incident management and response.
- **Command** - having appropriate leadership and direction
- **Control** - ability to manage technical aspects, coordinating resources and assigning tasks
- **Communication** - ability to keep stakeholders informed

#### Roles in CSIRT

- Security Analyst - continuously monitor for security threats
- Technical Lead - managing all technical aspects like applying software patches and updates
- Incident Coordinator - coordinate with relevant departments during a security incident

### 1.02.02 - Security Operations Center

#SOC 

A **SOC**(***Security Operations Center***) is an organizational unit dedicated to monitoring networks, systems and devices for security threats or attacks. It is involved in various blue team activities.

#### SOC Organization

![[SOC organization.png]]


1. **Tier 1 SOC Analyst**
	- monitoring, reviewing and prioritizing alerts based on criticality or severity
	- creating and closing alerts using ticketing systems
	- escalating tickets to Tier 2 or Tier 3

2. **Tier 2 SOC Analyst**
	- receiving escalated tickets from L1 and conducting deeper investigations
	- configuring and refining security tools
	- reporting to SOC Lead

3. **Tier 3 SOC Lead**
	- managing operations of their team
	- exploring methods of detection by performing advanced detection techniques
	- reporting to SOC Manager

4. **SOC Manager**
	- hiring, training, and evaluating SOC team members
	- creating performance metrics and managing the performance of SOC team
	- developing reports related to incidents, compliance, and auditing
	- communicating findings to stakeholders

***OPTIONAL:***

5. **Forensic Investigators**
	- L2s and L3s who collect, preserve and analyze digital evidence related to security incidents

6. **Threat Hunters**
	- L3s who work to detect, analyze, and defend against new and advanced cyber threats using threat intelligence

---

## 1.03 - Incident Response Tools

### 1.03.01 - Detection and Management tools

- **IDS**(***Intrusion Detection System***) - an application that monitors system and network activity and produces alerts on possible intrusions.
- **IPS**(***Intrusion Prevention Systems***) - an application that monitors system activity for intrusions and take action to stop the activity.
- **EDR**(***Endpoint Detection and Response***) - an application that monitors an endpoint for malicious activity. An **endpoint** is any device connected on a network.

#### IDS and IPS tools

- Snort
- Zeek
- Kismet
- Sagan
- Suricata

#### Detection Categories

1. **True Positive** - an alert that correctly detects the presence of an attack
2. **True Negative** - no malicious activity exists, no malicious activity is detected and no alert is triggered
3. **False Positive** - an alert that incorrectly detects the presence of a threat. This is when an IDS identifies an activity as malicious, but it isn't.
4. **False Negative** - malicious activity happens but its presence is not detected.

### 1.03.02 - Documentation tools
	
 - **Documentation** is any form of recorded content that is used for a specific purpose

#### Types of Documentation

- Playbooks
- Incident handler's journal
- Policies
- Plans
- Final reports

#### Word Processor Tools

- Google Docs
- OneNote
- Evernote
- Notepad++

#### Ticketing System

- Jira

### 1.03.03 - Investigative tools

- **SIEM**(***Security Information and Event Management***) - an application that collects and analyzes log data to monitor critical activities in an organization.
- **SOAR**(***Security Orchestration, Automation and Response***) - a collection of applications, tools, and workflows that uses automation to respond to security events
#### SIEM Process

1. Collect and aggregate data
2. Normalize data
3. Analyze data

#### SIEM Tools

- AlienVault OSSIM
- Chronicle
- Elastic
- Exabeam
- IBM QRadar Security Intelligence Platform
- LogRythm
- Splunk

---

#additional-info 

## 1.04 - Additional Information

- [The SOC Ecosystem](https://chronicle.security/blog/posts/soc-ecosystem-infographic)
- [Cyber Career Pathways Tool](https://niccs.cisa.gov/workforce-development/cyber-career-pathways-tool)

---
