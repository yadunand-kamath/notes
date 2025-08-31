
#LAN 

## Contents :-

#### [[#01 - LAN Topologies]]
#### [[#02 - Subnetting]]
#### [[#03 - ARP]]
#### [[#04 -DHCP]]

---

## 01 - LAN Topologies

- **Topology** - design of the network

### 01.01 - Star Topology

- Devices are individually connected via a central networking device such as a switch or hub.
- Most commonly found today because of its reliability and scalability - despite the cost.
- Any information sent to a device in this topology is sent via the central device to which it connects.
- More scalable in nature.
- Unfortunately, the more the network scales, the more maintenance is required to keep the network functional.
- This increased dependence on maintenance can also make troubleshooting faults much harder.
- If the centralized hardware that connects devices fails, these devices will no longer be able to send or receive data.
- More expensive than any of the other topologies due to more cabling and equipment costs.

### 01.02 - Bus Topology

- Relies upon a single connection which is known as a backbone cable.
- Because all data destined for each device travels along the same cable, it is very quickly prone to becoming slow and bottlenecked if devices within the topology are simultaneously requesting data. 
- This bottleneck also results in very difficult troubleshooting because it quickly becomes difficult to identify which device is experiencing issues with data all travelling along the same route.
- One of the easier and more cost-efficient topologies to set up because of their expenses, such as cabling or dedicated networking equipment used to connect these devices.
- There is a single point of failure along the backbone cable. If this cable were to break, devices can no longer receive or transmit data along the bus.

### 01.03 - Ring Topology

- Also known as Token topology.
- Devices such as computers are connected directly to each other to form a loop, meaning that there is little cabling required and less dependence on dedicated hardware.
- It works by sending data across the loop until it reaches the destined device, using other devices along the loop to forward the data. Interestingly, a device will only send received data from another device in this topology if it does not have any to send itself. If the device happens to have data to send, it will send its own data first before sending data from another device.
- Because there is only one direction for data to travel across this topology, it is fairly easy to troubleshoot any faults that arise.
- Data may have to visit many multiple devices first before reaching the intended device.
- Less prone to bottlenecks
- A fault such as cut cable, or broken device will result in the entire networking breaking.

### 01.04 - Switch

- Switches are dedicated devices within a network that are designed to aggregate multiple other devices that are capable of using ethernet.
- These various devices plug into a switch's port.
- Switches are much more efficient than their lesser counterpart (hubs/repeaters). Switches keep track of what device is connected to which port. This way, when they receive a packet, instead of repeating that packet to every port like a hub would do, it just sends it to the intended target, thus reducing network traffic.
- Both Switches and Routers can be connected to one another. The ability to do this increases the redundancy (the reliability) of a network by adding multiple paths for data to take.

### 01.05 - Router

- It's a router's job to connect networks and pass data between them. It does this by using routing.
- Routing is the label given to the process of data travelling across networks. 
- Routing involves creating a path between networks so that this data can be successfully delivered.

---

## 02 - Subnetting

- Subnetting is the term given to splitting up a network into smaller, miniature networks within itself.
- Subnetting is achieved by splitting up the number of hosts that can fit within the network, represented by a number called a subnet mask.
- An IP address is made up of four sections called octets. The same goes for a subnet mask which is also represented as a number of four bytes (32 bits), ranging from 0 to 255 (0-255).
- Subnets use IP addresses in three different ways:
	1. Identify the network address
	2. Identify the host address
	3. Identify the default gateway

|   |   |   |   |
|---|---|---|---|
|**Type**|**Purpose**|**Explanation**|**Example**|
|Network Address|This address identifies the start of the actual network and is used to identify a network's existence.|For example, a device with the IP address of 192.168.1.100 will be on the network identified by 192.168.1.0|192.168.1.0|
|Host Address|An IP address here is used to identify a device on the subnet|For example, a device will have the network address of 192.168.1.1|192.168.1.100|
|Default Gateway|The default gateway address is a special address assigned to a device on the network that is capable of sending information to another network|Any data that needs to go to a device that isn't on the same network (i.e. isn't on 192.168.1.0) will be sent to this device. These devices can use any host address but usually use either the first or last host address in a network (.1 or .254)|192.168.1.254|

---

## 03 - ARP

- Devices can have two identifiers: A *MAC address* and an *IP address*; the **ARP** (***Address Resolution Protocol***) is the technology that is responsible for allowing devices to identify themselves on a network.
- When devices wish to communicate with another, they will send a broadcast to the entire network searching for the specific device. Devices can use the ARP protocol to find the MAC address (and therefore the physical identifier) of a device for communication.
- Each device within a network has a ledger to store information on, which is called a cache. In the context of the ARP protocol, this cache stores the identifiers of other devices on the network.
- In order to map these two identifiers together (IP address and MAC address), the ARP protocol sends two types of messages:
	1. **ARP Request** - a message is broadcasted to every other device found on a network by the device, asking whether or not the device's MAC address matches the requested IP address.
	2. **ARP Reply** - If the device does have the requested IP address, a reply is returned to the initial device to acknowledge this. The initial device will now remember this and store it within its cache (an **ARP entry**).

---

## 04 -DHCP

- IP addresses can be assigned either manually (by entering them physically into a device) or automatically and most commonly by using a **DHCP** (***Dynamic Host Configuration Protocol***) server.

1. **DHCP Discover** - When a device connects to a network, if it has not already been manually assigned an IP address, it sends out a request to see if any DHCP servers are on the network. 
2. **DHCP Offer** - The DHCP server then replies back with an IP address the device could use.
3. **DHCP Request** - The device then sends a reply confirming it wants the offered IP Address.
4. **DHCP ACK** - The DHCP server sends a reply acknowledging this has been completed, and the device can start using the IP Address.

---
