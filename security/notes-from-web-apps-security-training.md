# Notes from Web Apps Security training from Niebezpiecznik.pl
Training agenda: [niebezpiecznik.pl/szkolenia/atakowanie-ochrona-www/](https://niebezpiecznik.pl/szkolenia/atakowanie-ochrona-www/)

* [shodan.io](https://www.shodan.io) - search engine for publicly available devices, servers (often with default settings)
  * [images.shodan.io](http://images.shodan.io) - visual search engine for stuff like webcams, unsecured remote desktop, etc. ([screenshot](https://pbs.twimg.com/media/CMFfQJ9UkAQvGVs.png))
* Tools for analysing network traffic
  * [tcpdump](https://danielmiessler.com/study/tcpdump/) (CLI tool)
  * [Wireshark](https://www.wireshark.org/) (GUI)
* Securing against bruteforce attacks
  * reCAPTCHA (not our own captcha solution)
  * locking log in functionality temporarily for an account for a short time after eg. 3rd failure (eg. using fibonnaci sequence, for 3s, 5s, 8s and so on)
* Securing against username/email guessing
  * Generic error messages
    * Login: "The login/password is incorrect"
    * Password reminder: "If we found this email in the database, we'll send you a reset link"
  * Performing actions such as sending a password reset email asynchronously (eg. using a message bus) to avoid guessing based on the response time
 
