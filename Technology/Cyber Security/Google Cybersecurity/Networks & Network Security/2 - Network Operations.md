
## Contents :-

#### [[#2.01 - Network Protocols]]
#### [[#2.02 - System Identification]]
#### [[#2.03 - Additional Information]]

---

#network-protocols

## 2.01 - Network Protocols  

A set of rules used by two or more devices on a network to describe the order of delivery and structure of the data. Protocols are like a common language that allows devices across the world to communicate with and understand each other.

Some protocols are assigned Port Numbers by the **IANA**(***Internet Assigned Numbers Authority***).

### Communication Protocols

They govern the exchange of information on network transmission.

- **TCP**(***Transmission Control Protocol***) - an internet communication protocol that allows two devices to form a connection and stream data. It uses the Three-Way handshake.
- **UDP**(***User Datagram Protocol***) - a connectionless protocol that does not establish a connection between devices before transmission. It is less reliable, but faster than TCP.
- **ARP**(***Address Resolution Protocol***) - used to determine the MAC address of the next router/device on the path. Translates IP addresses into MAC address of the hardware device.
- **HTTP**(***Hyper-Text Transfer Protocol***) - provides a method of communication between clients and website servers. HTTP uses Port 80.
- **DNS**(***Domain Name System***) - translates internet domain names into IP addresses. It normally uses UDP on Port 53.
- **Telnet** - an application layer protocol that allows a device to communicate with another device or server. Telnet sends all information in clear text. It uses command line prompts to control another device. Telnet can be used to connect to local or remote devices and uses TCP port 23. 
- **SMTP**(***Simple Mail Transfer Protocol***) - used to transmit and route email from the sender to the recipient’s address. SMTP works with **MTA**(***Message Transfer Agent***) software, which searches DNS servers to resolve email addresses to IP addresses, to ensure emails reach their intended destination. SMTP uses TCP/UDP port 25 for unencrypted emails and TCP/UDP port 587 using TLS for encrypted emails. The TCP port 25 is often used by high-volume spam. SMTP helps to filter out spam by regulating how many emails a source can send at a time.
- **POP**(***Post Office Protocol***) - an application layer protocol used to manage and retrieve email from a mail server. Many organizations have a dedicated mail server on the network that handles incoming and outgoing mail for users on the network. User devices will send requests to the remote mail server and download email messages locally. If you have ever refreshed your email application and had new emails populate in your inbox, you are experiencing POP and IMAP in action. Unencrypted, plaintext authentication uses TCP/UDP port 110 and encrypted emails use Secure Sockets Layer/Transport Layer Security (SSL/TLS) over TCP/UDP port 995.  When using POP, mail has to finish downloading on a local device before it can be read and it does not allow a user to sync emails. 
- **IMAP**(***Internet Message Access Protocol***) - used for incoming email. It downloads the headers of emails, but not the content. The content remains on the email server, which allows users to access their email from multiple devices. IMAP uses TCP port 143 for unencrypted email and TCP port 993 over the TLS protocol. Using IMAP allows users to partially read email before it is finished downloading and to sync emails. However, IMAP is slower than POP3.

### Management Protocols

They are used for monitoring and managing activity on a network. They include protocols for error reporting and optimizing performance on the network. 

- **SNMP**(***Simple Network Management Protocol***) - used for monitoring and managing devices on a network. SNMP can reset a password on a network device or change its baseline configuration. It can also send requests to network devices for a report on how much of the network’s bandwidth is being used up. It occurs at the application layer.
- **ICMP**(***Internet Control Message Protocol***) - an internet protocol used by devices to tell each other about data transmission errors across the network. ICMP is used by a receiving device to send a report to the sending device about the data transmission. ICMP is commonly used as a quick way to troubleshoot network connectivity and latency by issuing the “ping” command on a Linux operating system. It occurs at the internet layer.
- **DHCP**(***Dynamic Host Control Protocol***) - an application layer protocol used on a network to configure devices. It assigns a unique IP address and provides the addresses of the appropriate DNS server and default gateway for each device. DHCP servers operate on UDP port 67 while DHCP clients operate on UDP port 68.

### Security Protocols

They ensure that data is sent and received securely across a network by using encryption algorithms

- **HTTPS**(***Hyper-Text Transfer Protocol Secure***) - a network protocol that provides a secure method of communication between clients and website servers. HTTPS is a secure version of HTTP that uses secure sockets layer/transport layer security (SSL/TLS) encryption on all transmissions so that malicious actors cannot read the information contained. HTTPS uses port 443. It occurs at the application layer.
- **SFTP**(***Secure File Transfer Protocol***) - used to transfer files from one device to another over a network. SFTP uses secure shell (SSH), typically through TCP port 22. SSH uses Advanced Encryption Standard (AES) and other types of encryption to ensure that unintended recipients cannot intercept the transmissions. In the TCP/IP model, SFTP occurs at the application layer. SFTP is used often with cloud storage. Every time a user uploads or downloads a file from cloud storage, the file is transferred using the SFTP protocol.
- **SSH**(***Secure Shell***) - used to create a secure connection with a remote system. This application layer protocol provides an alternative for secure authentication and encrypted communication. SSH operates over the TCP port 22 and is a replacement for less secure protocols, such as Telnet.

![[Protocols & Port numbers.png]]

### Network Address Translation

#nat

The devices on your local home or office network each have a private IP address that they use to communicate directly with each other. In order for the devices with private IP addresses to communicate with the public internet, they need to have a public IP address. Otherwise, responses will not be routed correctly. Instead of having a dedicated public IP address for each of the devices on the local network, the router can replace a private source IP address with its public IP address and perform the reverse operation for responses. This process is known as Network Address Translation (NAT) and it generally requires a router or firewall to be specifically configured to perform NAT. NAT is a part of layer 2 (internet layer) and layer 3 (transport layer) of the TCP/IP model.

### Wireless Communication Protocols

#### Wi-Fi

#wifi

- Wi-Fi refers to a set of standards that define communication for wireless LANs. 
- Wi-Fi is a marketing term commissioned by the Wireless Ethernet Compatibility Alliance (WECA). WECA has since renamed their organization Wi-Fi Alliance. 
- Wi-Fi standards and protocols are based on the **802.11** family of internet communication standards determined by the **IEEE**(***Institute of Electrical and Electronics Engineers***). 

1. **WEP**(***Wired Equivalent Privacy***)
	-  a wireless security protocol designed to provide users with the same level of privacy on wireless network connections as they have on wired network connections. 
	- developed in 1999 and is the oldest of the wireless security standards.
	- WEP is largely out of use today as it is now considered a high-risk security protocol.

2. **WPA**(***Wi-Fi Protected Access***) 
	- developed in 2003 to improve upon WEP, address the security issues that it presented, and replace it. 
	- WPA was always intended to be a transitional measure so backwards compatibility could be established with older hardware.
	- The flaws with WEP were in the protocol itself and how the encryption was used. WPA addressed this weakness by using a protocol called **TKIP**(***Temporal Key Integrity Protocol***). 
	- WPA encryption algorithm uses larger secret keys than WEPs, making it more difficult to guess the key by trial and error. WPA also includes a message integrity check that includes a message authentication tag with each transmission.
	- Vulnerabilities - Malicious actors can use a **KRACK**(***Key Reinstallation Attack***) to decrypt transmissions using WPA. Attackers can insert themselves in the WPA authentication handshake process and insert a new encryption key instead of the dynamic one assigned by WPA. If they set the new key to all zeros, it is as if the transmission is not encrypted at all.

3. **WPA2** 
	- released in 2004. 
	- Uses the **AES**(***Advanced Encryption Standard***). 
	- WPA2 also improves upon WPA’s use of TKIP. It uses the **CCMP**(***Counter Mode Cipher Block Chain Message Authentication Code Protocol***), which provides encapsulation and ensures message authentication and integrity. 
	-  WPA2, like its predecessor, is vulnerable to KRACK attacks. 
	- Personal - WPA2 personal mode is best suited for home networks for a variety of reasons. It is easy to implement, initial setup takes less time for personal than enterprise version. The global passphrase for WPA2 personal version needs to be applied to each individual computer and access point in a network. 
	- Enterprise - WPA2 enterprise mode works best for business applications. The initial setup is more complicated than WPA2 personal mode, but enterprise mode offers individualized and centralized control over the Wi-Fi access to a business network. This means that network administrators can grant or remove user access to a network at any time. Users never have access to encryption keys, this prevents potential attackers from recovering network keys on individual computers.

4. **WPA3**
	- WPA3 addresses the authentication handshake vulnerability to KRACK attacks, which is present in WPA2. 
	- WPA3 uses **SAE**(***Simultaneous Authentication of Equals***), a password-authenticated, cipher-key-sharing agreement. This prevents attackers from downloading data from wireless network connections to their systems to attempt to decode it.
	- WPA3 has increased encryption to make passwords more secure by using 128-bit encryption, with WPA3-Enterprise mode offering optional 192-bit encryption.

---

## 2.02 - System Identification

### Firewall

#firewall

A network security device that monitors traffic to and from your network

- **Port Filtering** - a firewall function that blocks or allows certain port numbers to limit unwanted communication.

#### Firewall Categories

1. **Stateful** - a class of firewall that keeps track of information passing through it and proactively filters out threats. It uses a state table to track connections, so it can match return traffic to an existing session, thus requiring a rule in one direction only.
2. **Stateless** - a class of firewall that operates based on predefined rules and does not keep track of information from data packets. They are less secure than Stateful firewalls.
3. **NGFW**(***Next Generation Firewalls***)
	- deep packet inspection
	- intrusion protection
	- threat intelligence

#### Firewall Types

1. Physical
2. Software
3. Cloud-based

### Virtual Private Network

#vpn

VPN is a network security service that changes the public IP address and hides the virtual location, and also encrypts and encapsulates the data packets, thus ensuring data privacy while using a public network like the internet.

- **Encapsulation** - a process performed by VPN service that protects your data by wrapping sensitive data in other data packets.

### Network Segmentation

A security technique that divides the network into segments, each having its own access permissions and security rules.

- **Security Zone** - a segment of a network that protects the internal network from the internet.

- **Uncontrolled Zone** - any network outside of the organization's control.

- **Controlled Zone** - a subnet that protects the internal network from the uncontrolled zone. It has the following areas:
	1. **DMZ**(***Demilitarized Zone***) - acts as a network perimeter to the internal network.
	2. Internal network
	3. Restricted Zone

![[002.02.01 - Security Zones.png]]

### Subnetting

#subnetting 

- Subnetting is the subdivision of a network into logical groups called subnets. It works like a network inside a network. 
- It divides up a network address range into smaller subnets within the network. These smaller subnets form based on the IP addresses and network mask of the devices on the network. 
- Subnetting creates a network of devices to function as their own network. This makes the network more efficient and can also be used to create security zones. 
- If devices on the same subnet communicate with each other, the switch changes the transmissions to stay on the same subnet, improving speed and efficiency of the communications.

#### Classless Inter-Domain Routing Notation for Subnetting

#cidr

- **CIDR**(***Classless Inter-Domain Routing***) is a method of assigning subnet masks to IP addresses to create a subnet. Classless addressing replaces classful addressing. 
- Classful addressing was used in the 1980s as a system of grouping IP addresses into classes (Class A to Class E). Each class included a limited number of IP addresses, which were depleted as the number of devices connecting to the internet outgrew the classful range in the 1990s. 
- CIDR allows cybersecurity professionals to segment classful networks into smaller chunks. 
- CIDR IP addresses are formatted like IPv4 addresses, but they include a slash (“/’”) followed by a number at the end of the address, This extra number is called the **IP network prefix**.  
- For example, a regular IPv4 address uses the 198.51.100.0 format, whereas a CIDR IP address would include the IP network prefix at the end of the address, 198.51.100.0/24. This CIDR address encompasses all IP addresses between 198.51.100.0 and 198.51.100.255. The system of CIDR addressing reduces the number of entries in routing tables and provides more available IP addresses within networks.

### Proxy Servers

#proxy

A server that fulfills the requests of a client by forwarding them on to other servers. They utilize NAT to serve as a barrier between clients and external threats.

- **Forward Proxy Server** - regulates and restricts a person's access to the internet.
- **Reverse Proxy Server** - regulates and restricts the internet's access to an internal server.

---

#additional-info 

## 2.03 - Additional Information

- [Calculate CIDR](https://www.ipaddressguide.com/cidr)

---
