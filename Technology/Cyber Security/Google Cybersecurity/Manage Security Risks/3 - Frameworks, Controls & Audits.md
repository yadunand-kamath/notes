
## Contents :-

#### [[#3.01 - Controls]]
#### [[#3.02 - NIST Frameworks]]
#### [[#3.03 - OWASP Security Principles]]
#### [[#3.04 - Security Audits]]
#### [[#3.05 - Additional Information]]

---

#security-controls

## 3.01 - Controls

Controls are used alongside frameworks to reduce the possibility and impact of a security threat, risk, or vulnerability.

1. Physical controls
2. Technical controls
3. Administrative controls

- **Encryption** - process of converting data from a readable format (plaintext) to an encoded format (ciphertext)
- **Authentication** - process of verifying who someone or something is
- **Authorization** - granting access to specific resources within a system 

---

## 3.02 - NIST Frameworks

### NIST CSF (Cybersecurity Framework)

#nist-csf

A voluntary framework that consists of standards, guidelines, and best practices to manage cybersecurity risk.

1. **Identify** - management of cybersecurity risk and its effect on an organization's people and assets
2. **Protect** - strategy used to protect an organization through implementation of policies, procedures, training, and tools that help mitigate threats
3. **Detect** - identifying potential security incidents and improving monitoring capabilities to increase speed and efficiency of detections
4. **Respond** - ensure suitable procedures are used to contain, neutralize, and analyze security incidents, and implement improvements to the security process
5. **Recover** - process of returning affected systems back to normal working operations

---

#owasp

## 3.03 - OWASP Security Principles

- **Minimize attack surface area**: Attack surface refers to all the potential vulnerabilities a threat actor could exploit.
- **Principle of least privilege**: Users have the least amount of access required to perform their everyday tasks.
- **Defense in depth**: Organizations should have varying security controls that mitigate risks and threats.
- **Separation of duties**: Critical actions should rely on multiple people, each of whom follow the principle of least privilege. 
- **Keep security simple**: Avoid unnecessarily complicated solutions. Complexity makes security difficult. 
- **Fix security issues correctly**: When security incidents occur, identify the root cause, contain the impact, identify vulnerabilities, and conduct tests to ensure that remediation is successful.
- **Establish secure defaults**: This principle means that the optimal security state of an application is also its default state for users; it should take extra work to make the application insecure. 
- **Fail securely**: Fail securely means that when a control fails or stops, it should do so by defaulting to its most secure option. For example, when a firewall fails it should simply close all connections and block all new ones, rather than start accepting everything.
- **Don’t trust services**: Many organizations work with third-party partners. These outside partners often have different security policies than the organization does. And the organization shouldn’t explicitly trust that their partners’ systems are secure. 
- **Avoid security by obscurity**: The security of key systems should not rely on keeping details hidden. Consider the following example from OWASP (2016) - The security of an application should not rely on keeping the source code secret. Its security should rely upon many other factors, including reasonable password policies, defense in depth, business transaction limits, solid network architecture, and fraud and audit controls.

---

#security-audits

## 3.04 - Security Audits

- A security audit is a review of an organization's security controls, policies, and procedures against a set of expectations. 
- Audits are independent reviews that evaluate whether an organization is meeting internal and external criteria. 
- Internal criteria include outlined policies, procedures, and best practices. 
- External criteria include regulatory compliance, laws, and federal regulations. 
- Audits help ensure that security checks are made (i.e., daily monitoring of security information and event management dashboards), to identify threats, risks, and vulnerabilities. This helps maintain an organization’s security posture. And, if there are security issues, a remediation process must be in place.

### Goals and objectives of an audit

- The goal of an audit is to ensure an organization's information technology (IT) practices are meeting industry and organizational standards. 
- The objective is to identify and address areas of remediation and growth. 
- Audits provide direction and clarity by identifying what the current failures are and developing a plan to correct them.

### Audit checklist

A checklist is generally made up of the following areas of focus:

1. Identify the scope of the audit
	- List assets that will be assessed (e.g., firewalls are configured correctly, PII is secure, physical assets are locked, etc.) 
	- Note how the audit will help the organization achieve its desired goals
	- Indicate how often an audit should be performed
	- Include an evaluation of organizational policies, protocols, and procedures to make sure they are working as intended and being implemented by employees

2. Complete a risk assessment
	- A risk assessment is used to evaluate identified organizational risks related to budget, controls, internal processes, and external standards (i.e., regulations).

3. Conduct the audit
	 - When conducting an internal audit, you will assess the security of the identified assets listed in the audit scope.

4. Create a mitigation plan
	- A mitigation plan is a strategy established to lower the level of risk and potential costs, penalties, or other issues that can negatively affect the organization’s security posture. 

5. Communicate results to stakeholders
	- The end result of this process is providing a detailed report of findings, suggested improvements needed to lower the organization's level of risk, and compliance regulations and standards the organization needs to adhere to.

---

#additional-info 

## 3.05 - Additional Information

[Assessment & Auditing Resources](https://www.nist.gov/cyberframework/assessment-auditing-resources)

[IT Disaster Recovery Plan](https://www.ready.gov/it-disaster-recovery-plan)


![[Control-categories.pdf]]


![[Botium Toys - Audit & Scope Goals.pdf]]


![[Botium Toys - Risk Assessment.pdf]]


![[Botium Toys - Control Assessment.pdf]]


![[Botium Toys - Control Assessment Exemplar.pdf]]


![[Botium Toys - Compliance Checklist.pdf]]


![[Botium Toys - Compliance Checklist Exemplar.pdf]]


![[Botium Toys - Stakeholder Memorandum.pdf]]


![[Botium Toys - Stakeholder Memorandum Exemplar.pdf]]


---
