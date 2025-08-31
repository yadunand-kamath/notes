
#python 

## Contents :-

#### [[#003.01 - Basics]]
#### [[#003.02 - Strings]]
#### [[#003.03 - Math]]
#### [[#003.04 - Variables and Methods]]
#### [[#003.05 - Lists, Tuples, Dictionaries]]
#### [[#003.06 - Sockets]]
#### [[#003.07 - File I/O]]
#### [[#003.08 - Object Oriented Programming]]

---

#files 

## 003.01 - Basics

- `mousepad file.py&`: allows to use terminal and mousepad editor simultaneously.
- `#!/bin/python3`: shebang for python programs. Makes it helpful to locate python3 folder for execution.
- `python3 file.py`: executes python file in terminal.
- `from module import submodule as alias`: importing modules.
- `var = input("Enter input: ")`: receive user input using the `input()` function.

---

#strings

## 003.02 - Strings
	
`print('string')` :
   - `' '` - to print strings
   - `" "` - print strings
   - `""" """` - to print multi line string
   - `+` - string concatenation

- `len(my_string)`: function used to determine the length (number of characters) of a string.
- `my_string[start_index:end_index]`: String slicing to extract a substring from a string by specifying the start and end indices.
- `upper()`, `lower()`, `title()`: convert string into uppercase, lowercase, title case (capitalize first letters of all words in the string).
- `strip()`: removes whitespaces from the string.
- `split()`: splits the string into a list based on a delimiter. Default delimiter is space.
- `delimiter.join(split_list)`: joins the string elements in a list using the delimiter.
- `replace()`: replace characters in a string.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

#math

## 003.03 - Math

In Python, the `math` module is a built-in module that provides various mathematical functions and constants.

### Math Operators

- **Addition (`+`)** : Adds two numbers
- **Subtraction (`-`)** : Subtracts one number from another
- **Multiplication (`*`)** : Multiplies two numbers
- **Division (`/`)** : Divides one number by another
- **Integer Division (`//`)** : Performs division and returns the quotient as an integer (rounds down)
- **Modulo (`%`)** : Returns the remainder of division
- **Exponentiation (`**`)** : Raises a number to a power

### Math Functions

- `math.sqrt(x)` : Calculates the square root of `x`
- `math.pow(x, y)` : Raises `x` to the power of `y`
- `math.exp(x)` : Calculates the exponential value of `x` (e^x)
- `math.log(x)` : Calculates the natural logarithm of `x` (base e)
- `math.log10(x)` : Calculates the logarithm of `x` to base 10
- `math.sin(x)`, `math.cos(x)`, `math.tan(x)` : Calculate the sine, cosine, and tangent of `x`, respectively (where `x` is in radians)
- `math.degrees(x)` : Converts `x` from radians to degrees
- `math.radians(x)` : Converts `x` from degrees to radians

---

## 003.04 - Variables and Methods

- `var = value`: A variable is a named storage location used to store data or values in a program.
- A function/method is a reusable block of organized code.
- Function definition :
	`def function_name(var):
		`code...`
		`return value`	
- `name(value)`: function call

---

#list #tuple #dictionary

## 003.05 - Lists, Tuples, Dictionaries

### Lists

- A list is a versatile and ==mutable== data structure that can hold a collection of items. It allows you to store multiple values of different data types in a single variable.
- `list_name = [value1, value2, ...]`
- `list_name.append(value)`: add an element at the end of the list.
- `list_name.remove(value)`: removes an element

### Tuples

- A tuple is an ==ordered, immutable== (elements cannot be modified once they are created) collection of elements.
- `tuple_name = (value1, value2, ...)`

### Dictionaries

- A dictionary is an ==unordered== collection of ==key-value pairs==. It is a versatile and powerful data structure that allows you to store, retrieve, and manipulate data based on unique keys.
- `dict_name = {key1:value1, key2:value2, ...}`
- Iteration :
	`for key in dict_name:
	    `print(key, dict_name[key])`
- `dict_name.get(key)`: retrieve value for a key

---

#sockets

## 003.06 - Sockets

Sockets enable programs to establish connections, send data, and receive data over various network protocols.

### Socket methods

- `socket.connect(address)`: Establishes a connection to a remote address
- `socket.bind(address)`: Binds the socket to a specific address and port
- `socket.listen(backlog)`: Listens for incoming connections on a TCP socket
- `socket.accept()`: Accepts an incoming connection and returns a new socket object for communication
- `socket.send(data)`: Sends data over the socket
- `socket.recv(buffer_size)`: Receives data from the socket

### Examples

#### 1. Basic TCP server that listens for incoming connections:

```
#!/bin/python3 

import socket

# Create a TCP socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind the socket to a specific address and port
server_address = ('localhost', 1234)
server_socket.bind(server_address)

# Listen for incoming connections
server_socket.listen(5)

while True:
    # Accept a client connection
    client_socket, client_address = server_socket.accept()

    # Receive and send data
    data = client_socket.recv(1024)
    client_socket.send(b"Received: " + data)

    # Close the client socket
    client_socket.close()
    
```

#### 2. Port Scanner:

```
#!/bin/python3 

import sys 
import socket 
from datetime import datetime 

#Define our target 
if len(sys.argv) == 2: 
	target = socket.gethostbyname(sys.argv[1]) #Translate hostname to IPv4 
	
else: 
	print("Invalid amount of arguments.") 
	print("Syntax: python3 scanner.py") 
	
#Add a pretty banner 
print("-" * 50) 
print("Scanning target " + target) 
print("Time started: " + str(datetime.now())) 
print("-" * 50) 

try: 
	for port in range(50,85): 
		s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
		socket.setdefaulttimeout(1) 
		result = s.connect_ex((target,port)) 
		#returns an error indicator - if port is open it throws a 0, otherwise 1 
		if result == 0: 
			print("Port {} is open".format(port)) 
		s.close() 
		
except KeyboardInterrupt: 
	print("\nExiting program.") 
	sys.exit() 
	
except socket.gaierror: 
	print("Hostname could not be resolved.") 
	sys.exit() 
	
except socket.error: 
	print("Could not connect to server.") 
	sys.exit()

```

---

#fileio 

## 003.07 - File I/O

### Reading Files

- `open()`: function to open file

Once the file is open, following methods can retrieve the contents of the file:
- `read()`: Reads the entire content of the file as a string
- `readline()`: Reads a single line from the file
- `readlines()`: Reads all lines from the file and returns them as a list

### Writing Files

- `write()`: to write to a file, open it in write mode using the `open()` function

Once the file is open, following method can write content to the file:
 - `write(content)`: Writes the specified content to the file

### Examples

#### 1. Reading from a file:

```
# Open the file in read mode
file = open("example.txt", "r")

# Read the entire content
content = file.read()
print(content)

# Read a single line
line = file.readline()
print(line)

# Read all lines
lines = file.readlines()
print(lines)

# Close the file
file.close()
```

#### 2. Writing to a file:

```
# Open the file in write mode
file = open("example.txt", "w")

# Write content to the file
file.write("Hello, World!\n")
file.write("This is a new line.")

# Close the file
file.close()
```

#### 3.Appending files:

```
# Open the file in append mode
file = open("example.txt", "a")

# Append content to the file without overwriting its existing contents
file.write("\nThis is appended content.")

# Close the file
file.close()
```

### Recommendation

- use the `with` statement when working with files to ensure that the file is properly closed even if an exception occurs.

```
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

---

#oop

## 003.08 - Object Oriented Programming

### Class 

- blueprint or a template for creating objects
- defines the properties (attributes) and behaviors (methods) that objects of that class will possess

### Object

- instance of a class
- created based on the blueprint provided by the class
- each object has its own set of attributes and can invoke the methods defined in the class
- objects are created by calling the class as if it were a function

### Examples

#### 1. Employee Class:

```
# Employee.py

class Employees: 

	def __init__(self, name, department, role, salary, years_employed): 
		self.name = name 
		self.department = department 
		self.role = role 
		self.salary = salary 
		self.years_employed = years_employed 
		
	def eligible_for_retirement(self): 
		if self.years_employed >= 20: 
			return True 
		else: 
			return False
```

```
# UseEmployee.py

from Employees import Employees 

e1 = Employees("Bob", "Sales", "Director of Sales", 100000, 20) 
e2 = Employees("Linda", "Executive", "CIO", 150000, 10) 

print(e1.name) # Bob
print(e2.role) # CIO
print(e1.eligible_for_retirement()) # True
```

---
