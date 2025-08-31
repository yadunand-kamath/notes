
#networking

## Contents :-

#### [[#01 - The Internet]]
#### [[#02 - Identifying Devices on a Network]]
#### [[#03 - OSI Model]]
#### [[#04 - Network Tools]]

---

## 01 - The Internet

- **Network** is the interconnection of devices.
- The first iteration of the Internet was within the *ARPANET* project, funded by the United States Defense Department in the late 1960s.
- However, it wasn't until 1989 when the Internet as we know it was invented by Tim Berners-Lee by the creation of the **WWW** (***World Wide Web***). It wasn't until this point that the Internet started to be used as a repository for storing and sharing information, just like it is today.
- **The Internet** is a giant network that consists of many, many small networks within itself. These small networks are called **private networks**, where networks connecting these small networks are called **public networks** -- or the Internet!

---

## 02 - Identifying Devices on a Network

- Devices have two means of identification, with one being permeable. 

### 02.01 - IP Address

- **IP** (***Internet Protocol***) Address
- It can be used as a way of identifying a host on a network for a period of time, where that IP address can then be associated with another device without the IP address changing.
- IP addresses can change from device to device but cannot be active simultaneously more than once within the same network.
- An IP address is a set of numbers that are divided into *four octets*.
- A **public address** is used to identify the device on the Internet, whereas a **private address** is used to identify a device amongst other devices.
- Public IP addresses are given by **ISPs** (***Internet Service Provider***).

### 02.02 - MAC Address

- **MAC** (***Media Access Control***) Address 
- Devices on a network will all have a physical network interface, which is a microchip board found on the device's motherboard. This network interface is assigned a unique address at the factory it was built at, called a MAC address. 
- The MAC address is a twelve-character hexadecimal number (_a base sixteen numbering system used in computing to represent numbers_) split into two's and separated by a colon. These colons are considered separators. The first six characters represent the company that made the network interface, and the last six is a unique number.
- They can be faked or "spoofed" in a process known as spoofing. This spoofing occurs when a networked device pretends to identify as another using its MAC address. 

---

#osi 
## 03 - OSI Model

- The **OSI** (***Open Systems Interconnection***) Model is a standardized model which we use to demonstrate the theory behind computer networking. In practice, it's actually the more compact TCP/IP model that real-world networking is based off.

1. **Layer 7 -- Application**
	- Essentially provides networking options to programs running on a computer.
	- Works almost exclusively with applications, providing an interface for them to use in order to transmit data. 
	- When data is given to the application layer, it is passed down into the presentation layer.
2. **Layer 6 -- Presentation**
	- The presentation layer receives data from the application layer. 
	- This data tends to be in a format that the application understands, but it's not necessarily in a standardized format that could be understood by the application layer in the _receiving_ computer. 
	- The presentation layer translates the data into a standardized format, as well as handling any encryption, compression or other transformations to the data. 
	- With this complete, the data is passed down to the session layer.
3. **Layer 5 -- Session**
	- When the session layer receives the correctly formatted data from the presentation layer, it looks to see if it can set up a connection with the other computer across the network. If it can't then it sends back an error and the process goes no further. 
	- If a session can be established then it's the job of the session layer to maintain it, as well as co-operate with the session layer of the remote computer in order to synchronize communications. 
	- When the session layer has successfully logged a connection between the host and remote computer the data is passed down to the transport Layer.
4. **Layer 4 -- Transport**
	- The transport layer first chooses the protocol over which the data is to be transmitted. 
	- The two most common protocols in the transport layer are **TCP** (***Transmission Control Protocol***) and **UDP** (***User Datagram Protocol***).
	- With TCP the transmission is _connection-based_ which means that a connection between the computers is established and maintained for the duration of the request. This allows for a reliable transmission, as the connection can be used to ensure that the packets _all_ get to the right place. A TCP connection allows the two computers to remain in constant communication to ensure that the data is sent at an acceptable speed, and that any lost data is re-sent. 
	- With UDP, the opposite is true; packets of data are essentially thrown at the receiving computer -- if it can't keep up then that's _its_ problem (this is why a video transmission over something like Skype can be pixelated if the connection is bad). 
	- What this means is that TCP would usually be chosen for situations where accuracy is favored over speed (e.g. file transfer, or loading a webpage), and UDP would be used in situations where speed is more important (e.g. video streaming).
	- With a protocol selected, the transport layer then divides the transmission up into bite-sized pieces (over TCP these are called **_segments_**, over UDP they're called **_datagrams_**), which makes it easier to transmit the message successfully.
5. **Layer 3 -- Network**
	- The network layer is responsible for locating the destination of your request. 
	- It takes the IP address for the destination and figures out the best route to take. 
	- At this stage we're working with what is referred to as _**Logical**_ **addressing** (i.e. IP addresses) which are still software controlled. 
	- Logical addresses are used to provide order to networks, categorizing them and allowing us to properly sort them. 
	- Currently the most common form of logical addressing is the IPV4 format.
6. **Layer 2 -- Data Link**
	- The data link layer focuses on the **_physical_ addressing** of the transmission. 
	- It receives a packet from the network layer (that includes the IP address for the remote computer) and adds in the physical (MAC) address of the receiving endpoint. 
	- Inside every network enabled computer is a **NIC** (***Network Interface Card***) which comes with a unique **MAC** (***Media Access Control***) address to identify it.
	- MAC addresses are set by the manufacturer and literally burnt into the card; they can't be changed -- although they _can_ be spoofed. 
	- Additionally, it's also the job of the data link layer to present the data in a format suitable for transmission.
	- The data link layer also serves an important function when it receives data, as it checks the received information to make sure that it hasn't been corrupted during transmission.
7. **Layer 1 -- Physical**
	- The physical layer is right down to the hardware of the computer. This is where the electrical pulses that make up data transfer over a network are sent and received. 
	- It's the job of the physical layer to convert the binary data of the transmission into signals and transmit them across the network, as well as receiving incoming signals and converting them back into binary data.

### Encapsulation

- As the data is passed down each layer of the model, more information containing details specific to the layer in question is added on to the start of the transmission. This whole process is referred to as **encapsulation**; the process by which data can be sent from one computer to another.

![[OSI - Encapsulation.jpeg]]

- When the message is received by the second computer, it reverses the process -- starting at the physical layer and working up until it reaches the application layer, stripping off the added information as it goes. This is referred to as **de-encapsulation**.

### TCP/IP Model

- The TCP/IP model consists of four layers: Application, Transport, Internet and Network Interface. Between them, these cover the same range of functions as the seven layers of the OSI Model.

![[OSI vs TCP-IP.png]]

- **Protocols** are sets of rules that define how an action is to be carried out. TCP/IP takes its name from the two most important of these: the Transmission Control Protocol that controls the flow of data between two endpoints, and the Internet Protocol, which controls how packets are addressed and sent.
- TCP is a _connection-based_ protocol. In other words, before you send any data via TCP, you must first form a stable connection between the two computers. The process of forming this connection is called the **three-way handshake**.

![[TCP 3-way handshake.png]]

- When you attempt to make a connection, your computer first sends a special request to the remote server indicating that it wants to initialize a connection. This request contains something called a **_SYN_** (short for _synchronize_) bit, which essentially makes first contact in starting the connection process. The server will then respond with a packet containing the SYN bit, as well as another "acknowledgement" bit, called **_ACK_**. Finally, your computer will send a packet that contains the ACK bit by itself, confirming that the connection has been setup successfully. With the three-way handshake successfully completed, data can be reliably transmitted between the two computers. Any data that is lost or corrupted on transmission is re-sent, thus leading to a connection which appears to be lossless.

---

## 04 - Network Tools

### Ping

- fundamental network tool
- Ping uses **ICMP** (***Internet Control Message Protocol***) packets to determine the performance of a connection between devices, i.e., if the connection exists or is reliable.
- The time taken for ICMP packets travelling between devices is measured by ping. This measuring is done using **ICMP's Echo packet** and then **ICMP's Echo reply** from the target device.
- Syntax:  `ping IP address/website URL`

### Traceroute

- Traceroute can be used to map the path your request takes as it heads to the target machine.
- Syntax: `traceroute <destination>`

### WHOIS

- A domain translates into an IP address. Domains are leased out by companies called Domain Registrars.
- Whois essentially allows you to query who a domain name is registered to.
- Installation: `sudo apt update && sudo apt-get install whois`
- Syntax: `whois <domain>`
- A WHOIS server listens on TCP port 43 for incoming requests.

### Dig

- DNS allows us to ask a special server to give us the IP address of the website we're trying to access.
- The computer searches for IP->Domain mapping in the local ==Hosts File== and then in the local ==DNS Cache==. 
- If not found in both, then it sends a request to a recursive DNS server, whose details are stored in the router. This server will also maintain a cache of results for popular domains; however, if the website you've requested isn't stored in the cache, the recursive server will pass the request on to a ==root name server==.
- The root name servers essentially keep track of the DNS servers in the next level down, choosing an appropriate one to redirect your request to. These lower level servers are called **TLD** (***Top-Level Domain***) servers, which are split up into extensions, such as `.com` or `.in`.
- TLD servers keep track of the next level down: **Authoritative name servers**. When a TLD server receives your request for information, the server passes it down to an appropriate Authoritative name server.
- Dig allows us to manually query recursive DNS servers of our choice for information about domains.
- Syntax: `dig <domain> @<dns-server-ip>`

### DNSDumpster

- domain research tool that can discover hosts related to a domain.
- DNSDumpster will also represent the collected information graphically.

### Summary

![[networktools_commands.png]]

---

Several protocols have been created to prevent the Email Spoofing technique. With the help of **SPF** (***Sender Policy Framework***), **DKIM** (***DomainKeys Identified Email***) and DMARC protocols, it can be understood whether the sender's address is fake or real.