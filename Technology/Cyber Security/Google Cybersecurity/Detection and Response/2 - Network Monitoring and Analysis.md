
#network-analysis 

## Contents:-

#### [[#2.01 - Network Traffic]]
#### [[#2.02 - Data Exfiltration Attack]]

#### [[#2.03 - Packets and Packet Capture]]

#### [[#2.04 - Additional Information]]

---

## 2.01 - Network Traffic

- **Network Traffic** - the amount of data that moves across a network. It also includes the type of data transferred, such as HTTP.
- **Network Data** - the data that's transmitted between devices on a network.
- **IOC**(***Indicators of Compromise***) - observable evidence that suggests signs of a potential security incident.
- **Data Exfiltration** - unauthorized transmission of data from a system.

### 2.01.01 Monitoring Networks

Once a baseline for normal network behavior is determined, any deviations from that baseline can be identified as abnormal network behavior.

Networks can be monitored using tools like:

- **IDS**(***Intrusion Detection System***) to monitor system activity and alert on possible intrusions.
- **Network Protocol Analyzers/Packet Sniffers** to capture and analyze data traffic within a network. 

#### Flow Analysis

- **Flow** refers to movement of network communications and includes information related to packets, protocols and ports. 
- Packets can travel to ports, which receive and transmit communications. Ports are often associated with network protocols.
- **C2**(***Command and Control***) - techniques used by malicious actors to maintain communications between compromised systems and their own machine.

#### Packet Payload Information

- Network packets include details like source and destination addresses, and payload information.
- The payload information of these packets can be monitored to uncover unusual activity.

#### Temporal Patterns

- Network packets contain information relating to time which can help establish time patterns. For example, if bulk of data is transferred during a particular time, large volumes of network traffic outside these normal hours can be considered unusual and must be investigated.

---

## 2.02 - Data Exfiltration Attack

**Attacker:**
1. Gain access to system
2. Maintain access and avoid detection using lateral movement and pivoting (exploring and expanding access)
3. Search for valuable assets
4. Collect, package and exfiltrate data

**Defender:**
1. Prevent attacker access
2. Monitor network activity
3. Protect assets
4. Detect and stop exfiltration

---

#packet-sniffer 
## 2.03 - Packets and Packet Capture

- **Data packet**  is a basic unit of information that travels between devices in a network. Detecting network intrusions begins at the packet level.
- **P-cap**(***Packet capture***) - a file containing data packets intercepted from an interface or network.

### 2.03.01 - Components of a Packet

1. **Header** 
	- headers provide information that's used to route packets to their destination.
	- packets can have several headers depending on the protocols used.

![[ipv4 header.png]]
2. **Payload**
	- follows the header
	- contains actual data being delivered
3. **Footer**
	- also called **Trailer**
	- located at the end of the packet
	- can provide information for error-checking to determine if data has been corrupted.

***NOTE:*** Most protocols don't use footers.

### 2.03.02 - How Packet Sniffers work

- Network protocol analyzers use both software and hardware capabilities to capture network traffic and display it for security analysts to examine and analyze.
- First, packets must be collected from the network via the Network Interface Card (NIC), which is hardware that connects computers to a network, like a router. NICs receive and transmit network traffic, but by default they only listen to network traffic that’s addressed to them. To capture all network traffic that is sent over the network, a NIC must be switched to a mode that has access to all visible network data packets. In wireless interfaces this is often referred to as monitoring mode, and in other systems it may be called promiscuous mode. This mode enables the NIC to have access to all visible network data packets, but it won’t help analysts access all packets across a network. A network protocol analyzer must be positioned in an appropriate network segment to access all traffic between different hosts.
- The network protocol analyzer collects the network traffic in raw binary format. Binary format consists of 0s and 1s and is not as easy for humans to interpret. The network protocol analyzer takes the binary and converts it so that it’s displayed in a human-readable format, so analysts can easily read and understand the information.  

### 2.03.03 - P-cap Libraries and Formats

P-cap files can come in many formats depending on the packet capture library that’s used. Each format has different uses and network tools may use or support specific packet capture file formats by default. You should be familiar with the following libraries and formats:

- **Libpcap** is a packet capture library designed to be used by Unix-like systems, like Linux and MacOS®. Tools like tcpdump use Libpcap as the default packet capture file format. 
- **WinPcap** is an open-source packet capture library designed for devices running Windows operating systems. It’s considered an older file format and isn’t predominantly used.
- **Npcap** is a library designed by the port scanning tool Nmap that is commonly used in Windows operating systems.
- **PCAPng** is a modern file format that can simultaneously capture packets and store data. Its ability to do both explains the “ng,” which stands for “next generation.”

### 2.03.04 - tcpdump

Tcpdump is a command-line network protocol analyzer. It is used to capture network traffic. This traffic can be saved to a packet capture (p-cap), which is a file containing data packets intercepted from an interface or network.

- `sudo tcpdump [-i interface] [option(s)] [expression(s)]`: 
	- begins running tcpdump using elevated permissions as sudo. 
	- The -i parameter specifies the network interface to capture network traffic. 
	- The option(s) are optional and provide you with the ability to alter the execution of the command. Options are case-sensitive. Options that are written using short options can be written with or without a space between the option and its value. For example, sudo tcpdump -i any -c 3 and sudo tcpdump -iany -c3 are equivalent commands.
	- The expression(s) are a way to further filter network traffic packets so that you can isolate network traffic. 
	
***Note***: Before you can begin capturing network traffic, you must identify which network interface you'll want to use to capture packets from. You can use the `-D` flag to list the network interfaces available on a system.


- `-w`: Using the -w flag, you can write or save the sniffed network packets to a packet capture file instead of just printing it out in the terminal.
- `-r`: Using the -r flag, you can read a packet capture file by specifying the file name as a parameter. 
- `-v`: By default, tcpdump will not print out all of a packet's information. This option, which stands for verbose, lets you control how much packet information you want tcpdump to print out. There are three levels of verbosity you can use depending on how much packet information you want tcpdump to print out. The levels are `-v`, `-vv`, and `-vvv`. 
- `-c`: The -c option stands for count. This option lets you control how many packets tcpdump will capture. 
- `-n`: By default, tcpdump will perform name resolution. This means that tcpdump automatically converts IP addresses to names. It will also resolve ports to commonly associated services that use these ports. This can be problematic because tcpdump isn’t always accurate in name resolution. Additionally, name resolution uses what’s known as a *reverse DNS lookup*. A reverse DNS lookup is a query that looks for the domain name associated with an IP address. If you perform a reverse DNS lookup on an attacker’s system, they might be alerted that you are investigating them through their DNS records. Using the `-n` flag disables this automatic mapping of numbers to names and is considered to be best practice when sniffing or analyzing traffic. Using -n will not resolve hostnames, whereas `-nn` will not resolve both hostnames or ports. 

---

#additional-info 
## 2.04 - Additional Information

- [Network Traffic](https://attack.mitre.org/datasources/DS0029/)
- [Exfiltration Techniques](https://attack.mitre.org/tactics/TA0010/)
- [tcpdump Tutorial with Examples - Daniel Miessler](https://danielmiessler.com/p/tcpdump/)
- [tcpdump & libpcap Documentation](https://www.tcpdump.org/)
- [Wireshark User Guide](https://www.wireshark.org/docs/wsug_html/)

---
