# hacking web clients

## client attacks

1. Exploits:

Malicious actions or code is executed on the web client and its host system via an overt vulnerability. This includes software bugs and/or
misconfiguration that cause undesired behavior to occur.

Ex: the attacker will need to get victims to view web content containing exploit code by sending email, or leverage malicious search engine optimization (SEO)
techniques to place pages containing malware at the top of Google results.

* Json hijacking
* Rich Internet application vulnerabilities
* cross-domain exploitation
* java vulnerabilities
* client plug-in attacks
* abusing active x
* The evil side of firefox extensions
* xul (user interface language)
* client-side storage: many security risks are exposed when web applications store data on the client.

2. Trickery

The use of trickery to cause the human operator of the web client software to send valueable information to the attacker, regardless of any overt vulnerabilities in the client platform.
The attacker in essence "pokes" the client with some attractive message, and then the client (and/or its human operator) sends sensitive information directly to the attacker or install
some software that the attacker then uses to pull data from the client system.

Phising

* targeted at users of online finance sites
* Invalid or illicit source addresses
* Spoof authenticity using familiar brand imagery
* Compels action with urgency

Clickjacking

* Bypasses this form of protection by placing the victim's mouse over the target area that the attacker want the victim to click.

Malicious IFRAMEs

* Malicious IFRAME tags are leveraged more and more to subvert web client protection mechanisms and target users with new advanced phising techniques.
