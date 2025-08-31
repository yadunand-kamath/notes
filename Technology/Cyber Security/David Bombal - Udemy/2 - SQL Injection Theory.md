
#command-injection

## Contents :-

#### [[#1.1 - Command Injection]]
#### [[#1.2 - Finding Command Injection Vulnerabilities]]
#### [[#1.3 - Preventing Command Injection Vulnerabilities]]
#### [[#1.4 - Additional Information]]

---

## 2.1 - SQL Injection

- **SQLi**(***SQL Injection***) - a vulnerability that consists of an attacker interfering with the SQL queries that an application makes to a database.

### 2.1.1 - Types of Command Injection

1. **In-band (Classic) SQLi** 
	- Occurs when attacker uses same communication channel to both launch the attack and gather the result of the attack. 
	- Retrieved data is presented directly in the application web page. 
	- Easier to exploit than other SQLi categories
	1. **Error-based SQLi** - forces the database to generate an error, giving the attacker information upon which to refine their injection.
	2. **Union-based SQLi** - leverages the UNION SQL operator to combine the result of two queries into a single result set.
2. **Inferential (Blind) SQLi** 
	- No actual transfer of data via the web application.
	- Takes longer to exploit than in-band SQLi.
	1. **Boolean-based SQLi** - uses Boolean conditions to return a different result depending on whether the query returns a TRUE or FALSE result.
	2. **Time-based SQLi** - relies on the database pausing for a specified amount of time, then returning the results, indicating a successful SQL query execution.
3. **Out-of-Band SQLi**
	- Consists of triggering an out-of-band network connection to a system that you control..

### 2.1.2 - Impact {CRITICAL}

- unauthorized access to sensitive information
- can be used to view sensitive information, alter and delete content in application; thus violating CIA triad
- remote code execution on the OS

---

## 2.2 - Finding SQL Injection Vulnerabilities

- **Black Box Testing** - tester is given limited information and access to system
- **White Box Testing** - tester is given complete information and access to system

### 2.2.1 - Black-Box Testing 

1. Map the application.
	- identify all instances where the web app appears to be interacting with the underlying OS.
2. Fuzz the application.
	- submit SQL-specific characters such as `'` or `"`, and look for errors or other anomalies.
	- submit Boolean conditions such as `OR 1=1` and `OR 1=2`, and look for differences in the application's responses.
	- submit payloads designed to trigger time delays when executed within a SQL query, and look for differences in the time taken to respond.
	- submit OAST payloads designed to trigger an out-of-band network interaction when executed within an SQL query, and monitor for any resulting interactions.

### 2.2.2 - White-Box Testing

1. Enable web server logging.
2. Enable database logging.
3. Map the application
	- visible functionality in application
	- regex search on all instances in the code that talk to the database
4. Code review
	- follow code path for all input vectors

---

## 2.3 - Exploiting SQL Injection Vulnerabilities

### 2.3.1 Exploiting Error-based SQLi

- Submit SQL-specific characters such as ' or ", and look for errors or other anomalies
- Different characters can give different errors

### 2.3.2 - Exploiting Union-based SQLi

- 2 rules for combining result sets of 2 queries by using UNION:
	1. The number and the order of columns must be the same in all queries.
	2. The data types must be compatible.
- Figure out the number of columns the query is making
- Figure the data types of the columns (mainly interested in string data)
- Use UNION operator to output information from the database
- Determining the number of columns required in an SQL injection UNION attack using ORDER BY: `SELECT title, cost FROM product WHERE id = 1 ORDER BY 1`. Incrementally inject a series of ORDER BY clauses until an error is observed.
- Determining the number of columns required in an SQL injection UNION attack using NULL VALUES: `SELECT title, cost FROM product WHERE id = 1 UNION SELECT NULL--`. Incrementally inject a series of UNION SELECT payloads specifying a different number of null values until no error is observed.
- Finding columns with a useful data type in an SQL injection UNION attack:
	- Probe each column to test whether it can hold string data by submitting a series of UNION SELECT payloads that place a string value into each column in turn: `' UNION SELECT 'a',NULL-- `

### 2.3.3 - Exploiting Boolean-based SQLi

- Submit a Boolean condition that evaluates to FALSE and note the response
- Submit a Boolean condition that evaluates to TRUE and note the response
- Write a program that uses conditional statements to ask the database a series of TRUE/FALSE questions and monitor response

### 2.3.4 - Exploiting Time-based SQLi

- Submit a payload that pauses the application for a specified period of time
- Write a program that uses conditional statements to ask the database a series of TRUE/FALSE questions and monitor response time

### 2.3.5 - Exploiting Out-of-Band SQLi

- Submit OAST payloads designed to trigger an out-of-band network interaction when executed within an SQL query, and monitor for any resulting interactions
- Depending on SQL injection use different methods to exfil data

---

## Preventing SQLi Vulnerabilities

- Primary Defenses
	- Use of Prepared Statements (Parameterized queries)
	- Use of Stored Procedures (Partial)
	- Whitelist Input Validation (Partial)
	- Escaping all user supplied input (Partial)

- Additional Defenses
	- Enforcing least privilege
	- Performing Whitelist Input Validation as Secondary Defense



---

#additional-info 
## 1.4 - Additional Information

- [SQL Map](https://github.com/sqlmapproject/sqlmap)

---
