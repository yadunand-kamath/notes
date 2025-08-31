
## Contents :-

#### [[#3.01 - Network Interception Attacks]]
#### [[#3.02 - Denial of Service Attack]]
#### [[#3.03 - Network Protocol Analyzer]]
#### [[#3.04 - Network Attack Tactics]]

---

## 3.01 - Network Interception Attacks 

- Network interception attacks work by intercepting network traffic and stealing valuable information or interfering with the transmission in some way.
- Malicious actors can use hardware or software tools to capture and inspect data in transit. This is referred to as packet sniffing. 
- In addition to seeing information that they are not entitled to, malicious actors can also intercept network traffic and alter it. 

### Backdoor attacks

#backdoor

- An organization may have a lot of security measures in place, including cameras, biometric scans and access codes to keep employees from entering and exiting without being seen. However, an employee might work around the security measures by finding a backdoor to the building that is not as heavily monitored, allowing them to sneak out for the afternoon without being seen. 
- In cybersecurity, backdoors are weaknesses intentionally left by programmers or system and network administrators that bypass normal access control mechanisms. Backdoors are intended to help programmers conduct troubleshooting or administrative tasks. However, backdoors can also be installed by attackers after they’ve compromised an organization to ensure they have persistent access.
- Once the hacker has entered an insecure network through a backdoor, they can cause extensive damage: installing malware, performing a denial of service (DoS) attack, stealing private information or changing other security settings that leaves the system vulnerable to other attacks. 

---

#DoS #DDoS

## 3.02 - Denial of Service Attack

- **DoS**(***Denial of Service***) is an attack that targets a network or server and floods it with network traffic.
- **DDoS**(***Distributed Denial of Service***) is a type of DoS attack that uses multiple devices or servers in different locations to flood the target network with unwanted traffic.
- **Botnet** - a collection of computers infected by malware that are under the control of a single threat actor, known as **bot-herder**. 

### Network-level DoS Attacks

1. **SYN**(***Synchronize***) **Flood attack**
	 - a type of DoS attack that simulates a TCP connection and floods a server with SYN packets.
2. **ICMP Flood attack**
	- a type of DoS attack performed by an attacker repeatedly sending ICMP packets to a network server.
3. **Ping of Death attack**
	 - a type of DoS attack caused when a hacker pings a system by sending it an oversized ICMP packet that is bigger than 64KB. 

---

## 3.03 - Network Protocol Analyzer

#packet-sniffer

A network protocol analyzer, also called a **packet sniffer** or a **packet analyzer**, is a tool designed to capture and analyze data traffic within a network. They are commonly used as investigative tools to monitor networks and identify suspicious activity. 

There are a wide variety of network protocol analyzers available, but some of the most common analyzers  include:
- SolarWinds NetFlow Traffic Analyzer
- ManageEngine OpManager
- Azure Network Watcher
- Wireshark
- tcpdump

### tcpdump 

- tcpdump is a command-line network protocol analyzer. 
- It is popular, text based, lightweight (uses little memory and has a low CPU usage) and uses the open-source libpcap library. 
- tcpdump provides a brief packet analysis and converts key information about network traffic into formats easily read by humans. It prints information about each packet directly into your terminal. tcpdump also displays the source IP address, destination IP addresses, and the port numbers being used in the communications. 

![[tcpdump - Output Log.png]]

Some information you receive from a packet capture includes: 
- **Timestamp** - The output begins with the timestamp, formatted as hours, minutes, seconds, and fractions of a second.  
- **Source IP** - The packet’s origin is provided by its source IP address.
- **Source port** - This port number is where the packet originated.
- **Destination IP** - The destination IP address is where the packet is being transmitted to.
- **Destination port** - This port number is where the packet is being transmitted to.

Common uses:
tcpdump and other network protocol analyzers are commonly used to capture and view network communications and to collect statistics about the network, such as troubleshooting network performance issues. They can also be used to:
- Establish a baseline for network traffic patterns and network utilization metrics.
- Detect and identify malicious traffic
- Create customized alerts to send the right notifications when network issues or security threats arise.
- Locate unauthorized instant messaging (IM), traffic, or wireless access points.
- However, attackers can also use network protocol analyzers maliciously to gain information about a specific network. 

---

## 3.04 - Network Attack Tactics

**NIC**(***Network Interface Card***) - piece of hardware that connects the device to a network. The NIC reads the data transmission, and if it contains the device's MAC address, it accepts the packet and sends it to the device to process information based on the protocol. However, a NIC can be set to **promiscuous mode**, which means that it accepts all traffic on the network, even the packets that aren't addressed to the NIC's device.

### Interception attack

These attacks intercept data packets as they travel across the network.

#### Malicious Packet Sniffing

Packet  sniffing is the process of capturing and inspecting data packets across a network.
1. **Passive Packet Sniffing** - a type of attack where data packets are read in transit.
2. **Active Packet Sniffing** - a type of attack where data packets are manipulated in transit.

Countermeasures:
- use VPN Tunnels to encrypt data in transit
- use HTTPS
- avoid using unprotected/public Wi-Fi

#### IP Spoofing

A network attack performed when an attacker changes the source IP of a data packet to impersonate an authorized system and gain access to a network.
1. **On Path attack** - an attack where malicious actor places themselves in the middle of an authorized connection and intercepts or alters the data in transit. It is also called **Man-in-the-Middle attack.**
2. **Replay attack** - an attack performed when a malicious actor intercepts a data packet in transit and delays it or repeats it another time.
3. **Smurf attack** - an attack performed when an attacker sniffs an authorized user's IP address and floods it with packets. The attacker keeps sending IP packets containing fake IP addresses until the network server crashes, whereas in DoS attack all packets are authorized (not fake).

Countermeasures:
- firewalls

---

