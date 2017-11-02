# attacking web authentication

attack techniques:

  * username enumeration
  * password guessing
  * eavesdropping

## username enumeration

* error message login
* registration
* account lockout : unlock account after 30m, 1h, 24h
* timing attack

## password guessing

* manual password guessing
* automated password guessing:


### countermeasures for username enumeration and password guessing

* The most effective countermeasures against password guessing is a combination of a strong password policy and
a strong account lockout policy. After a small number of unsuccessful login attempts, the application should
lock the account to limit the exposure from this type of attack.

* add additional authentication (captcha)

* apply multifactor authentication

ebay: tracking ip address + account (to prevent access to the system from different ip)


## eavesdropping and replay attacks

eavesdropping: secret listen to a conversation
