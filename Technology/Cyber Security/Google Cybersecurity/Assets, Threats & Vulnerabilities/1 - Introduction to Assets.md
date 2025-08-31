
#assets

## Contents :-

#### [[#1.01 - Asset Security]]
#### [[#1.02 - Asset Classification]]
#### [[#1.03 - Digital Assets]]
#### [[#1.04 - Risk and Asset Security]]
#### [[#1.05 - Security Controls]]
#### [[#1.06 - Data Lifecycle]]

---

## 1.01 - Asset Security

**Risk** - anything that can impact the confidentiality, integrity, or availability of an asset.

### 1.01.01 - Security Risk Planning 

**Security plans** are all about how an organization defines risk. 

- **Assets** (what) - an item of value 
- **Threats** (why) - any circumstance/event that can negatively impact assets
- **Vulnerabilities** (how) - a weakness that can be exploited by a threat

---

## 1.02 - Asset Classification

- **Asset Management** - process of tracking assets and the risks that affect them. You can only protect what you know you have. 
- **Asset Inventory** - a catalog of assets that need to be protected
- **Asset Classification** - practice of labeling assets based on sensitivity and importance to an organization
 
### 1.02.01 - Levels of Asset Classification

- **Restricted** is the highest level. This category is reserved for incredibly sensitive assets, like need-to-know information.
- **Confidential** refers to assets whose disclosure may lead to a significant negative impact on an organization.
- **Internal-only** describes assets that are available to employees and business partners.
- **Public** is the lowest level of classification. These assets have no negative consequences to the organization if they’re released. 

---

## 1.03 - Digital Assets 

Digital assets contain data.

#### States of Data 

- **In use** - data being accessed by one or more users.
- **In transit** - data travelling from one point to another. 
- **At rest** - data currently not being accessed.

- **InfoSec**(***Information Security***) - practice of keeping data in all states away from unauthorized users.

---

## 1.04 - Risk and Asset Security 

### Types of risk categories 

- Damage
- Disclosure 
- Loss of information 

### Elements of Security Plan 

1. **Policies** - a set of rules that reduces risk and protects information  
2. **Standards** - references that inform how to set policies 
3. **Procedures** - step-by-step instructions to perform a specific security task

- **Compliance** - process of adhering to internal standards and external regulations
- **Regulations** - rules set by a government or other authority to control the way something is done 

### NIST CSF Components

#### Core 

- The CSF core is a set of desired cybersecurity outcomes that help organizations customize their security plan. It consists of five functions:
	1. Identify
	2. Protect
	3. Detect
	4. Respond
	5. Recover
- These functions are commonly used as an informative reference to help organizations identify their most important assets and protect those assets with appropriate safeguards. 
- The CSF core is also used to understand ways to detect attacks and develop response and recovery plans should an attack happen.
	
#### Tiers

- The CSF tiers are a way of measuring the sophistication of an organization's cybersecurity program. 
- CSF tiers are measured on a scale of 1 to 4. Tier 1 is the lowest score, indicating that a limited set of security controls have been implemented. 
- Overall, CSF tiers are used to assess an organization's security posture and identify areas for improvement.

#### Profiles

- The CSF profiles are pre-made templates of the NIST CSF that are developed by a team of industry experts. CSF profiles are tailored to address the specific risks of an organization or industry. 
- They are used to help organizations develop a baseline for their cybersecurity plans, or as a way of comparing their current cybersecurity posture to a specific industry standard.

---

## 1.05 - Security Controls

**Security Controls** are safeguards designed to reduce specific security risks.

### 1.05.01 - Types of Security Controls:

- Operational
- Managerial
- Technical

### 1.05.02 - Types of User Accounts:

- **Guest accounts** - provided to external users who need to access an internal network, like customers, clients, contractors, or business partners.
- **User accounts** - assigned to staff based on their job duties.
- **Service accounts** - granted to applications or software that needs to interact with other software on the network.
- **Privileged accounts** - have elevated permissions or administrative access.

### 1.05.03 - Auditing Account Privileges

There are three common approaches to auditing user accounts:

1. **Usage audits**
	- The security team will review which resources each account is accessing and what the user is doing with the resource. 
	- Usage audits can help determine whether users are acting in accordance with an organization’s security policies. 
	- They can also help identify whether a user has permissions that can be revoked because they are no longer being used.
2. **Privilege audits**
	- Users tend to accumulate more access privileges than they need over time, an issue known as ***privilege creep***. 
	- This might occur if an employee receives a promotion or switches teams and their job duties change. 
	- Privilege audits assess whether a user's role is in alignment with the resources they have access to.
3. **Account change audits**
	- Account directory services keep records and logs associated with each user. 
	- Changes to an account are usually saved and can be used to audit the directory for suspicious activity, like multiple attempts to change an account password. 
	- Performing account change audits helps to ensure that all account changes are made by authorized users.
	
---

## 1.06 - Data Lifecycle

#### Collect -> Store -> Use -> Archive -> Destroy

**Data governance** - a set of processes that define how an organization manages information. Governance often includes policies that specify how to keep data private, accurate, available, and secure throughout its lifecycle.

Effective data governance is a collaborative activity that relies on people. Data governance policies commonly categorize individuals into a specific role:
- **Data owner**: the person that decides who can access, edit, use, or destroy their information.
- **Data custodian**: anyone or anything that's responsible for the safe handling, transport, and storage of information.
- **Data steward**: the person or group that maintains and implements data governance policies set by an organization.

Security and privacy are two terms that often get used interchangeably outside of this field. Although the two concepts are connected, they represent specific functions:

- **Information privacy** refers to the protection of unauthorized access and distribution of data.
- **Information security**(***InfoSec***) refers to the practice of keeping data in all states away from unauthorized users.

The key difference: Privacy is about providing people with control over their personal information and how it's shared. Security is about protecting people’s choices and keeping their information safe from potential threats.

---
