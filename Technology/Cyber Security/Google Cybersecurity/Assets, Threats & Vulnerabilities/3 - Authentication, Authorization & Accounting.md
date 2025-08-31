
## Contents :-

#### [[#3.01 - AAA Framework]]
#### [[#3.02 - User provisioning]]
#### [[#3.03 - Additional Information]]

---

## 3.01 - AAA Framework

- **Access Controls** - security controls that manage access, authorization and accountability of information.

### 3.01.01 - **Authentication**

#authentication

1. **Knowledge** - something the user knows
2. **Ownership** - something the user possesses
3. **Characteristic** - something the user is 

#### SSO (*Single Sign-On*) 

#SSO #LDAP #SAML

- a technology that combines several different logins into one.
- SSO solutions use trusted third-parties to prove that a user is who they claim to be. This is done through the exchange of encrypted access tokens between the identity provider and the service provider.
- SSO implementations commonly rely on two different authentication protocols: LDAP and SAML. 
- **LDAP**(***Lightweight Directory Access Protocol***) is mostly used to transmit information on-premises
- **SAML**(***Security Assertion Markup Language***) is mostly used to transmit information off-premises, like in the cloud.
- LDAP and SAML protocols are often used together.

#### MFA(*Multi Factor Authentication*) 

- a security measure that requires a user to verify their identity in two or more ways to access a system/network.

### 3.01.02 - **Authorization**

#authorization

- **Principle of Least Privileges** - a user is only granted the minimum level of access and authorization required to complete a task or function.
- **Separation of Duties** - the principle that users should not be given levels of authorization that would allow them to misuse a system.
- **Basic Auth** - technology used to establish a user's request to access a server
- **OAuth** - an open-standard authorization protocol that shares designated access between applications 
- **API Token** - a small block of encrypted code that contains information about a user.
	
### 3.01.03 - **Accounting**

#accounting

- **Session** - a sequence of network HTTP basic auth requests and responses associated with the same user.
- **Session ID** - a unique token that identifies a user and their device while accessing the system.
- **Session Cookie** - a token that websites use to validate a session and determine how long that session should last.
- **Session Hijacking** - an event when attackers obtain a legitimate user's session ID.

---

## 3.02 - User provisioning

- Back-end systems need to be able to verify whether the information provided by a user is accurate. To accomplish this, users must be properly provisioned. 
- User provisioning is the process of creating and maintaining a user's digital identity. 
- For example, a college might create a new user account when a new instructor is hired. The new account will be configured to provide access to instructor-only resources while they are teaching. 
- Security analysts are routinely involved with provisioning users and their access privileges.

***NOTE***: Another role analysts have in **IAM**(***Identity Access Management***) is to deprovision users. This is an important practice that removes a user's access rights when they should no longer have them.

### 3.02.01 - Granting authorization

- If the right user has been authenticated, the network should ensure the right resources are made available. 
- There are three common frameworks that organizations use to handle this step of IAM:

1. **MAC**(***Mandatory Access Control***)
	- MAC is the strictest of the three frameworks. 
	- Authorization in this model is based on a strict need-to-know basis. 
	- Access to information must be granted manually by a central authority or system administrator. 
	- For example, MAC is commonly applied in law enforcement, military, and other government agencies where users must request access through a chain of command. 
	- MAC is also known as non-discretionary control because access isn’t given at the discretion of the data owner.

2. **DAC**(***Discretionary Access Control***)
	- DAC is typically applied when a data owner decides appropriate levels of access. 
	- One example of DAC is when the owner of a Google Drive folder shares editor, viewer, or commentor access with someone else.

3. **RBAC**(***Role-based Access Control***)
	- RBAC is used when authorization is determined by a user's role within an organization. 
	- For example, a user in the marketing department may have access to user analytics but not network administration.

---

#additional-info 

## 3.03 - Additional Information

- [IDPro](https://idpro.org/) - a professional organization dedicated to sharing essential IAM industry knowledge.

---
