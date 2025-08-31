
#networks 

## Contents :-

#### [[#1.01 - IP Address]]
#### [[#1.02 - MAC Address]]
#### [[#1.03 - TCP]]
#### [[#1.04 - UDP]]
#### [[#1.05 - Common Ports & Protocols]]
#### [[#1.06 - OSI Model]]
#### [[#1.07 - Subnetting]]

---

#ip #layer3

## 1.01 - IP Address

- **IP** (***Internet Protocol***)
* Layer 3 Protocol
* used to identify and locate devices on a network

### IP Versions

#ipv4 #ipv6

1. **IPv4**
	- dotted-decimal notation 
	- *32 bits* (8 bits X 4)
2. **IPv6**
	- hexadecimal notation 
	- *128 bits* (16 bits * 8)
	- eight groups of four hexadecimal digits, separated by colons
	- leading zeros within a group can be omitted, and consecutive groups of zeros can be represented by a double colon (::) to simplify the address

==IPv4 and IPv6 are not directly compatible.==

`inet -> IPv4, inet6 -> IPv6, ether -> MAC address`![[ifconfig-command.png]]

- **NAT** (***Network Address Translation***) - prevents us from running out of IPv4 addresses

### Commands to find IP address 

- `ipconfig`: Windows
- `ifconfig`: Linux/MAC OS
 
![[publicIP-privateIP.png]]

![[privateIP-classes.png]]

---

#mac-address #layer2

## 1.02 - MAC Address

* Layer 2 protocol
* used to ==communicate over switches within a **LAN**== (***Local Area Network***)
* unique address given to **NICs** (***Network Interface Card***)
* hardware address that is permanently assigned by the manufacturer and is stored in the device's firmware or **ROM** (***Read-Only Memory***)
* *48 bits* in length - 6 pairs of hexadecimal digits separated by colons
* first 3 hexadecimal pairs -> vendor identifier (can be found using [MAC Address Lookup](https://maclookup.app/))

---

#tcp #layer4

## 1.03 - TCP

- **TCP** (***Transmission Control Protocol***)
* layer 4 protocol
* ==connection-oriented== protocol
* reliable, ordered and error-checked delivery of data packets over an IP network
* *Examples: FTP, SSH, Telnet, SMTP, POP3, IMAP, HTTP/HTTPS*

### Three-way Handshake

#3-way-handshake

==SYN -> SYN-ACK -> ACK==

![[tcp-handshake.png]]

1. **SYN (*Synchronize*)** : The initiating device (client) sends a TCP packet with the SYN flag set to the destination device (server). This packet indicates the desire to establish a connection and includes an initial sequence number.
2. **SYN-ACK (*Synchronize-Acknowledge*)** : Upon receiving the SYN packet, the destination device responds with a TCP packet that has both the SYN and ACK (acknowledge) flags set. This packet acknowledges the receipt of the initial SYN packet and also includes its own initial sequence number.
3. **ACK (*Acknowledge*)** : Finally, the initiating device acknowledges the SYN-ACK packet by sending an ACK packet back to the destination. This packet confirms the establishment of the connection and typically contains an incremented sequence number.

---

#udp #layer4

## 1.04 - UDP

- **UDP** (***User Datagram Protocol***)
* layer 4 protocol
* ==connectionless== protocol
* unreliable
* does not establish a connection or guarantee delivery of packets
* *Examples: DNS, DHCP, TFTP, SNMP, VoIP*

---

#port #protocol

## 1.05 - Common Ports & Protocols

- **FTP** (***File Transfer Protocol***): Port 21 (TCP)
- **SSH** (***Secure Shell***): Port 22 (TCP)
- **Telnet**: Port 23 (TCP)
- **SMTP** (***Simple Mail Transfer Protocol***): Port 25 (TCP)
- **DNS** (***Domain Name System***): Port 53 (TCP and UDP)
- **HTTP** (***Hypertext Transfer Protocol***): Port 80 (TCP)
- **HTTPS** (***Hypertext Transfer Protocol Secure***): Port 443 (TCP)
- **DHCP** (***Dynamic Host Configuration Protocol***): Port 67 (UDP) and Port 68 (UDP)
- **POP3** (***Post Office Protocol version 3***): Port 110 (TCP)
- **IMAP** (***Internet Message Access Protocol***): Port 143 (TCP)
- **SNMP** (***Simple Network Management Protocol***): Port 161 (UDP)
- **RDP** (***Remote Desktop Protocol***): Port 3389 (TCP)
- **NTP** (***Network Time Protocol***): Port 123 (UDP)
- **SMB** (***Server Message Block***): Port 445 (TCP)
- **FTPS** (***FTP over SSL/TLS***): Port 990 (TCP)
- **TFTP** (***Trivial File Transfer Protocol***): Port 69 (UDP)
- **LDAP** (***Lightweight Directory Access Protocol***): Port 389 (TCP and UDP)
- **MySQL**: Port 3306 (TCP)
- **RDP** (***Remote Desktop Protocol***): Port 3389 (TCP)

---

#osi 

## 1.06 - OSI Model

1) **Physical** - *cables, cat6*
	- Responsible for the transmission and reception of raw unstructured data bits over a physical medium. 
	- Defines the electrical, mechanical, and functional characteristics of the physical interface between devices.
2) **Data** - *MAC address, switching*
	- Handles the reliable transmission of data frames between directly connected nodes over a physical link. 
	- Provides error detection and correction, flow control, and handles access to the physical medium.
	- *Examples of data link layer protocols: Ethernet, Wi-Fi, and PPP (Point-to-Point Protocol)*
3) **Network** - *IP address, routing*
	- Enables the routing of data packets across different networks. 
	- Deals with logical addressing and determines the best path for data delivery based on network conditions and routing protocols.
4) **Transport** - *TCP, UDP*
	- Ensures the reliable and orderly delivery of data between end systems. 
	- Breaks data into smaller segments, manages end-to-end communication, and provides error recovery, flow control, and congestion control.
5) **Session** - *session management*
	- Establishes, manages, and terminates communication sessions between applications. 
	- Provides synchronization and dialog control mechanisms to enable seamless communication between devices.
6) **Presentation** - *JPEG, PDF, MOV*
	- Responsible for data representation, encryption, compression, and formatting. 
	- Ensures that data sent by the application layer of one system is understandable by the application layer of another system. 
	- Deals with data syntax and semantics.
7) **Application** - *HTTP, SMTP*
	- Closest layer to the end-user and provides services directly to user applications. 
	- Includes protocols for various application-level services such as file transfer, email, web browsing, and remote access.

- ==Please Do Not Throw Sausage Pizza Away==
- ==All People Seem To Need Data Processing==

### Data Flow in OSI Model

* Receiving data and troubleshooting -> 1 to 7
* Transmitting data -> 7 to 1

---

#subnetting

## 1.07 - Subnetting

- Process of dividing a network into smaller subnetworks called subnets.
- Allows for more efficient use of IP addresses and facilitates network management and routing.
- Commonly used in IPv4 networks.

![[subnetting-cheatsheet.png]]

- Subnetting involves borrowing bits from the host portion of an IP address to create a subnet identifier. By doing this, a network can be divided into multiple subnets, each with its own range of IP addresses.

- ==CIDR (**Classless Inter-Domain Routing**)== notation is a method used to represent IP addresses and their corresponding subnet masks. It specifies the network prefix length, which indicates the number of bits used for the network portion of the IP address. CIDR notation is expressed by appending a forward slash (/) followed by the prefix length to the IP address.

---

#additional-info 
## Additional Information

- [IP Address Guide](https://www.ipaddressguide.com/)
- [Professor Messer - YouTube Video](https://www.youtube.com/watch?v=ZxAwQB8TZsM&ab_channel=ProfessorMesser)

---
