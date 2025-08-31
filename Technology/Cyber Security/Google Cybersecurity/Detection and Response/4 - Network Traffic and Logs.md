
## Contents :-

#### [[#4.01 - Importance of Logs]]
#### [[#4.02 - IDS]]
#### [[#4.03 - SIEM Tools]]

---

#logs 

## 4.01 - Importance of Logs

- **Logs** - a record of events that occur within a system
- **Log Analysis** - the process of examining logs to identify events of interest
- **Log Management** - process of collecting, storing, analyzing, and disposing of log data

### 4.01.01 - Log Types

- Network
- System
- Application
- Security
- Authentication

### 4.01.02 - Log Details

- Date
- Time
- Location
- Action
- Author of action

### 4.01.03 - Log Formats

#### syslog

- a standard for logging and transmitting data

1. **Protocol** - used to transport logs to a centralized log server for log management. It uses *Port 514* for plaintext logs and *Port 6514* for encrypted logs.
2. **Service** - acts as a log forwarding service that consolidates logs from multiple sources into a single location.
3. **Log format** - consists of: *a header, structured-data, and a message*

```
`<236>1 2022-03-21T01:11:11.003Z virtual.machine.com evntslog - ID01 
[user@32473 iut="1" eventSource="Application" eventID="9999"] 
This is a log entry!`
```

- **Header:** The header contains details like the timestamp; the hostname, which is the name of the machine that sends the log; the application name; and the message ID. 
- **Timestamp:** The timestamp in this example is *2022-03-21T01:11:11.003Z*, where *2022-03-21* is the date in *YYYY-MM-DD* format. T is used to separate the date and the time. *01:11:11.003* is the 24-hour format of the time and includes the number of milliseconds *003*. Z indicates the time zone, which is **UTC**(***Coordinated Universal Time***). 
- **Hostname:** *virtual.machine.com* 
- **Application:** *evntslog* 
- **Message ID:** *ID01*
- **Structured-data:** The structured-data portion of the log entry contains additional logging information. This information is enclosed in square brackets and structured in key-value pairs. Here, there are three keys with corresponding values: `[user@32473 iut="1" eventSource="Application" eventID="9999"]`
- **Message:** The message contains a detailed log message about the event. Here, the message is: *This is a log entry!*.
- **PRI**(***Priority***): PRI field indicates the urgency of the logged event and is contained with angle brackets. In this example, the priority value is *<236>* . Generally, the lower the priority level, the more urgent the event is. 

***Note:*** Syslog headers can be combined with JSON, and XML formats. Custom log formats also exist.

#### JSON(*JavaScript Object Notation*)

- key-value pairs
- commas
- double quotes
- curly brackets
- square brackets

```
"User"
{ 
    "id": "1234", 
    "name": "user",
    "role": "engineer"
}
```


#### XML(*eXtensible Markup Language*) 

- language and format for storing and transmitting data.

1. **Tags** - store and identify data
2. **Elements** - include both the data contained inside of a tag and the tags itself
3.  **Attributes** - used to provide additional information about elements

```
<EventData>
    <Data Name='SubjectUserSid'>S-2-3-11-160321</Data>
    <Data Name='SubjectUserName'>JSMITH</Data>
    <Data Name='SubjectDomainName'>ADCOMP</Data>
    <Data Name='SubjectLogonId'>0x1cf1c12</Data>
    <Data Name='NewProcessId'>0x1404</Data>
</EventData>
```


#### CSV(*Comma Separated Values*) 

- uses commas to separate data values.

```
2009-11-24T21:27:09.534255,ALERT,192.168.2.7, 1041,x.x.250.50,80,TCP,ALLOWED,1:2001999:9,"ET MALWARE BTGrab.com Spyware Downloading Ads",1
```

#### CEF(*Common Event Format*) 

- uses key-value pairs to structure data and identify fields and their corresponding values.
- CEF syntax: `CEF:Version|Device Vendor|Device Product|Device Version|Signature ID|Name|Severity|Extension`

```
Sep 29 08:26:10 host CEF:1|Security|threatmanager|1.0|100|worm successfully stopped|10|src=10.0.0.2 dst=2.1.2.2 spt=1232
```

---

#IDS

## 4.02 - IDS

- **Telemetry** - collection and transmission of data for analysis
- **IDS** (***Intrusion Detection System***) - an application that monitors activity and alerts on possible intrusions
- **Endpoint** - any device connected on a network

1. **HIDS** (***Host-based IDS***) 
	- an application that monitors the activity of the host on which it's installed. 
	- Host is also known as endpoint.
	- installed on individual hosts

![[HIDS.png]]

2. **NIDS** (***Network-based IDS***) 
	- an application that collects and monitors network traffic and network data.
	- installed on a network
	- Components of a NIDS Rule:
		1. **Action** - determines the action to take if the rule criteria is met. Alert, Pass, Reject
		2. **Header** - source and destination IP addresses and ports, protocols, and traffic direction
		3. **Rule Options** - provide different options to customize signatures

![[NIDS.png]]

### 4.02.01 - Detection Techniques

1. **Signature Analysis** 
	- it's a detection method used to find events of interest. 
	- A **signature** is a pattern that is associated with malicious activity. 
	- *Advantage:* low rate of false positives
	- *Disadvantages:* signatures can be evaded, requires regular updates, and are unable to detect unknown threats

2. **Anomaly-based Analysis**
	- it is a detection method that identifies abnormal behavior.
	- 2 phases: 
		1. **Training phase** - a baseline of normal or expected behavior must be established.
		2. **Detection phase** - current system activity is compared against the baseline.
	- *Advantage:* ability to detect new and evolving threats
	- *Disadvantage:* high rate of false positives, pre-existing compromise (existence of an attacker during training phase will include malicious behavior in the baseline)

---

#siem 

## 4.03 - SIEM Tools

- **SIEM** - an application that collects and analyzes log data to monitor critical activities in an organization.
- Splunk uses its own **SPL** (***Search Processing Language***)
- Chronicle uses **YARA-L**, a computer language used to create rules for searching through ingested log data. Types of Search:
	1. **UDM** (***Unified Data Model***) search
	2. Raw log search

### 4.03.01 - SIEM Process

1. Collect and aggregate data
2. Normalize data - convert data into a standard format to maintain consistency.
3. Analyze data

- **Log ingestion** is the process of collecting and importing data from log sources into a SIEM tool. In log ingestion, the SIEM creates a copy of the event data it receives and retains it within its own storage. This copy allows the SIEM to analyze and process the data without directly modifying the original source logs.
- **Log forwarders** are software that automate the process of collecting and sending log data

---

#additional-info 

## 4.04 - Additional Information

- [Date and Time on the Internet: Timestamps](https://www.rfc-editor.org/rfc/rfc3339)
- [Generate Test Data](https://generatedata.com/)
- [Syslog Protocol](https://www.rfc-editor.org/rfc/rfc5424)
- [Data Ingestion to Chronicle](https://cloud.google.com/chronicle/docs/data-ingestion-flow)
- [Data Ingestion - Splunk](https://docs.splunk.com/Documentation/SplunkCloud/9.0.2303/Data/Howdoyouwanttoadddata)
- [Conduct a Search - Chronicle](https://cloud.google.com/chronicle/docs/review-security-alert)
- [Search - Splunk](https://docs.splunk.com/Documentation/Splunk/9.0.1/Search/GetstartedwithSearch)

---
