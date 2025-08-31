
#hydra

## Contents :-

#### [[#01 - Hydra Introduction]]
#### [[#02 - Hydra Commands]]
#### [[#03 - Additional Information]]

---

## 01 - Hydra Introduction

- Hydra is a brute force online password cracking program, a quick system login password “hacking” tool.
- Hydra can run through a list and “brute force” some authentication services. 
- If a password is common, doesn’t contain special characters and is not above eight characters, it will be prone to be guessed. 
- CCTV cameras and web frameworks often use `admin:password` as the default login credentials, which is obviously not strong enough.
- `apt install hydra`: install Hydra on Ubuntu

---

## 02 - Hydra Commands

- The options passed into Hydra depend on which service (protocol) is the target.

### SSH

- `hydra -l <username> -P <full path to pass> 10.10.128.174 -t 4 ssh`

|Option|Description|
|---|---|
|`-l`|specifies the (SSH) username for login|
|`-P`|indicates a list of passwords|
|`-t`|sets the number of threads to spawn|

### POST Web Form

- Hydra can be used to brute force web forms too. 
- You must know which type of request it is making; GET or POST methods are commonly used. You can use your browser’s network tab (in developer tools) to see the request types or view the source code.

- `sudo hydra <username> <wordlist> 10.10.128.174 http-post-form "<path>:<login_credentials>:<invalid_response>"`

|Option|Description|
|---|---|
|`-l`|the username for (web form) login|
|`-P`|the password list to use|
|`http-post-form`|the type of the form is POST|
|`<path>`|the login page URL, for example, `login.php`|
|`<login_credentials>`|the username and password used to log in, for example, `username=^USER^&password=^PASS^`|
|`<invalid_response>`|part of the response when the login fails|
|`-V`|verbose output for every attempt|


---

#additional-info 

## 03 - Additional Information

- [Hydra - Github](https://github.com/vanhauser-thc/thc-hydra)
- [Hydra Help](https://en.kali.tools/?p=220)

---