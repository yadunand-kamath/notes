
## Networking

- **Network** - 2 or more computers linked together to share data, information & resources.
	1. **LAN** (***Local Area Network***) - spanning a single floor/building.
	2. **WAN** (***Wide Area Network***) - long-distance connections between geographically remote networks.

- **Ethernet** (*IEEE 802.3*) is a standard that defines wired connections of networked devices. It defines the way data is formatted over the wire to ensure disparate devices can communicate over the same cable.

### Networking Devices

1. **Hub** - wired device used to connect multiple devices in a network.
2. **Switch** - wired devices that know the addresses of the devices connected to them and route traffic to that port/device rather than retransmitting to all devices.
3. **Router** - used to control traffic flow on networks and are often used to connect similar networks and can connect multiple switches.
4. **Firewall** - a network device used to filter traffic based on a defined set of rules, also called **filters** or **access control list**. They are essential in managing and controlling network traffic and protecting the network. It is typically deployed between a private network and the internet, but it can also be deployed between segmented networks.
5. **Server** - a computer that provides information to other computers on a network.
6. **Endpoint** - ends of a network communication link. One end is often at a server where a resource resides, and the other end is often a client making a request to use a network resource.

---

## Other Terminologies

- **VPN** (***Virtual Private Networks***) is not necessarily an encrypted tunnel. It is simply a point-to-point connection between two hosts that allows them to communicate.

- **Intrusion detection** is a specific form of monitoring that monitors recorded information and real-time events to detect abnormal activity indicating a potential incident or intrusion. An **IDS** (***Intrusion Detection System***) automates the inspection of logs and real-time system events to detect intrusion attempts and system failure.
	1. **HIDS** (***Host-based IDS***) - monitors a single computer or host.
	2. **NIDS** (***Network-based IDS***) - monitors a network by observing network traffic patterns.

- **SIEM** (***Security Information and Event Management***) - gather log data from various sources across the enterprise to better understand potential security concerns and apportion resources accordingly.

- **IPS** (***Intrusion Prevention System***) is a special type of active IDS that automatically attempts to detect and block attacks before they reach target system.

- **Redundancy** - design systems with duplicate components so that if a failure were to occur, there would be a backup.

- **Cloud computing** refers to on-demand access to computing resources available from almost anywhere, and cloud computing resources are highly available and easily scalable.

- **DMZ** (***Demilitarized Zone***) - a network area that is designed to be accessed by outside visitors but is still isolated from the private network of the organization.

- **VLAN** (***Virtual LAN***) - created by switches to logically segment a network without altering its physical topology. **VLAN hopping** are attacks that allow a malicious user to see traffic from other VLANs.

- **SLA** (***Service-Level Agreement***) - an agreement between a *cloud service provider* and a *cloud service customer* based on a taxonomy of cloud computing–specific terms to set the quality of the cloud services delivered.

- **Logical Ports** - When a communication connection is established between two systems, it is done using ports. A logical port (also called a socket) is little more than an address number that both ends of the communication link agree to use when transferring data. Ports allow a single IP address to support multiple simultaneous communications, each using a different port number.
	- Well-known ports (*0–1023*)
	- Registered ports (*1024–49151*)
	- Dynamic or private ports (*49152–65535*)

- **ICMP** (***Internet Control Message Protocol***) is used to determine the health of a network or a specific link. ICMP is utilized by ping, traceroute, and other network management tools.

---
