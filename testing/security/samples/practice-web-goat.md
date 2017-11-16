# web goat
owasp demo site

# installation

* download from git:
```
https://github.com/WebGoat/WebGoat
git clone git@github.com:WebGoat/WebGoat.git
```

* install maven in kali linux
```
https://tutorialforlinux.com/2017/04/13/how-to-install-latest-apache-maven-on-kali-linux-easy-guide/
```
* install by using mvn
```
source $HOME/.bashrc
mvn clean install

Now let's start by compiling the project.

cd WebGoat
git checkout develop
mvn clean install
Now we are ready to run the project. WebGoat 8.x is using Spring-Boot.

mvn -pl webwolf spring-boot:run
```

* run stand-alone :

```
download
https://github.com/WebGoat/WebGoat/releases
then
java -jar webgoatxxx.jar
then:
http://localhost:8080/WebGoat/login

```

# attack techniques:

I will try to practice test first then categorize them later

## General

* http/s basics: learn to intercept request by using zap/burpsuite

```
Go General/HTTP basics
Use burp suite to capture get/post method then edit and forward

result:
POST /WebGoat/HttpBasics/attack2 HTTP/1.1
magic_num=36&answer=&magic_answer=36

read the magic_numb then edit it

Identify type of request: post/get
```

* http proxies: learn how to deploy proxy on zap/burpsuite

## injection flow
https://www.owasp.org/index.php/SQL_Injection_Bypassing_WAF

  1. sql injection
  * data manipulation language (select, insert, update)
  * data definition language (create, alter, drop)
  * data control language (grant, revoke)

* numeric injection

* combining sql injection techniques
  ```
  special characters
   - /*
    '*/:comment the remainder of the query
   - ; allow query chaining  ex: 'select * from users; drop table users;'
   - || allow string concatenate
   - union : 'Select id, text from news union all select name, pass from users'
   - joins
  ```
* blind sql injection
```
```

  2. examples:
```
- simple sql injection:
serName = Smith' or '1'='1
userName =' or 1=1 --
userID = 1234567 or 1=1
UserName = Smithâ€™;drop table users; truncate audit_log;--

- advance sql injection:
Smith'; select * from user_system_data where '1'='1

-blind sql injection:
https://my-shop.com?article=4
>> SELECT * from articles where article_id = 4

```

  3. practices:
  * simple sql injection
```
http://localhost:8080/WebGoat/start.mvc#lesson/SqlInjection.lesson/6
input: Smith' or '1'='1
then submit

http://localhost:8080/WebGoat/start.mvc#lesson/SqlInjection.lesson/7
input : 123456 or 1=1
then submit

```
  * advance sql injection
  ```
  http://localhost:8080/WebGoat/start.mvc#lesson/SqlInjectionAdvanced.lesson/2
  6.a input: Smith'; select * from user_system_data where '1'='1
  105, dave, dave, ,
  6.b input: dave
  ```

  * combine all: burpsuite: could user repeater module to input data to save time to make request
  ```
  http://localhost:8080/WebGoat/start.mvc#lesson/SqlInjectionAdvanced.lesson/4
  tried : http://sechow.com/bricks/docs/login-1.html but failed

  ```

  4. sql injection mitigations

  ```
  use order by
  http://192.168.60.148:8080/WebGoat/SqlInjection/servers?column=id
  edit query:
  column=(case when (true) then hostname else id end)

  input ip address: 192.168.6.4
  click submit
  ```

## Authentication flows

### Authentication bypasses
https://henryhoggard.co.uk/blog/Paypal-2FA-Bypass
1. concept:
usually take advantage of some flaw in the configuration or logic

* hidden inputs
* removing parameters
* forced browsing

2. practices:
There are many ways to practice this:
check hidden account which comment in source
remove parameters/change parameters name

```
http://localhost:8080/WebGoat/start.mvc#lesson/AuthBypass.lesson/1
intercept the post method
secQuestion0=test&secQuestion1=test&jsEnabled=1&verifyMethod=SEC_QUESTIONS&userId=12309746

change the parameter name:
secQuestion3=test&secQuestion4=test&jsEnabled=1&verifyMethod=SEC_QUESTIONS&userId=12309746

magicly it passed
```

### JWT tokens (under development)
https://jwt.io/introduction/

## Cross Site Scripting(XSS)

Cross-site script (also commonly known as XSS) is a vulnerability/flaw that combines …​ # the allowance of html/script tags as input that are …​ # rendred into a browser without encoding or sanitization

### Goals

* understand how XSS works
* understand best practices for defending against XSS injection attacks
* demonstrate knowledge on:
  * Reflected XSS injection
    ```
    malicious content from a user request: displayed to the user, written into the page
    social engineering
    runs with browser privileges inherited from user in browser
    ```
  * Stored XSS injections
  ```
  malicious content is stored on the server (in a database, file system, or other object) and later displayed to users in a web browser
  social engineering is not required

  ```
  * Dom-based XSS injection (also technically reflected )
  ```
    malicious content from a user request: by client-side scripts to write html
  ```
### Most common Locations

* search fields, input fields, error messages, hidden fields, pages: messages boards, free form comments, and http headers.

### XSS attacks may result in

* steal session cookie, create false request, create false fields, redirect your site,
* create a request that masquerade as a valid user
* execute malicious code on an end-user system (active scripting)
* insert inappropriate content

### Practices
```
data to check xss:
<i>
<i> hello </i>
<img src="images/logos/owaps.jpg"/>
<img src=x onerror=;;alert('xss')/>
phoneHome Response is..."><script>webgoat.customjs.phoneHome();</script>

```

```
1. simple: concurrency flows

http://localhost:8080/WebGoat/start.mvc#lesson/CrossSiteScripting.lesson/1
open 2 tabs and input: javascript:alert(document.cookie) you will see that 2 tabs have the same cookies
input answer: yes then click submit button

2. reflected xss scenario
http://localhost:8080/WebGoat/start.mvc#lesson/CrossSiteScripting.lesson/6
step 1. purchase with low value
step 2. update cart with high prices

3. dom-based xss
find the test route to exploit the javascript function
http://localhost:8080/WebGoat/start.mvc#lesson/CrossSiteScripting.lesson/9
not solved yet

4. blind
http://localhost:8080/WebGoat/start.mvc#lesson/CrossSiteScripting.lesson/10
console: run command `webgoat.customjs.phoneHome()`
open server running console to copy random value then input and submit

5. stored xss:

https://www.owasp.org/index.php/Testing_for_Stored_Cross_site_scripting_(OTG-INPVAL-002)

  * post malicious script to a message board  > database
  * victim read message > malicious script send sensitive information to attackers
  http://localhost:8080/WebGoat/start.mvc#lesson/CrossSiteScripting.lesson/12

   Input comment: phoneHome Response is..."><script>webgoat.customjs.phoneHome();</script>
   it will turn to : <input class="inputbox" type="text" name="email" size="40" value="phoneHome Response is..."> MALICIOUS CODE <!-- />
   then read value response by using proxy and input to the answer
```
#### Mitigations

* encoding all the inputs to avoid attacks

## Access Control Flaws

https://www.owasp.org/index.php/Top_10_2013-A4-Insecure_Direct_Object_References

### Direct Object References

when an application uses client-provided input to access data and objects.

```
ex: Examples of Direct Object References using the GET method may look something like

https://some.company.tld/dor?id=12345

https://some.company.tld/images?img=12345

https://some.company.tld/dor/12345
```

### Insecure Direct Object References

```
https://some.company.tld/app/user/23398

... and you can view your profile there. What happens if you navigate to:

https://some.company.tld/app/user/23399 …
```

### Practices
```
I. Insecure direct object references

1. Authentication first, abuse authorization later
 http://localhost:8080/WebGoat/start.mvc#lesson/IDOR.lesson/1
 input: tom/cat

 http://localhost:8080/WebGoat/start.mvc#lesson/IDOR.lesson/2
 use proxy to capture responses,
 You will see 2 paramers: `userId, role` then input and subimit diffs
2. guessing and predicting patterns
http://localhost:8080/WebGoat/start.mvc#lesson/IDOR.lesson/3
capture the userId from the previous request ex: userId=2342384
input:WebGoat/IDOR/profile/2342384

II. missing function level access control

1. finding hidden items
http://localhost:8080/WebGoat/start.mvc#lesson/MissingFunctionAC.lesson/1
Inspect tag: hidden-menu-item
You will find: Users, Config
Input hidden item 1, 2: Users, Config

2. parameter tampering
is a form of web-based attack in which certain parameters in the Uniform Resource Locator(URL)
or web page form field data entered by a user are changed without that user's authorization.

parameter tampering can often be done with:
* Cookies
* Form Fields
* URL Query Strings
* HTTP Headers

http://localhost:8080/WebGoat/start.mvc#lesson/MissingFunctionAC.lesson/2
not solved yet.

```

## Insecure communication

### Insecure login
  encryption is a very important tool for secure communication.

### Practices
```
http://localhost:8080/WebGoat/start.mvc#lesson/InsecureLogin.lesson/1
click login
use sniffer tool to capture login info
input captured user info in to textbox then click submit
CaptainJack/BlackPearl
```
## Client Side

### Client side filtering
When have too much information is being sent to the client, creating a serious access control problem.

### Bypass front-end restrictions

users have a great degree of control over the front-end of the web application. They can alter HTML code, sometimes also scripts.
This is why apps that require certain format of input should also validate on server side

### Html tampering

Browsers generally offer many options of editing the displayed content. Developers therefore must be aware that the values sent by the user may have been tampered with

### Practices

```
1. client side filtering:
http://localhost:8080/WebGoat/start.mvc#lesson/ClientSideFiltering.lesson/1
just find the hidden table which contains information of Neville Bartholomew
Edit option value: in list select user: 112
the salary will be: 450000

2. bypass front-end restrictions

2.1 field restrictions
http://localhost:8080/WebGoat/start.mvc#lesson/BypassRestrictions.lesson/1
inspect elements
* select field: change it
<select name="select" multiple>
* radio button : change them
<input type="checkbox" name="radio".....>
* checkbox: change it
<input type="text" name="checkbox"...>
* Input restricted max 5 characters: change maxlength to 10
click submit  

2.2 Validation:
http://localhost:8080/WebGoat/start.mvc#lesson/BypassRestrictions.lesson/2
search validate() javascirpt function
I tried 2 ways:
1. capture and edit 7 field then send request then click submit
2. remove validate function and edit 7 fields then click submit

3. Html tampering
http://192.168.60.148:8080/WebGoat/start.mvc#lesson/HtmlTampering.lesson/1
just intercept the request then edit the total, and quantity the forward request
```
## Request forgeries  (xsrf)

attack forces an authenticated user(victim) to send a forged http request, including the victim's session cookie to a vulnerable web application
which allows the attacker to force the victim's browser to generate request such that the vulnerable app perceives as legitimate from the victim

* session hijacking and cross-site request


## refrences

https://www.owasp.org/index.php/Testing_for_Stored_Cross_site_scripting_(OTG-INPVAL-002)
