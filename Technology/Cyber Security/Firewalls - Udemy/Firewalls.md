
#firewall 

## Contents :-

#### [[#NAT]]
#### [[#Firewall Zones]]
#### [[#Layer 3 & Layer 4 Firewalls]]
#### [[#Explicit and Implicit Rules]]
#### [[#Stateful and Stateless Firewalls]]
#### [[#Layer 7 NGFW]]
#### [[#Host-based Firewall]]
#### [[#IDS/IPS]]
#### [[#Segmentation using VLANs]]

---
## NAT 

- **NAT**(***Network Address Translation***) - hides internal network addresses from external networks

1. **SNAT**(***Source NAT***) 
	- changes the IP address of outgoing packets from internal devices (Private IP swapped with Public IP)
	- allows systems with private IP addresses to access external networks including the Internet
2. **DNAT**(***Destination NAT***) 
	- translates destination IP addresses to internal addresses for incoming packets 
	
---

## Firewall Zones

- Firewalls are used to control traffic between zones

1. **Inside** - private systems and data
2. **DMZ**(***De-Militarized Zone***) - semi-protected area for systems that must be accessed from outside networks 
3. **Outside** - unprotected networks 
	
---

## Layer 3 & Layer 4 Firewalls

- Layer 4 - Protocol & Port
- Layer 3 - Source and Destination IP address 
- Rules are processed from top to down 
- Last rule denies all 

### Explicit and Implicit Rules 

- Explicit Rules - explicitly states to allow/deny
- Implicit Deny All - blocks all traffic by default unless specifically permitted

---

## Stateful and Stateless Firewalls

- **Stateful firewall** - tracks connection state and allows response traffic even if not mentioned explicitly 
- **State Firewall** - requires rules in both directions 

---

## Layer 7 NGFW

- **NGFW**(***Next Gen Firewall***)
- filters traffic based on application level protocols and content using signatures
- performs deep packet inspection

---

## Host-based Firewall

- secures an individual device from network-based threats
- can be tailored to each individual device and OS
- exists within the attack surface
- can be vulnerable if host's security is compromised

---

## IDS/IPS

- **IDS**(***Intrusion Detection System***) - takes a copy of the traffic and monitors, and detects any suspicious activities
- **IPS**(***Intrusion Prevention System***) - actively blocks and prevents suspicious activities

- **Signature-based** - string of bytes matching known malware or known attack 
- **Behavior-based** - determine normal baseline traffic and watch for unusual traffic patterns

---

## Segmentation using VLANs

- **VLAN**(***Virtual Local Area Network***)
- use different network segments for different security zones
- can enforce rules on traffic between segments but not within segments 

### Microsegmentation

- limits lateral movement of threats within a subnet

---