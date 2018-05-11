# Notes from Web Apps Security training from Niebezpiecznik.pl
Training agenda: [niebezpiecznik.pl/szkolenia/atakowanie-ochrona-www/](https://niebezpiecznik.pl/szkolenia/atakowanie-ochrona-www/)

## Tools, apps, websites
* [Kali Linux](https://www.kali.org/) - Penetration Testing Linux Distribution
* Network security tools
  * [nmap](https://nmap.org) - network exploration tool and port scanner
  * [tcpdump](https://danielmiessler.com/study/tcpdump) - analysing network traffic (CLI)
  * [Wireshark](https://www.wireshark.org) - analysing network traffic (GUI)
  * `whois`, `host` - checking domain info
  * [OWASP ZAP](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project) - multipurpose penetration testing tool for finding vulnerabilities in web applications
    * Functionality:
      * brute-force file/directory search
      * ...
    * Commercial competitors:
      * [Acunetix](https://www.acunetix.com)
      * [IBM AppScan](https://www.ibm.com/security/application-security/appscan)
* SaaS
  * [shodan.io](https://www.shodan.io) - search engine for publicly available devices, servers (often with default settings)
  * [images.shodan.io](http://images.shodan.io) - visual search engine for stuff like webcams, unsecured remote desktop, etc. ([screenshot](https://pbs.twimg.com/media/CMFfQJ9UkAQvGVs.png))
  * [stalkscan.com](http://stalkscan.com) - all 'public' info Facebook doesn't let you see (can be used to eg. prepare "personalised" attack based on interests, etc.)
* [CTFtime.org](https://ctftime.org/) - security competitions
  
## Recommended books
* The Tangled Web
* The Browser Hacker's Handbook
* The Web Application Hacker's Handbook

## Glossary
* **Zero-day attack** - happens once software/hardware vulnerability is exploited and attackers release malware before a developer has an opportunity to create a patch to fix the vulnerability.
* **Penetration testing**
  * *White-box* hacking - working directly on source code and identifying security vurnerabilities
  * *Black-box* hacking - acting as a real hacker, trying to hack into a system/application
* **Principle of least privilege** (stubborn admin rule) - do not give a permission to a resource up-front, unless the user really needs it
* **Google hacking** - using Google search to find security vurnerabilities, eg. configuration files, vurnerable open source plugins, directory indicies
  * `site:example.com ...` - looking for a keyword on a particular website
  * `intitle:index.of ...` - looking for a directory index
  * [Bing](https://bing.com) also allows to search by IP: eg. `ip:192.30.252.153 ...` searches for pages hosted on GitHub Pages hosting
* **Web Server Fingerprinting** - recognizing/guessing the server engine (and possibly version) based on HTTP headers it responds with and its behaviour

## Basic security rules
* Never, ever, use default settings for stuff like login or password
* Remove metadata (especially author, path on a disk) from documents (eg. `.doc`, `.pdf`) before publishing
* Never show any error details
* Watch your logs and fix errors

## Authentication attacks
* Securing against bruteforce attacks
  * reCAPTCHA (not custom captcha solution)
  * locking log in functionality temporarily for an account for a short time after eg. 3rd failure (eg. using fibonnaci sequence, for 3s, 5s, 8s and so on)
* Securing against username/email guessing
  * Generic error messages
    * Login: "The login/password is incorrect"
    * Password reminder: "If we found this email in the database, we'll send you a reset link"
  * Performing actions such as sending a password reset email asynchronously (eg. using a message bus) to avoid guessing based on the response time
* Applications
  * [cupp](https://github.com/Mebus/cupp) - generates passwords dictionary based on personal data
  
## Authorization attacks
* Trying to access pages the logged in user shouldn't have access to
* [Burp Authorize plugin](https://github.com/Quitten/Autorize) can be used to automate verifying such scenarios

## SQL injection attacks
* Be careful with scanning text looking for SQL words - as somebody may be called W**alter** Cons**table** :)
* Blind SQL injection attack - an attack where there's no actual SQL output and no error. An attacker can only guess that a page is vurnerable, for example by appending ` AND 1=1` or ` AND 1=2` and seeing how the application behaves.  
* Time-based blind SQL injection attack - an attack in which `sleep(x)` function is added. If the page responds with a given delay, it means that the page is vulnerable.
* Tools to check against SQL injection:
  * [sqlmap](http://sqlmap.org)

## HTTP related attacks
* Do not perform `GET` requests with any sensitive data - it will be stored in logs, and the URL may be visible if you're using TLS with SNI
* Do not trust HTTP headers. Each header can be overwritten
* Sign your JSONs with eg. JSON Web Signature, to protect from users modifying data with a proxy and eg. enabling premium features for free.
* SSL pinning - making sure the client checks the server’s certificate against a known copy of that certificate, to prevents a man-in-the-middle attacks using a fake, but trusted certificate.

## DoS attacks
* Slowloris attack - sending HTTP request content very slowly, filling a server's maximum concurrent connection pool

## Other kinds of attacks
* Directory bruteforcing - searching for specific directories/files (especially config files) using a dictionary attack
* Clickjacking - substituting or inserting hidden buttons
* Opening a page in an iframe - disablee with Content-Security–Policy or X-Frame-Options header, or in JavaScript using "framekiller" (checking the self variable)
* Path traversal in server-side includes - when there's no validation on the file name to load
  * Null-byte attack - stripping the rest of the string to eg. remove the hardcoded extension. Even if we have something like `include '/home/userx/data/' .$_GET['name']. '.jpg'`, we can strip the rest of the variable by passing a null byte. C based languages (eg. PHP) may be vulnerable.
  
## To explore
- [ ] Threat modeling
- [ ] Network Address Translation
- [ ] WiFi Pineapple threat
- [ ] Apps isolation
- [ ] Server hardening
- [ ] Misconfigured zone transfers
- [ ] HTTPS vs TLS vs SSL?
- [ ] OWASP TOP 10
  - [ ] NodeGoat - https://github.com/OWASP/NodeGoat
  - [ ] WebGoat
