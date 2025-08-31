
## Contents :-

#### [[#5.01 - Threat Actors]]
#### [[#5.02 - Advanced Persistent Threats]]
#### [[#5.03 - Attack Vectors]]

---

## 5.01 - Threat Actors

- **Threat actors** - A threat actor is any person or group who presents a security risk. This broad definition refers to people inside and outside an organization. It also includes individuals who intentionally pose a threat, and those that accidentally put assets at risk. 

Threat actors are normally divided into five categories based on their motivations:
- **Competitors** refers to rival companies who pose a threat because they might benefit from leaked information.
- **State actors** are government intelligence agencies.
- **Criminal syndicates** refer to organized groups of people who make money from criminal activity.
- **Insider threats** can be any individual who has or had authorized access to an organization’s resources. This includes employees who accidentally compromise assets or individuals who purposefully put them at risk for their own benefit.
- **Shadow IT** refers to individuals who use technologies that lack IT governance. A common example is when an employee uses their personal email to send work-related communications.

In the digital attack surface, these threat actors often gain unauthorized access by hacking into systems. By definition, a hacker is any person who uses computers to gain access to computer systems, networks, or data. Similar to the term threat actor, hacker is also an umbrella term. When used alone, the term fails to capture a threat actor’s intentions.
### Types of hackers

Because the formal definition of a hacker is broad, the term can be a bit ambiguous. In security, it applies to three types of individuals based on their intent:

1. **Unauthorized hackers** - An unauthorized hacker, or unethical hacker, is an individual who uses their programming skills to commit crimes. Unauthorized hackers are also known as malicious hackers.
2. **Authorized, or ethical, hackers** - Authorized, or ethical, hackers refer to individuals who use their programming skills to improve an organization's overall security. These include internal members of a security team who are concerned with testing and evaluating systems to secure the attack surface. They also include external security vendors and freelance hackers that some companies incentivize to find and report vulnerabilities, a practice called bug bounty programs.
3. **Semi-authorized hackers** - Semi-authorized hackers typically refer to individuals who might violate ethical standards, but are not considered malicious. For example, a hacktivist is a person who might use their skills to achieve a political goal. One might exploit security vulnerabilities of a public utility company to spread awareness of their existence. The intentions of these types of threat actors is often to expose security risks that should be addressed before a malicious hacker finds them.
### Access points

- Each threat actor has a unique motivation for targeting an organization's assets. Keeping them out takes more than knowing their intentions and capabilities. It’s also important to recognize the types of attack vectors they’ll use.

For the most part, threat actors gain access through one of these attack vector categories:

- **Direct access**, referring to instances when they have physical access to a system
- **Removable media**, which includes portable hardware, like USB flash drives
- **Social media platforms** that are used for communication and content sharing
- **Email**, including both personal and business accounts
- **Wireless networks** on premises
- **Cloud services** usually provided by third-party organizations
- **Supply chains** like third-party vendors that can present a backdoor into systems

Any of these attack vectors can provide access to a system. Recognizing a threat actor’s intentions can help you determine which access points they might target and what ultimate goals they could have.

---

## 5.02 - Advanced Persistent Threats

Many malicious hackers find their way into a system, cause trouble, and then leave. But on some occasions, threat actors stick around. These kinds of events are known as **APTs**(***Advanced Persistent Threats***).

APT refers to instances when a threat actor maintains unauthorized access to a system for an extended period of time. The term is mostly associated with nation states and state-sponsored actors. Typically, an APT is concerned with surveilling a target to gather information. They then use the intel to manipulate government, defense, financial, and telecom services.

Just because the term is associated with state actors does not mean that private businesses are safe from APTs. These kinds of threat actors are stealthy because hacking into another government agency or utility is costly and time consuming. APTs will often target private organizations first as a step towards gaining access to larger entities.

---
## 5.03 - Attack Vectors

- **Attack Vectors** - the pathways attackers use to penetrate security defenses 

Attacker Mindset:
1. Identify a target
2. Determine how the target can be accessed 
3. Evaluate the attack vectors that can be exploited
4. Find the tools and methods of attack 

### Brute Force Attacks 

- A matter of trial and error
- One way of opening a closed lock is trying as many combinations as possible. Threat actors sometimes use similar tactics to gain access to an application or a network. 

1. **Simple brute force attacks** are an approach in which attackers guess a user's login credentials. They might do this by entering any combination of username and password that they can think of until they find the one that works.
2. **Dictionary attacks** are a similar technique except in these instances attackers use a list of commonly used credentials to access a system. This list is similar to matching a definition to a word in a dictionary.
3. **Reverse brute force attacks** are similar to dictionary attacks, except they start with a single credential and try it in various systems until a match is found.
4. **Credential stuffing** is a tactic in which attackers use stolen login credentials from previous data breaches to access user accounts at another organization. A specialized type of credential stuffing is called **pass the hash**. These attacks reuse stolen, unsalted hashed credentials to trick an authentication system into creating a new authenticated user session on the network.

Note: Besides access credentials, encrypted information can sometimes be brute forced using a technique known as **exhaustive key search**.

#### Common Brute Forcing tools:

- Aircrack-ng
- Hashcat
- John the Ripper
- Ophcrack
- THC Hydra

#### Prevention Measures

Organizations defend against brute force attacks with a combination of technical and managerial controls. 
- **Hashing and salting** - Hashing converts information into a unique value that can then be used to determine its integrity. Salting is an additional safeguard that’s used to strengthen hash functions. It works by adding random characters to data, like passwords. This increases the length and complexity of hash values, making them harder to brute force and less susceptible to dictionary attacks.
- **MFA** (***Multi-factor authentication***) - a security measure that requires a user to verify their identity in two or more ways to access a system or network.
- **CAPTCHA** (***Completely Automated Public Turing test to tell Computers and Humans Apart***) - a challenge-response authentication system. CAPTCHA asks users to complete a simple test that proves they are human and not software that’s trying to brute force a password. There are two types of CAPTCHA tests. One scrambles and distorts a randomly generated sequence of letters and/or numbers and asks users to enter them into a text box. The other test asks users to match images to a randomly generated word.
- **Password policies** - Organizations use these managerial controls to standardize good password practices across their business. The [NIST Special Publication 800-63B](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63b.pdf) provides detailed guidance that organizations can reference when creating their own password policies.
 
---

#additional-info
## Additional Information

- [OUCH!](https://www.sans.org/newsletters/ouch/) - free monthly newsletter from the SANS Institute that reports on social engineering trends and other security topics.
- [Scamwatch](https://www.scamwatch.gov.au/) -  resource for news and tools for recognizing, avoiding, and reporting social engineering scams.

---
