
## Contents :-

#### [[#2.01 - Introduction]]
#### [[#2.02 - Impacts of Threats, Risks and Vulnerabilities]]
#### [[#2.03 Layers of the Web]]
#### [[#2.04 - NIST RMF]]
#### [[#2.05 - Additional Information]]

---

## 2.01 - Introduction

### Threat

#threat

Any circumstance or event that can negatively impact assets.

Some common threats:
- **Insider threats** - members of an organization abuse their authorized access
- **APTs** (*Advanced Persistent Threats*) - a threat actor maintains unauthorized access for an extended period of time

### Risk

#risk

- Anything that can impact the confidentiality, integrity, or availability of an asset.
- It is the likelihood of a threat occurring.
- ==A risk is only present if there is a vulnerability and a threat==.

1. **Low-risk asset** 
	- Information that would not harm the organization's reputation or ongoing operations and would not cause financial damage if compromised.
2. **Medium-risk asset** 
	- Information that's not available to the public and may cause some damage to the organization's finances, reputation, or ongoing operations.
3. **High-risk asset**
	- Information protected by regulations or laws which of compromised would have a severe negative impact on an organization's finances, ongoing operations, or reputation.

There are different factors that can affect the likelihood of a risk to an organization’s assets, including:
- **External risk** - anything outside the organization that has the potential to harm organizational assets, such as threat actors attempting to gain access to private information.
- **Internal risk** - a current or former employee, vendor, or trusted partner who poses a security risk.
- **Legacy systems** - old systems that might not be accounted for or updated, but can still impact assets, such as workstations or old mainframe systems. For example, an organization might have an old vending machine that takes credit card payments or a workstation that is still connected to the legacy accounting system.
- **Multiparty risk** - outsourcing work to third-party vendors can give them access to intellectual property, such as trade secrets, software designs, and inventions.
- **Software compliance/licensing** - software that is not updated or in compliance, or patches that are not installed in a timely manner

#### Risk Management Strategies

- **Acceptance** - accepting a risk to avoid disrupting business continuity
- **Avoidance** - creating a plan to avoid the risk altogether
- **Transference** - transferring a risk to a third party to manage
- **Mitigation** - lessening the impact of a known risk

### Vulnerability

#vulnerability

A weakness that can be exploited by a threat.

Some vulnerabilities include:
- **ProxyLogon** - a pre-authenticated vulnerability that affects the Microsoft Exchange server. This means a threat actor can complete a user authentication process to deploy malicious code from a remote location.
- **ZeroLogon** - a vulnerability in Microsoft’s Netlogon authentication protocol. An authentication protocol is a way to verify a person's identity. Netlogon is a service that ensures a user’s identity before allowing access to a website's location.
- **Log4Shell** - allows attackers to run Java code on someone else’s computer or leak sensitive information. It does this by enabling a remote attacker to take control of devices connected to the internet and run malicious code.
- **PetitPotam** - affects Windows New Technology Local Area Network (LAN) Manager (NTLM). It is a theft technique that allows a LAN-based attacker to initiate an authentication request.
- **Security logging and monitoring failures** - insufficient logging and monitoring capabilities that result in attackers exploiting vulnerabilities without the organization knowing it.
- **Server-side request forgery** - allows attackers to manipulate a server-side application into accessing and updating backend resources. It can also allow threat actors to steal data.

---

## 2.02 - Impacts of Threats, Risks and Vulnerabilities

- Financial damage
- Reputational damage
- Identity theft 

### Ransomware

#ransomware

A malicious attack where the threat actors encrypt an organization's data and demand payment to restore access.

---

## 2.03 Layers of the Web

1. Surface web
2. Deep web
3. Dark web

---

#nist-rmf

## 2.04 - NIST RMF 

**Risk Management Framework:**
1. **Prepare**
	- activities to manage security and privacy risks before a breach occurs
2. **Categorize**
	- used to develop risk management processes and tasks
3. **Select**
	- choose, customize and capture documentation of the controls that protect an organization (ex: updating playbook)
4. **Implement**
	- implement security and privacy plans for the organization 
5. **Assess**
	- determine if established controls are implemented correctly and are sufficient to manage risks
6. **Authorize**
	- being accountable for the security and privacy risks that may exist in an organization
7. **Monitor**
	- be aware of how systems are operating

---

#additional-info 

## 2.05 - Additional Information

[NIST Cybersecurity Risks](https://www.nist.gov/itl/smallbusinesscyber/cybersecurity-basics/cybersecurity-risks)

[NIST - RMF](https://csrc.nist.gov/projects/risk-management/about-rmf)

[NIST - National Vulnerabilities Database](https://nvd.nist.gov/vuln)

[CISA - Known Vulnerabilities Catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog)

---
