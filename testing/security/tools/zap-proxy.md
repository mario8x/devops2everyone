# zap
https://github.com/zaproxy/zaproxy/wiki/ZAP-Articles
https://www.youtube.com/watch?v=ZWSLFHpg1So&index=3&list=PLEBitBW-Hlsv8cEIUntAO8st2UGhmrjUB
```
an easy to use webapp pentest tool

```

* source: https://github.com/zaproxy/zaproxy

* download:
* install


# features

## Intercepting proxy

Tools > Options:
* Dynamic SSL Certificate: generate ssl certificate to capture https request
* Local Proxy : default port is 8080 (change port to resolve conflicts with webgoat or apache defaul port)
* Break: to intercept and edit then transfer a request

## Quick Start

* To scan security vulnerabilities
* Alerts : display the url and the vulnerability detected in the right side of the information Window.

## Active and Passive Scanners

### Spider (Passive Scan)

* by default passively scans all HTTP messages (request and responses) sent to the web application being tested.
Passive scanning does not change the requests nor the responses in any way and is therefore safe to use.

* In the Site tab, right click select Spider

### Active Scan

* Attempts to find potential vulnerabilities by using known attacks against the selected targets.
* In the Site tab, right click then select Active Scan
* Options Active Scan: num of hosts, concurrent scanning threads per host, max results list...
    https://github.com/zaproxy/zap-core-help/wiki/HelpUiDialogsOptionsAscan

## Report Generation

## Brute Force (Using OWASP DirBuster code)

## Fuzzing (using fuzzdb & OWASP JBroFuzz)

Fuzzing is a technique of submitting lots of invalid or unexpected data to a target.
Allows you to fuzz any request still using:
* A build in set of payloads
* Payloads defined by optional add-ons
* Custom scripts

## Extensibility:

## Additional features

* Auto tagging
* Port scanner
* Parameter analysis
* Smart card support
* Session comparison
* Invoke external apps
* API + Headless mode
* Dynamic SSL Certificates
* Anti CSRF token handling

# Practices

## A simple penetration test

* Configure your browser to proxy via ZAP
* Explore the application manually
* Use the spider to find `hidden` content
* See what issues the Passive Scanner has found
* Use the Active Scanner to find vulnerabilities
