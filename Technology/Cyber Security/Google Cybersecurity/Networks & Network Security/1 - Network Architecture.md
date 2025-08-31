 
## Contents :-

#### [[#1.01 - Networks]]
#### [[#1.02 - Network Communication]]

---

#networks 

## 1.01 - Networks

**Network** is a group of connected devices that communicate over wired or wireless connections.

### Types of networks

- **LAN**(***Local Area Network***) - a network that spans a small area (office, school, home)
- **WAN**(***Wide Area Network***) - a network that spans a large geographic area (city, state, country)

### Network Devices

#network-devices

- **Hub** - a network device that provides a common point of connection for all devices connected to it, and broadcasts information to every device on the network.
- **Switch** - a device that makes connections between specific devices on a network, by maintaining a MAC table, and sends and receives data between them. It is a part of the Data Link layer.
- **Router** - a network device that connects multiple networks together, and reads IP header information to forward the packet to the next router on the path to the destination. It is a part of the Network layer.
- **Modem** - a device that connects the router to the internet and brings internet access to the LAN. It usually interfaces with an **ISP**(*Internet Service Provider*), and converts the transmissions it receives into digital signals.
- **Virtualization tools** - software that performs network operations.
- **Firewall** - a network security device that monitors traffic to or from the network and also restricts specific incoming and outgoing network traffic based on some security rules.
- **Servers** - provide a service for other devices on the network.
- **Clients** - devices that connect to a server.
- **WAP**(***Wireless Access Point***) - sends and receives digital signals over radio waves creating a wireless network. Devices with wireless adapters connect to the WAP using Wi-Fi.

### Cloud Network

A collection of servers or computers that stores resources and data in remote data centers that can be accessed via the internet.

**Cloud Computing** refers to the practice of using remote servers, applications, and network services that are hosted on the internet instead of a physical location owned by a company.

**CSP**(***Cloud Service Provider***) is a company that offers cloud computing services. 
CSPs provide 3 main categories of services:
1. **SaaS**(***Software as a service***) refers to software suites operated by the CSP that a company can use remotely without hosting the software. 
2. **IaaS**(***Infrastructure as a service***) refers to the use of virtual computer components offered by the CSP. These include virtual containers and storage that are configured remotely through the CSP’s API or web console. 
3. **PaaS**(***Platform as a service***) refers to tools that application developers can use to design custom applications for their company. Custom applications are designed and accessed in the cloud and used for a company’s specific business needs.


![[Cloud Services.png]]


---

#network-communication 

## 1.02 - Network Communication

- **Data Packet** - a basic unit of information that travels from one device to another within a network
- **Bandwidth** - amount of data a device receives every second
- **Speed** - rate at which data packets are received or downloaded
- **Packet Sniffing** - practice of capturing and inspecting data packets across a network

### TCP/IP Model

#tcp 

TCP/IP model is a framework used to visualize how data is organized and transmitted across the network.

- **TCP** (***Transmission Control Protocol***) - an internet communication protocol that allows two devices to form a connection and stream data.
- **IP** (***Internet Protocol***) - set of standards used for routing and addressing data packets as they travel between devices on a network.
- **Port** - a software-based location that organizes the sending and receiving of data between devices on a network.

#### Layers of TCP/IP model

![[TCP-IP model.png]]

1. **Network Access layer**
	- also called **Data Link layer**
	- organizes sending and receiving data frames within a single network.
	- corresponds to the physical hardware involved in network transmission. Hubs, modems, cables, and wiring are all considered part of this layer.
	1. **ARP** (***Address Resolution Protocol***) - ARP assists IP with directing data packets on the same physical network by mapping IP addresses to MAC addresses on the same physical network.

2. **Internet layer**
	- also called **Network layer**
	- responsible for ensuring the delivery to the destination host, which potentially resides on a different network.
	- determines which protocol is responsible for delivering the data packets.
	1. **IP** (***Internet Protocol***) - IP sends the data packets to the correct destination and relies on Transmission Control Protocol/User Datagram Protocol (TCP/UDP) to deliver them to corresponding service. IP packets allow communication between two networks. They are routed from the sending network to the receiving network. It retransmits any data that is lost or corrupt.
	2. **ICMP** (***Internet Control Message Protocol***) - ICMP shares error information and status updates of data packets. This is useful for detecting and troubleshooting network errors. ICMP reports information about packets that were dropped or disappeared in transit, issues with network connectivity, and packets redirected to other routers.

3. **Transport layer**
	- responsible for reliably delivering data between two systems or networks.
	1. **TCP** (***Transmission Control Protocol***) - TCP ensures that data is reliably transmitted to the destination service. TCP contains the port number of the intended destination service, which resides in the TCP header of an TCP/IP packet.
	2. **UDP** (***User Datagram Protocol***) - UDP is used by applications that are not concerned with reliability of the transmission. Data sent over UDP is not tracked as extensively as data sent using TCP. Because UDP does not establish network connections, it is used mostly for performance sensitive applications that operate in real time, such as video streaming.

4. **Application layer**
	- similar to the application, presentation, and session layers of the OSI model.
	- responsible for making network requests or responding to requests. 
	- defines which internet services and applications any user can access.
	- **HTTP** (***Hypertext Transfer Protocol***),  **SMTP** (***Simple Mail Transfer Protocol***), **SSH** (***Secure Shell***), **FTP** (***File Transfer Protocol***), **DNS** (***Domain Name System***)
	- Application layer protocols rely on underlying layers to transfer the data across the network.

### OSI Model

#osi 

The OSI model is a standardized concept that describes the seven layers computers use to communicate and send data over the network

![[TCP-IP vs OSI.png]]

1. **Layer 7: Application layer**
	-  includes all of the networking protocols that software applications use to connect a user to the internet. This characteristic is the identifying feature of the application layer—user connection to the network via applications and requests.
	- An example of a type of communication that happens at the application layer is using a web browser. The internet browser uses HTTP or HTTPS to send and receive information from the website server. The email application uses simple mail transfer protocol (SMTP) to send and receive email information. Also, web browsers use the domain name system (DNS) protocol to translate website domain names into IP addresses which identify the web server that hosts the information for the website. 

2. **Layer 6: Presentation layer**
	- Functions at the presentation layer involve data translation and encryption for the network.
	- This layer adds to and replaces data with standardized formats that can be understood by applications (layer 7) on both sending and receiving systems. 
	- Some formatting functions that occur at layer 6 include encryption, compression, and confirmation that the character code set can be interpreted on the receiving system. 
	- One example of encryption that takes place at this layer is SSL, which encrypts data between web servers and browsers as part of websites with HTTPS.

3. **Layer 5: Session layer**
	- A session describes when a connection is established between two devices. 
	- An open session allows the devices to communicate with each other. Session layer protocols occur to keep the session open while data is being transferred and terminate the session once the transmission is complete. 
	- Also responsible for activities such as authentication, reconnection, and setting checkpoints during a data transfer. If a session is interrupted, checkpoints ensure that the transmission picks up at the last session checkpoint when the connection resumes. 
	- Sessions include a request and response between applications. Functions in the session layer respond to requests for service from processes in the presentation layer (layer 6) and send requests for services to the transport layer (layer 4).

4. **Layer 4: Transport layer**
	- Responsible for delivering data between devices. 
	- Also handles the speed of data transfer, flow of the transfer, and breaking data down into smaller segments to make them easier to transport. 
	- Segmentation is the process of dividing up a large data transmission into smaller pieces that can be processed by the receiving system. These segments need to be reassembled at their destination so they can be processed at the session layer (layer 5). The speed and rate of the transmission also has to match the connection speed of the destination system. 
	- TCP and UDP are transport layer protocols. 

5. **Layer 3: Network layer**
	- Oversees receiving the frames from the data link layer (layer 2) and delivers them to the intended destination. The intended destination can be found based on the address that resides in the frame of the data packets. 
	- Data packets allow communication between two networks. These packets include IP addresses that tell routers where to send them. They are routed from the sending network to the receiving network. 

6. **Layer 2: Data link layer**
	- Organizes sending and receiving data packets within a single network. 
	- The data link layer is home to switches on the local network and network interface cards on local devices.
	- Protocols like **NCP** (***Network Control Protocol***), **HDLC** (***High-level Data Link Control***), and **SDLC** (***Synchronous Data Link Control Protocol***) are used at the data link layer.

7. **Layer 1: Physical layer** 
	- Corresponds to the physical hardware involved in network transmission. Hubs, modems, and the cables and wiring that connect them are all considered part of the physical layer. 
	- To travel across an ethernet or coaxial cable, a data packet needs to be translated into a stream of 0s and 1s. The stream of 0s and 1s are sent across the physical wiring and cables, received, and then passed on to higher levels of the OSI model.

### IP Address

#ip 

**IP**(***Internet Protocol***) address is a unique string of characters that identifies the location of a device on the internet.

#### IP version 4 (IPv4)

#ipv4 

![[IPv4 Packet Format.png]]

- **Version** - The first 4-bit header tells receiving devices what protocol the packet is using. The packet used in the illustration above is an IPv4 packet.
- **HLEN**(***IP Header Length***) - HLEN is the packet’s header length. It indicates where the packet header ends and the data segment begins. 
- **ToS**(***Type of Service***) - Routers prioritize packets for delivery to maintain quality of service on the network. The ToS field provides the router with this information.
- **Total Length** - This field communicates the total length of the entire IP packet, including the header and data. The maximum size of an IPv4 packet is 65,535 bytes.
- **Identification** - For IPv4 packets that are larger than 65, 535 bytes, the packets are divided, or fragmented, into smaller IP packets. The identification field provides a unique identifier for all the fragments of the original IP packet so that they can be reassembled once they reach their destination. 
- **Flags** - This field provides the routing device with more information about whether the original packet has been fragmented and if there are more fragments in transit.
- **Fragmentation Offset** - The fragment offset field tells routing devices where in the original packet the fragment belongs.
- **TTL**(***Time to Live***) - TTL prevents data packets from being forwarded by routers indefinitely. It contains a counter that is set by the source. The counter is decremented by one as it passes through each router along its path. When the TTL counter reaches zero, the router currently holding the packet will discard the packet and return an ICMP Time Exceeded error message to the sender. 
- **Protocol** - The protocol field tells the receiving device which protocol will be used for the data portion of the packet.
- **Header Checksum** - The header checksum field contains a checksum that can be used to detect corruption of the IP header in transit. Corrupted packets are discarded.
- **Source IP Address** - The source IP address is the IPv4 address of the sending device.
- **Destination IP Address** - The destination IP address is the IPv4 address of the destination device.
- **Options** - The options field allows for security options to be applied to the packet if the HLEN value is greater than five. The field communicates these options to the routing devices.

#### IP version 6 (IPv6)

#ipv6 

![[IPv4 vs IPv6.png]]

#### Private IP address 

- unique within the private network
- not visible to global networks
- assigned by network admins
- no cost to use
- Address ranges:
	1. 10.0.0.0 - 10.255.255.255
	2. 172.16.0.0 - 172.31.255.255
	3. 192.168.0.0 - 192.168.255.255

#### Public IP address 

- unique address in global internet
- assigned by ISP and IANA 
- costs to lease a public IP address
- Address ranges:
	1. 1.0.0.0 - 9.255.255.255
	2. 11.0.0.0 - 126.255.255.255
	3. 128.0.0.0 - 172.15.255.255
	4. 172.32.0.0 - 192.167.255.255
	5. 192.169.0.0 - 233.255.255.255

### MAC Address

#mac-address 

**MAC**(***Media Access Control***) address is a permanent, unique alphanumeric identifier that is assigned to each physical device on a network. It is used by Switch to forward data packets to the intended device.

---
