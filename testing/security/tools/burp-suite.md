# burp-suite
https://www.udemy.com/burp-suite/learn/v4/t/lecture/4170198?start=0

## Modules

1. Proxy
  * Intercept: is used to display and modify http and websockets messages that pass between your browser and web server

    ability: monitor, intercept (on/off), and modify all messages

  * Options: is used to configure proxy listeners, intercept client request, intercept server responses
  * Certificate:
    * Generate CA-signed per-host certificates: need to install burp ca
2. Repeater module:
 simple definition: take one request and repeat it

3. Target and Spider
  * target
  ```
  scope: define scope to limit what will need to focus
  ```
  * spider (web crawling)
  ```
  to begin spidering, browser to the target application, then right-click one or more nodes in the target site map, and choose "spider this host/branch"
  ```
  * benefits:
  to discover information of your site

4. Sequencer and scanner
  * sequencer : is to analyze (sessions, cookies) if it is not really random
  ```
  define custom token location : JSESSIONID=,
  ```
  * scanner (need to buy license) :auto scan security issues

5. Intruder and comparer
  * intruder:
  allows to enumerate over parameters with payloads from wordlists.
  You can use intruder to input sql injection values.

  ```
  4 attack modes
  - sniper : attack enumerates over each parameter
    format:
    1st request - param1=wordlist[0]&param2=
    2nd request - param1=wordlist[1]&param2=
    ...
    After enumerating through param1 with all the payloads from wordlist,
    1st request - param1=&param2=wordlist[0]
    2nd request - param1=&param2=wordlist[1]
    ...

  - battering ram: attack enumerates over multiple parameters with the same payload for all the parameters
    format:
    1st req - param1=wordlist[0]&param2=wordlist[0]
    2nd req - param1=wordlist[1]&param2=wordlist[1]
    ...

  - pitchfork: attack type enumerates over multiple parameters at the same time using different payloads for each parameter at the same time

    format:
    1st request - param1=wordlist1[0]&param2=wordlist2[0]
    2nd request - param1=wordlist1[1]&param2=wordlist2[1]
    ...

  - cluster bomb: attack type enumerates over multiple parameters by using all the possible combinations of payloads from the multiple wordlists.

    format:
    1st request - param1=wordlist1[0]&param2=wordlist2[0]
    2nd request - param1=wordlist1[1]&param2=wordlist2[0]
    3rd request - param1=wordlist1[2]&param2=wordlist2[0]
    ...

    After enumerating through param1 with all the payloads from wordlist1,

    1st request - param1=wordlist1[0]&param2=wordlist2[1]
    2nd request - param1=wordlist1[1]&param2=wordlist2[1]
    3rd request - param1=wordlist1[2]&param2=wordlist2[1]
    ...

  https://nitstorm.github.io/blog/burp-suite-intruder-attack-types/
  ```
  * comparer
   to compare 2 requests in intruder results

* Decoder
* Extender
* Options
* Alerts
