
#penetration-testing

## Contents :-

#### [[#01 - ROE]]
#### [[#02 - Penetration Testing Methodologies]]
#### [[#03 - Penetration Testing Types]]
#### [[#04 - Principles of Security]]
#### [[#05 - Additional Information]]

---

## 01 - ROE

- **ROE**(***Rules of Engagement***) - a document that is created at the initial stages of a penetration testing engagement. 

This document consists of the following sections, which are ultimately responsible for deciding how the engagement is carried out:

1. **Permission**: This section of the document gives explicit permission for the engagement to be carried out. This permission is essential to legally protect individuals and organizations for the activities they carry out.
2. **Test Scope**: This section of the document will annotate specific targets to which the engagement should apply. For example, the penetration test may only apply to certain servers or applications but not the entire network.
3. **Rules**: The rules section will define exactly the techniques that are permitted during the engagement. For example, the rules may specifically state that techniques such as phishing attacks are prohibited, but MITM (Man-in-the-Middle) attacks are okay.

---

## 02 - Penetration Testing Methodologies


![[Pentesting Methodologies.png]]

---

## 03 - Penetration Testing Types


![[Pentesting Types.png]]

---

## 04 - Principles of Security

- **Defense in Depth** - the use of multiple varied layers of security to an organization's systems and data in the hopes that multiple layers will provide redundancy in an organization's security perimeter.
- According to a security model, any system or piece of technology storing information is called an information system.
- **Threat modelling** is the process of reviewing, improving, and testing the security protocols in place in an organization's information technology infrastructure and services.
- A breach of security is known as an **incident**. 
- Actions taken to resolve and remediate the threat are known as **Incident Response**.

### 04.01 - The Bell LaPadula Model

- The Bell-La Padula Model is used to achieve confidentiality. 
- This model has a few assumptions, such as an organization's hierarchical structure it is used in, where everyone's responsibilities/roles are well-defined.
- The model works by granting access to pieces of data (called objects) on a strictly need to know basis. This model uses the rule "no write down, no read up".

![[Bell LaPadula Model.png]]

![[bell lapadula table.png]]

### 04.02 - Biba Model

- The Biba model is arguably the equivalent of the Bell-La Padula model but for the integrity of the CIA triad.
- This model applies the rule to objects (data) and subjects (users) that can be summarized as "no write up, no read down". This rule means that subjects **can** create or write content to objects at or below their level but **can only** read the contents of objects above the subject's level.

![[Biba Model.png]]

![[biba model table.png]]

### 04.03 - STRIDE

 - **STRIDE** (***Spoofing identity, Tampering with data, Repudiation threats, Information disclosure, Denial of Service and Elevation of privileges***)

![[STRIDE.png]]


---
## 05 - Additional Information

- [SANS - Rules of Engagement Worksheet](https://sansorg.egnyte.com/dl/bF4I3yCcnt/)

---
