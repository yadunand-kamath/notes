
#burpsuite

## Contents :-

#### [[#01 - Burp Suite Introduction]]
#### [[#02 - Dashboard]]
#### [[#03 - Burp Proxy]]
#### [[#04 - Target Tab]]
#### [[#05 - Proxying HTTPS]]
#### [[#06 - Repeater]]

---

## 01 - Burp Suite Introduction

- Burp Suite is a Java-based framework designed to serve as a comprehensive solution for conducting web application penetration testing.
- It captures and enables manipulation of all the HTTP/HTTPS traffic between a browser and a web server. By intercepting requests, users have the flexibility to route them to various components within the Burp Suite framework
- The ability to intercept, view, and modify web requests before they reach the target server or even manipulate responses before they are received by our browser makes Burp Suite an invaluable tool for manual web application testing.

### Key Features

- **Proxy** - The Burp Proxy enables interception and modification of requests and responses while interacting with web applications.
- **Repeater**: Repeater allows for capturing, modifying, and resending the same request multiple times. This functionality is particularly useful when crafting payloads through trial and error (e.g., in SQLi - Structured Query Language Injection) or testing the functionality of an endpoint for vulnerabilities.
- **Intruder**: Despite rate limitations in Burp Suite Community, Intruder allows for spraying endpoints with requests. It is commonly utilized for brute-force attacks or fuzzing endpoints.
- **Decoder**: Decoder offers a valuable service for data transformation. It can decode captured information or encode payloads before sending them to the target.
- **Comparer**: Comparer enables the comparison of two pieces of data at either the word or byte level. While not exclusive to Burp Suite, the ability to send potentially large data segments directly to a comparison tool with a single keyboard shortcut significantly accelerates the process.
- **Sequencer**: Sequencer is typically employed when assessing the randomness of tokens, such as session cookie values or other supposedly randomly generated data. If the algorithm used for generating these values lacks secure randomness, it can expose avenues for devastating attacks.

---

## 02 - Dashboard

The Burp Dashboard is divided into four quadrants:

1. **Tasks** - The Tasks menu allows you to define background tasks that Burp Suite will perform while you use the application. Burp Suite Professional offers additional features like on-demand scans.
2. **Event log** - The Event log provides information about the actions performed by Burp Suite, such as starting the proxy, as well as details about connections made through Burp.
3. **Issue Activity** - This section is specific to Burp Suite Professional. It displays the vulnerabilities identified by the automated scanner, ranked by severity and filterable based on the certainty of the vulnerability.
4. **Advisory** - The Advisory section provides more detailed information about the identified vulnerabilities, including references and suggested remediations. This information can be exported into a report. In Burp Suite Community, this section may not show any vulnerabilities.

### Navigation Shortcuts

|Shortcut|Tab|
|---|---|
|`Ctrl + Shift + D`|Dashboard|
|`Ctrl + Shift + T`|Target tab|
|`Ctrl + Shift + P`|Proxy tab|
|`Ctrl + Shift + I`|Intruder tab|
|`Ctrl + Shift + R`|Repeater tab|

---

## 03 - Burp Proxy

The Burp Proxy enables the capture of requests and responses between the user and the target web server. This intercepted traffic can be manipulated, sent to other tools for further processing, or explicitly allowed to continue to its destination.

- **Intercepting Requests** - When requests are made through the Burp Proxy, they are intercepted and held back from reaching the target server. The requests appear in the Proxy tab, allowing for further actions such as forwarding, dropping, editing, or sending them to other Burp modules. To disable the intercept and allow requests to pass through the proxy without interruption, click the `Intercept is on` button.
- **Taking Control** - The ability to intercept requests empowers testers to gain complete control over web traffic, making it invaluable for testing web applications.  
- **Capture and Logging** - Burp Suite captures and logs requests made through the proxy by default, even when the interception is turned off. This logging functionality can be helpful for later analysis and review of prior requests.
- **WebSocket Support** - Burp Suite also captures and logs WebSocket communication, providing additional assistance when analyzing web applications.
- **Logs and History** - The captured requests can be viewed in the **HTTP history** and **Web Sockets history** sub-tabs, allowing for retrospective analysis and sending the requests to other Burp modules as needed.

### Useful Proxy Settings

- **Response Interception** - By default, the proxy does not intercept server responses unless explicitly requested on a per-request basis. The "Intercept responses based on the following rules" checkbox, along with the defined rules, allows for a more flexible response interception.
- **Match and Replace** - The "Match and Replace" section in the **Proxy settings** enables the use of regular expressions (regex) to modify incoming and outgoing requests. This feature allows for dynamic changes, such as modifying the user agent or manipulating cookies.

---

## 04 - Target Tab

The **Target** tab in Burp Suite provides more than just control over the scope of our testing. It consists of three sub-tabs:

1. **Site map**: This sub-tab allows us to map out the web applications we are targeting in a tree structure. Every page that we visit while the proxy is active will be displayed on the site map. This feature enables us to automatically generate a site map by simply browsing the web application. In Burp Suite Professional, we can also use the site map to perform automated crawling of the target, exploring links between pages and mapping out as much of the site as possible. Even with Burp Suite Community, we can still utilize the site map to accumulate data during our initial enumeration steps. It is particularly useful for mapping out APIs, as any API endpoints accessed by the web application will be captured in the site map.
2. **Issue definitions**: It provides an extensive list of web vulnerabilities, complete with descriptions and references. This resource can be valuable for referencing vulnerabilities in reports or assisting in describing a particular vulnerability that may have been identified during manual testing.
3. **Scope settings**: This setting allows us to control the target scope in Burp Suite. It enables us to include or exclude specific domains/IPs to define the scope of our testing. By managing the scope, we can focus on the web applications we are specifically targeting and avoid capturing unnecessary traffic. By setting a scope for the project, we can define what gets proxied and logged in Burp Suite. 
	- We can restrict Burp Suite to target only the specific web application(s) we want to test. The easiest way to do this is by switching to the `Target` tab, right-clicking on our target from the list on the left, and selecting `Add To Scope`. Burp will then prompt us to choose whether we want to stop logging anything that is not in scope, and in most cases, we want to select `yes`.
	- To check our scope, we can switch to the `Scope settings` sub-tab within the `Target` tab.
	- However, even if we disabled logging for out-of-scope traffic, the proxy will still intercept everything. To prevent this, we need to go to the **Proxy settings** sub-tab and select `And` `URL` `Is in target scope` from the "Intercept Client Requests" section.

Overall, the **Target** tab offers features beyond scoping, allowing us to map out web applications, fine-tune our target scope, and access a comprehensive list of web vulnerabilities for reference purposes.

---

## 05 - Proxying HTTPS

- When intercepting HTTP traffic, we may encounter an issue when navigating to sites with TLS enabled. We may receive an error indicating that the PortSwigger Certificate Authority (CA) is not authorized to secure the connection. This happens because the browser does not trust the certificate presented by Burp Suite.
- To overcome this issue, we can manually add the PortSwigger CA certificate to our browser's list of trusted certificate authorities. Here's how to do it:
	1. **Download the CA Certificate:** With the Burp Proxy activated, navigate to http://burp/cert. This will download a file called `cacert.der`. Save this file somewhere on your machine.
	2. **Access Firefox Certificate Settings:** Type `about:preferences` into your Firefox URL bar and press **Enter**. This will take you to the Firefox settings page. Search the page for "certificates" and click on the **View Certificates** button.
	3. **Import the CA Certificate:** In the Certificate Manager window, click on the **Import** button. Select the `cacert.der` file that you downloaded in the previous step.
	4. **Set Trust for the CA Certificate:** In the subsequent window that appears, check the box that says "Trust this CA to identify websites" and click OK.

---

## 06 - Repeater

- Burp Suite Repeater enables us to modify and resend intercepted requests to a target of our choosing. It allows us to take requests captured in the Burp Proxy and manipulate them, sending them repeatedly as needed. 
- Alternatively, we can manually create requests from scratch, similar to using a command-line tool like cURL.
- The Repeater interface consists of six main sections:
	1. **Request List** - Located at the top left of the tab, it displays the list of Repeater requests. Multiple requests can be managed simultaneously, and each new request sent to Repeater will appear here.
	2. **Request Controls** - Positioned directly beneath the request list, these controls allow us to send a request, cancel a hanging request, and navigate through the request history.
	3. **Request and Response View** - Occupying the majority of the interface, this section displays the **Request** and **Response** views. We can edit the request in the Request view and then forward it, while the corresponding response will be shown in the Response view.
	4. **Layout Options** - Located at the top-right of the Request/Response view, these options enable us to customize the layout of the Request and Response views. The default setting is a side-by-side (horizontal) layout, but we can also choose a vertical layout or combine them in separate tabs.
	5. **Inspector** - Positioned on the right-hand side, the Inspector allows us to analyze and modify requests in a more intuitive manner than using the raw editor. 
	6. **Target** - Situated above the Inspector, the Target field specifies the IP address or domain to which the requests are sent. When requests are sent to Repeater from other Burp Suite components, this field is automatically populated.
- Once a request has been captured in the Proxy module, we can send it to Repeater by either right-clicking on the request and selecting **Send to Repeater**, or by utilizing the keyboard shortcut `Ctrl + R`.
- Repeater provides us with various request and response presentation options:
	1. **Pretty** - This is the default option, which takes the raw response and applies slight formatting enhancements to improve readability.
	2. **Raw** - This option displays the unmodified response directly received from the server without any additional formatting.
	3. **Hex** - By selecting this view, we can examine the response in a byte-level representation, which is particularly useful when dealing with binary files.
	4. **Render** - The render option allows us to visualize the page as it would appear in a web browser. While not commonly utilized in Repeater, as our focus is usually on the source code, it still offers a valuable feature. For most scenarios, the **Pretty** option is generally sufficient. However, it is beneficial to be acquainted with the usage of the other three options.