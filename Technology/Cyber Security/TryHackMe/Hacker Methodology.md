
## Contents :-

#### [[#01 - Reconnaissance]]
#### [[#02 - Scanning and Enumeration]]
#### [[#03 - Exploitation Phase]]
#### [[#04 - Privilege Escalation]]
#### [[#05 - Covering Tracks]]
#### [[#06 - Reporting]]

---

## 01 - Reconnaissance

- **Reconnaissance** - collecting information about the target. It involves no interaction with the target.
- Tools used:
	- Google (specifically Google Dorking)
	- Wikipedia
	- PeopleFinder.com
	- who.is
	- sublist3r
	- hunter.io
	- builtwith.com
	- wappalyzer

---

## 02 - Scanning and Enumeration

- **Scanning and Enumerating** - interacting with the target to attempt to find vulnerabilities related to the target. Attacker tries to determine the overall attack surface. The attack surface determines what the target might be vulnerable to in the Exploitation phase.
- Tools used:
	- nmap
	- dirb
	- dirbuster
	- metasploit
	- exploit-db
	- Burp Suite
	- enum4linux

---

## 03 - Exploitation Phase

- Attacker exploits the vulnerabilities found.
- A professional penetration tester never jumps into the exploitation phase without doing adequate *reconnaissance* and *enumeration*.
- Tools used:
	- Metasploit
	- BeEF
	- Burp Suite
	- SQLMap

---

## 04 - Privilege Escalation

- After gaining access to a victim machine via the *exploitation* phase, the next step is to escalate privileges to a higher user account. 
- The following accounts are what we try to reach as a pentester:
	- In Windows: **Administrator or System**
	- In Linux: **root**

---

## 05 - Covering Tracks

- While ethical hackers rarely have a need to cover their tracks, you still must carefully track and notate all of the tasks that you performed as part of the penetration test to assist in fixing the vulnerabilities and recommending changes to the system owner.

---

## 06 - Reporting

- Outline everything that is found including:
	- The Finding(s) or Vulnerabilities
	- The CRITICALITY of the Finding
	- A description or brief overview of how the finding was discovered
	- Remediation recommendations to resolve the finding
	
- A findings report generally goes in three formats:
	- Vulnerability scan results (a simple listing of vulnerabilities)
	- Findings summary (list of the findings as outlined above)
	- Full formal report.

---
