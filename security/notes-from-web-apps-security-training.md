# Notes from Web Apps Security training from Niebezpiecznik.pl
Training agenda: [niebezpiecznik.pl/szkolenia/atakowanie-ochrona-www/](https://niebezpiecznik.pl/szkolenia/atakowanie-ochrona-www/)

## Tools, apps
* [Kali Linux](https://www.kali.org/) - Penetration Testing Linux Distribution
* Network security tools
  * [nmap](https://nmap.org) - network exploration tool and port scanner
  * [tcpdump](https://danielmiessler.com/study/tcpdump) - analysing network traffic (CLI)
  * [Wireshark](https://www.wireshark.org) - analysing network traffic (GUI)
  * `whois`, `host` - checking domain info
* SaaS
  * [shodan.io](https://www.shodan.io) - search engine for publicly available devices, servers (often with default settings)
  * [images.shodan.io](http://images.shodan.io) - visual search engine for stuff like webcams, unsecured remote desktop, etc. ([screenshot](https://pbs.twimg.com/media/CMFfQJ9UkAQvGVs.png))
  * [stalkscan.com](http://stalkscan.com) - all 'public' info Facebook doesn't let you see (can be used to eg. prepare "personalised" attack based on interests, etc.)

## Becoming secure
* Never, ever, use default settings for stuff like login or password
* Securing against bruteforce attacks
  * reCAPTCHA (not custom captcha solution)
  * locking log in functionality temporarily for an account for a short time after eg. 3rd failure (eg. using fibonnaci sequence, for 3s, 5s, 8s and so on)
* Securing against username/email guessing
  * Generic error messages
    * Login: "The login/password is incorrect"
    * Password reminder: "If we found this email in the database, we'll send you a reset link"
  * Performing actions such as sending a password reset email asynchronously (eg. using a message bus) to avoid guessing based on the response time
  
## Vocabulary
* **Zero-day attack** - happens once software/hardware vulnerability is exploited and attackers release malware before a developer has an opportunity to create a patch to fix the vulnerability.
* **Penetration testing**
  * *White-box* hacking - working directly on source code and identifying security vurnerabilities
  * *Black-box* hacking - acting as a real hacker, trying to hack into a system/application
* **Principle of least privilege** (stubborn admin rule) - do not give a permission to a resource up-front, unless the user really needs it
* **Google hacking** - using Google search to find security vurnerabilities, eg. configuration files, vurnerable open source plugins, directory indicies
  * `site:example.com ...` - looking for a keyword on a particular website
  * `intitle:index.of ...` - looking for a directory index
  * [Bing](https://bing.com) also allows to search by IP: eg. `ip:192.30.252.153 ...` searches for pages hosted on GitHub Pages hosting

## Useful websites
* Security competitions
  * [CTFtime.org](https://ctftime.org/)
  
## To explore
- [ ] Threat modeling
- [ ] Network Address Translation
- [ ] WiFi Pineapple threat
- [ ] Apps isolation
- [ ] Server hardening
