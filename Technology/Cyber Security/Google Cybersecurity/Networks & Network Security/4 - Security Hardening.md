
## Contents :-

#### [[#4.01 - Introduction to Security Hardening]]
#### [[#4.02 - OS Hardening]]
#### [[#4.03 - Network Hardening]]
#### [[#4.04 - Cloud Hardening]]

---

## 4.01 - Introduction to Security Hardening

Security hardening is the process of strengthening a system to reduce its vulnerability and attack surface.

**Attack Surface** - all potential vulnerabilities that a threat actor could exploit.

Security hardening is conducted on:
- hardware
- operating systems
- applications
- computer networks
- databases

### Security hardening procedures

- software updates/patches
- device updates/configuration changes
- improving encryption
- removing/disabling unused applications, services, ports
- reducing access permissions
- regular penetration testing

**Penetration Testing** - a simulated attack that helps identify vulnerabilities in systems, networks, websites, applications and processes.

---

## 4.02 - OS Hardening

**OS**(***Operating System***) is the interface between the computer hardware and the user.

### OS Hardening Measures

- **Patch Update** - an update that addresses security vulnerabilities within a program/product
- **Baseline Configuration (baseline image)** - a documented set of specifications within a system that is used as a basis for future builds, updates and releases.
- Secure hardware and software disposal 
- Strong password policy
- **MFA**(***Multi-Factor Authentication***) - a security measure which requires a user to verify their identity in two or more ways to access a system or network
	1. something you know 
	2. something you have 
	3. something unique about you 

### Brute force attacks

A brute force attack is a trial-and-error process of discovering private information. 

Types of brute force attacks: 

1. **Simple brute force attacks** - When attackers try to guess a user's login credentials, it’s considered a simple brute force attack. They might do this by entering any combination of usernames and passwords that they can think of until they find the one that works.
2. **Dictionary attacks** - attackers use a list of commonly used passwords and stolen credentials from previous breaches to access a system. These are called “dictionary” attacks because attackers originally used a list of words from the dictionary to guess the passwords, before complex password rules became a common security practice. 

Using brute force to access a system can be a tedious and time consuming process, especially when it’s done manually. There are a range of tools attackers use to conduct their attacks. 

### Assessing vulnerabilities

Analysts can use virtual machines and sandboxes to test suspicious files, check for vulnerabilities before an event occurs, or to simulate a cybersecurity incident.

- **VMs**(***Virtual machines***) - Virtual machines (VMs) are software versions of physical computers. VMs provide an additional layer of security for an organization because they can be used to run code in an isolated environment, preventing malicious code from affecting the rest of the computer or system. VMs can also be deleted and replaced by a pristine image after testing malware. VMs also give you the ability to revert to a previous state. However, there’s still a small risk that a malicious program can escape virtualization and access the host machine. 

- **Sandbox environments** - A sandbox is a type of testing environment that allows you to execute software or programs separate from your network. They are commonly used for testing patches, identifying and addressing bugs, or detecting cybersecurity vulnerabilities. Sandboxes can also be used to evaluate suspicious software, evaluate files containing malicious code, and simulate attack scenarios. Sandboxes can be stand-alone physical computers that are not connected to a network; however, it is often more time and cost-effective to use software or cloud-based virtual machines as sandbox environments. Note that some malware authors know how to write code to detect if the malware is executed in a VM or sandbox environment. Attackers can program their malware to behave as harmless software when run inside these types of  testing environments. 

## Prevention measures

Some common measures organizations use to prevent brute force attacks and similar attacks from occurring include: 

- **Salting and hashing**: Hashing converts information into a unique value that can then be used to determine its integrity. It is a one-way function, meaning it is impossible to decrypt and obtain the original text. Salting adds random characters to hashed passwords. This increases the length and complexity of hash values, making them more secure.
- **MFA**(***Multi-factor authentication***) and **2FA**(***Two-Factor Authentication***): MFA is a security measure which requires a user to verify their identity in two or more ways to access a system or network. This verification happens using a combination of authentication factors: a username and password, fingerprints, facial recognition, or a one-time password (OTP) sent to a phone number or email. 2FA is similar to MFA, except it uses only two forms of verification.
- **CAPTCHA**(***Completely Automated Public Turing test to tell Computers and Humans Apart***) and reCAPTCHA: It asks users to complete a simple test that proves they are human. This helps prevent software from trying to brute force a password. reCAPTCHA is a free CAPTCHA service from Google that helps protect websites from bots and malicious software.
- **Password policies**: Organizations use password policies to standardize good password practices throughout the business. Policies can include guidelines on how complex a password should be, how often users need to update passwords, and if there are limits to how many times a user can attempt to log in before their account is suspended.

---

## 4.03 - Network Hardening 

Tasks performed:
- Firewall rules maintenance
- Network log analysis - examining network logs to identity events of interest
- Patch updates 
- Server backups
- Network access privilege
- Encryption
- Port filtering

### Firewall

- Firewalls allow or block traffic based on a set of rules. 
- As data packets enter a network, the packet header is inspected and allowed or denied based on its port number. 
- Each system should have its own firewall, regardless of the network firewall.

### Intrusion Detection System 

- An **IDS**(***Intrusion Detection System***) is an application that monitors system activity and alerts on possible intrusions. An IDS alerts administrators based on the signature of malicious traffic.
- The IDS is configured to detect known attacks. IDS systems often sniff data packets as they move across the network and analyze them for the characteristics of known attacks. Some IDS systems review not only for signatures of known attacks, but also for anomalies that could be the sign of malicious activity. When the IDS discovers an anomaly, it sends an alert to the network administrator who can then investigate further.
- Limitations: IDS systems can only scan for known attacks or obvious anomalies. IDS doesn’t actually stop the incoming traffic if it detects something awry. It’s up to the network administrator to catch the malicious activity before it does anything damaging to the network. 
- When combined with a firewall, an IDS adds another layer of defense. The IDS is placed behind the firewall and before entering the LAN, which allows the IDS to analyze data streams after network traffic that is disallowed by the firewall has been filtered out. This is done to reduce noise in IDS alerts, also referred to as false positives.

### Intrusion Prevention System 

- An **IPS**(***Intrusion Prevention System***) is an application that monitors system activity for intrusive activity and takes action to stop the activity. It offers even more protection than an IDS because it actively stops anomalies when they are detected, unlike the IDS that simply reports the anomaly to a network administrator.
- An IPS searches for signatures of known attacks and data anomalies. An IPS reports the anomaly to security analysts and blocks a specific sender or drops network packets that seem suspect. 
- The IPS (like an IDS) sits behind the firewall in the network architecture. This offers a high level of security because risky data streams are disrupted before they even reach sensitive parts of the network. 
- One potential limitation is that it is inline: If it breaks, the connection between the private network and the internet breaks. Another limitation of IPS is the possibility of false positives, which can result in legitimate traffic getting dropped.


![[Firewall-IDS-IPS.png]]


![[network-hardening-tools.png]]

### Full packet capture devices

Full packet capture devices can be incredibly useful for network administrators and security professionals. These devices allow you to record and analyze all of the data that is transmitted over your network. They also aid in investigating alerts created by an IDS. 

### Security Information and Event Management 

- A SIEM tool is an application that collects and analyzes log data to monitor critical activities in an organization. 
- SIEM tools work in real time to report suspicious activity in a centralized dashboard. SIEM tools additionally analyze network log data sourced from IDSs, IPSs, firewalls, VPNs, proxies, and DNS logs. SIEM tools are a way to aggregate security event data so that it all appears in one place for security analysts to analyze. This is referred to as a single pane of glass. 

---

## 4.04 - Cloud Hardening

### Cloud security considerations

#### Identity Access Management

**IAM**(***Identity Access Management***) is a collection of processes and technologies that helps organizations manage digital identities in their environment. This service also authorizes how users can use different cloud resources. A common problem that organizations face when using the cloud is the loose configuration of cloud user roles. An improperly configured user role increases risk by allowing unauthorized users to have access to critical cloud operations. 

#### Configuration

The number of available cloud services adds complexity to the network. Each service must be carefully configured to meet security and compliance requirements. This presents a particular challenge when organizations perform an initial migration into the cloud. When this change occurs on their network, they must ensure that every process moved into the cloud has been configured correctly. If network administrators and architects are not meticulous in correctly configuring the organization’s cloud services, they could leave the network open to compromise. Misconfigured cloud services are a common source of cloud security issues. 

#### Attack surface 

Cloud service providers (CSPs) offer numerous applications and services for organizations at a low cost. Every service or application on a network carries its own set of risks and vulnerabilities and increases an organization’s overall attack surface. An increased attack surface must be compensated for with increased security measures.
Cloud networks that utilize many services introduce lots of entry points into an organization’s network. However, if the network is designed correctly, utilizing several services does not introduce more entry points into an organization’s network design. These entry points can be used to introduce malware onto the network and pose other security vulnerabilities. It is important to note that CSPs often defer to more secure options, and have undergone more scrutiny than a traditional on-premises network. 

#### Zero-day attacks

Zero-day attacks are an important security consideration for organizations using cloud or traditional on-premise network solutions. A zero day attack is an exploit that was previously unknown. CSPs are more likely to know about a zero day attack occurring before a traditional IT organization does. CSPs have ways of patching hypervisors and migrating workloads to other virtual machines. These methods ensure the customers are not impacted by the attack. There are also several tools available for patching at the operating system level that organizations can use.

#### Visibility and tracking 

Network administrators have access to every data packet crossing the network with both on-premise and cloud networks. They can sniff and inspect data packets to learn about network performance or to check for possible threats and attacks.

This kind of visibility is also offered in the cloud through flow logs and tools, such as packet mirroring. CSPs take responsibility for security in the cloud, but they do not allow the organizations that use their infrastructure to monitor traffic on the CSP’s servers. Many CSPs offer strong security measures to protect their infrastructure. Still, this situation might be a concern for organizations that are accustomed to having full access to their network and operations. CSPs pay for third-party audits to verify how secure a cloud network is and identify potential vulnerabilities. The audits can help organizations identify whether any vulnerabilities originate from on-premise infrastructure and if there are any compliance lapses from their CSP. 

Things change fast in the cloud
CSPs are large organizations that work hard to stay up-to-date with technology advancements. For organizations that are used to being in control of any adjustments made to their network, this can be a potential challenge to keep up with. Cloud service updates can affect security considerations for the organizations using them. For example, connection configurations might need to be changed based on the CSP’s updates. 

Organizations that use CSPs usually have to update their IT processes. It is possible for organizations to continue following established best practices for changes, configurations, and other security considerations. However, an organization might have to adopt a different approach in a way that aligns with changes made by the CSP.

#### Shared responsibility model

A commonly accepted cloud security principle is the shared responsibility model. The shared responsibility model states that the CSP must take responsibility for security involving the cloud infrastructure, including physical data centers, hypervisors, and host operating systems. The company using the cloud service is responsible for the assets and processes that they store or operate in the cloud.

The shared responsibility model ensures that both the CSP and the users agree about where their responsibility for security begins and ends. A problem occurs when organizations assume that the CSP is taking care of security that they have not taken responsibility for. One example of this is cloud applications and configurations. The CSP takes responsibility for securing the cloud, but it is the organization’s responsibility to ensure that services are configured properly according to the security requirements of their organization. 

---

