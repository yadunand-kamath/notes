
#python 

## Contents :-

#### [[#01 - Installing Python on Linux]]
#### [[#02 - Exception Handling]]
#### [[#03 - Subprocess]]
#### [[#04 - Optparse]]
#### [[#05 - Object Oriented Programming]]

---

## 01 - Installing Python on Linux

`apt install python3-pip`

---

## 02 - Exception Handling

- try block - contains statements which are susceptible for exception
- except block - if exception occurs, program enters this block, else it is skipped


---

## 03 - Subprocess

- module to execute system commands 
- ***SYNTAX:*** 
```
import subprocess
subprocess.call("command", shell = True)
```

---

## 04 - Optparse

- module that allows argument parsing in the Python program
- makes it easy to handle command-line arguments 
- ***SYNTAX:***
```
import optparse
parser = optparse.OptionParser()
parser.add_option("-option", dest = " ", help = " ")
(options, arguments) = parser.parse_args()
```
- since *optparse* is deprecated, use *argparse*

---

## 05 - Object Oriented Programming

- **Class** - blueprint of program that logically groups functions and data.
- **Constructor Method** - initialization method called automatically when an object is created

---

#additional-info 

## Additional Information

- [Test Python Regular Expressions](https://pythex.org/)
- [SMTP Lib](https://docs.python.org/2/library/smtplib.html)
- [OS Library Docs](https://docs.python.org/2/library/os.html)
- [Pynput Doc](https://pypi.org/project/pynput/)
- [Threading Doc](https://docs.python.org/2/library/threading.html)
- [Socket Documentation](https://docs.python.org/2/library/socket.html)
- [Python Requests](https://requests.readthedocs.io/en/latest/)

---