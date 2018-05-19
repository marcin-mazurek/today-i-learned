# Notes from Web Apps Security training from Niebezpiecznik.pl
Training agenda: [niebezpiecznik.pl/szkolenia/atakowanie-ochrona-www/](https://niebezpiecznik.pl/szkolenia/atakowanie-ochrona-www/)

## Tools, apps, websites
* [Kali Linux](https://www.kali.org/) - Penetration Testing Linux Distribution
* Network security tools
  * [nmap](https://nmap.org) - network exploration tool and port scanner
  * [tcpdump](https://danielmiessler.com/study/tcpdump) - analysing network traffic (CLI)
  * [Wireshark](https://www.wireshark.org) - analysing network traffic (GUI)
  * [dnsenum](https://github.com/fwaeytens/dnsenum) - gathering public information about domains/DNS config, allows for sub-domain bruteforcing
  * `whois`, `host` - checking domain info
* Penetration testing tools / scanners
  * [OWASP ZAP](https://www.owasp.org/index.php/OWASP_Zed_Attack_Proxy_Project) - multipurpose penetration testing tool for finding vulnerabilities in web applications
  * [Acunetix](https://www.acunetix.com)
  * [IBM AppScan](https://www.ibm.com/security/application-security/appscan)
  * [Metasploit](https://www.metasploit.com/)
  * [skipfish](https://github.com/spinkham/skipfish)
  * [Nikto](https://cirt.net/Nikto2)
* JavaScript related
  * [/packer/](http://dean.edwards.name/packer/) - JavaScript compressor / obfuscator
  * [JSFuck](http://www.jsfuck.com/) - writes any JavaScript using 6 characters - `()+[]!`
  * [https://chrome.google.com/webstore/detail/hackbar/ejljggkpbkchhfcplgpaegmbfhenekdc?hl=en](HackBar) - a Chrome extension for testing against SQL injections, XSS holes, etc.
  * [http://beefproject.com/](BeEF) - penetration testing tool that focuses on the web browser security
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
* **Principle of least privilege** (or stubborn admin rule) - do not give a permission to a resource up-front, unless the user really needs it
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
* Do not keep real data on test/pre-production servers. If you have to, use anonymised data instead
* Remember about different application versions - eg. if you have a separate mobile and desktop version, and find a security issue in one of them, check if it exists in the other one
* Never show application/library versions (hackers can search for a specific security holes for given version)
* Before deploying to production for the first time, perform server hardening - basically, make the server secure
* Block / hide any debugging capabilities in production

## Personal security
* Use two factor authentication
* [umatrix](https://chrome.google.com/webstore/detail/umatrix/ogfcmafjalglgifnmanfmnieipoejdcf?hl=en) - in-browser firewall extension, blocks malware domains, allows for flexible setup
* If you type a password on a website, make sure it uses SSL
* Do not use untrusted VPN services
* To avoid socio-technical attacks, don't trust others, do not give away information

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
* Blind SQL injection attack - an attack where there's no actual SQL output and no error. An attacker can only guess that a page is vurnerable, for example by appending ` AND 1=1` or ` AND 1=2` and seeing how the application behaves
* Time-based blind SQL injection attack - an attack in which `sleep(x)` function is added. If the page responds with a given delay, it means that the page is vulnerable
* SQL injection can be even used to execute a shell command
* Tools to check against SQL injection:
  * [sqlmap](http://sqlmap.org)
* How to stay secure:
  * Stored procedures
  * Prepared statements / bind variables

## HTTP related attacks
* Do not perform `GET` requests with any sensitive data - it will be stored in logs, and the URL may be visible if you're using TLS with SNI
* Do not trust HTTP headers. Each header can be overwritten
* Use HSTS - Strict-Transport-Security response header that tells a browser that it can be only accessed using HTTPS, instead of using HTTP. Doing just a redirect is not safe - the first request (with potentially unsafe data) will not be encoded and can be captured by HTTP sniffer
* Sign your JSONs with eg. JSON Web Signature, to protect from users modifying data with a proxy and eg. enabling premium features for free
* SSL pinning - making sure the client checks the server’s certificate against a known copy of that certificate, to prevents a man-in-the-middle attacks using a fake, but trusted certificate
* Forceful browsing attack - accessing resources that are not linked anywhere
  * If you detect a HTTP bruteforce attack, you can return 200 rather than 404, to mislead the attacker
  * Hide directory listings
  * Do not rename files on a server from eg. `index.php` to `index.php.backup`. Such files can be downloaded and source code can be compromised

## Browser attacks
* XSS - cross-site scripting - injection of malicious scripts into trusted web sites
  * Allows to steal any page content, swap links, mislead user, steal cookies
  * If a browser is vurnerable, it can take over the entire operating system
  * How to protect against it:
    * Verify user input - block/validate scripts and HTML tags
      * If possible - do not allow any HTML tags at all. Use something like Markdown or BB Code if you need formatting
      * Prefer whitelisting over blacklisting
      * To execute JavaScript on content load you don't need a script tag - you can also use `<img onload=...>`
    * Validate data both when reading and saving data
  * What to watch out for:
    * Any JavaScript can be written using the following 6 characters: `()+[]!` (see http://www.jsfuck.com)
    * XSS can be done through URL, which can be eg. sent by email
    * Stored XSS - data earlier saved to database
  * [Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP) header can help mitigate XSS if it occurs
* CRSF or XRSF - cross-site request forgery - also called as single-click attack, occurs when loading or interacting with one website, which maliciously interact with another
  * How to protect against it:
    * Use CRSF token
      * One-off token - can be problematic when working with multiple tabs, as each page reload will generate a new token
      * With limited life time, eg. 24h
      * Must be assigned to a single user
    * Require additional validation before accessing sensitive information (as when accessing user data on Ebay/Allegro)
  * What to watch out for:
    * Mutating data, especially deliting with GET request (this way data can be mutated even using CSS background!)
* File upload
  * Verify multiple things:
    * Mime type
    * First bytes
    * Extension
  * Assign new, random names to uploaded files
  * Remove comments from files
  * Compress images even by 1%
  * Use separate server for upload (without any language interpreter)

## User session attacks
* Session hijacking - gaining unauthorized access to a website by stealing or guessing a session token. Token can be compromised by:
  * being predictable/easy to guess
  * session sniffing - unsecure connection
  * client-side attacks like XSS, spyware
  * man-in-the-middle attack
* Securing against user session stealing:
  * First, secure against XSS
  * Verify so called browser ID (bear in mind that things listed below may change even if the user remains the same, which may result in user being logged out - consider the risk and decide which ones you  on your own)
    * User agent
    * IP
    * Screen resolution
    * List of browser fonts
  
## DoS attacks
* Classic DoS/DDoS attack - performing numerous requests to the server, more than servers can handle
* Slowloris attack - sending HTTP request content very slowly, filling a server's maximum concurrent connection pool

## Decoding passwords (eg. once database content is stolen)
* How to decode a hashed password
  * Using rainbow tables - precomputed table for reversing cryptographic hash functions
  * [John The Ripper](http://www.openwall.com/john/) - bruteforce hash decoder
* How to protect against it:
  * Use strong, slow hashing algorithm with *salt* (a user specific string, eg. part of their email address, ID, etc.) and *pepper* - constant string. The currently recommended algorithm is future-proof, self-salting *Bcrypt*. It allows to define Key Factor, which is basically the cost of hashing. When computers become more powerful in the future, the passwords can be hashed again by given Key Factor to give additional protection against bruteforcing/rainbow table attack.

## Other attacks
* Directory bruteforcing - searching for specific directories/files (especially config files) using a dictionary attack
* Clickjacking - substituting or inserting hidden buttons
* Opening a page in an iframe - disablee with Content-Security–Policy or X-Frame-Options header, or in JavaScript using "framekiller" (checking the self variable)
* Path traversal in server-side includes - when there's no validation on the file name to load
  * Null-byte attack - stripping the rest of the string to eg. remove the hardcoded extension. Even if we have something like `include '/home/userx/data/' .$_GET['name']. '.jpg'`, we can strip the rest of the variable by passing a null byte. C based languages (eg. PHP) may be vulnerable
* Fuzzing - finding implementation bugs using generated malformed/semi-malformed data
  
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
