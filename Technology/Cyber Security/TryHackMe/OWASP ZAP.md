
#owasp-zap

## Contents :-

#### [[#01 - Intro to ZAP]]

#### [[#02 - ZAP Features]]

---

## 01 - Intro to ZAP

- OWASP Zap is a security testing framework much like Burp Suite. 
- It acts as a very robust enumeration tool. It’s used to test web applications.
- Open source and free

Feature benefits of OWASP ZAP over Burp Suite:
- **Automated Web Application Scan** - This will automatically passively and actively scan a web application, build a sitemap, and discover vulnerabilities. This is a paid feature in Burp.    
- **Web Spidering** - You can passively build a website map with Spidering. This is a paid feature in Burp.
- **Unthrottled Intruder** - You can brute force login pages within OWASP as fast as your machine and the web-server can handle. This is a paid feature in Burp.
- **No need to forward individual requests through Burp** - When doing manual attacks, having to change windows to send a request through the browser, and then forward in burp, can be tedious. OWASP handles both and you can just browse the site and OWASP will intercept automatically. This is NOT a feature in Burp.

---

## 02 - ZAP Features

### Automated Scan

- The automated scan performs both passive and automated scans to build a sitemap and detect vulnerabilities.
- A traditional spider scan is a passive scan that enumerates links and directories of the website. It builds a website index without brute-forcing. This is much quieter than a brute-force attack and can still net a login page or other juicy details, but is not as comprehensive as a bruteforce.
- The Ajax Spider is an add-on that integrates in ZAP a crawler of AJAX rich sites called Crawljax. You can use it in conjunction with the traditional spider for better results. It uses your web browser and proxy. 
- Installing Ajax Spider with HTMLUnit: 
	- To install HTML Unit use the command: `sudo apt install libjenkins-htmlunit-core-js-java`
	- And then select HtmlUnity from the Ajax Spider Dropdown. 


---

#additional-info 

## Additional Information

- [OWASP ZAP - Download](https://www.zaproxy.org/download/)
- [ZAP-extensions](https://github.com/zaproxy/zap-extensions)
- [Bugcrowd - HUNT](https://github.com/bugcrowd/HUNT)

---
