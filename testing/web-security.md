## Security
References: Hacking Exposed Web Applications, Third edition
http://www.webhackingexposed.com


### techniques
#### security 101

3 simple ways to hack:
  directly manipulating the application via its gui
  tampering with the Uniform Resource Identifier(URI)
  Tampering with HTTP elements not contained in the URI

* gui web hacking
  as sql injection : ``` `Or 1=1--```

* methods, headers, and body
  methods : get, post...
  headers:
  Authorization: define whether certain types of authentication are used with the request.
  Cache-control
  Referer
  Cookies

* Resources
  ultimate goal is to gain unauthorized access to web application resources

* authentication, sessions, and authorization

* other protocols
Web Distributed Authoring and Versioning (WebDAV)
SOAP
RSS
AJAX
User generated content (UGC)

* who, when, and where :

* Weak spots:
  web platform
    server : IIS, apache
    framework: asp.net, php
  web application: authentication, authorization, site structure, input validation, application logic, and management interfaces
  database: sql injection
  web client: cross site scripting attact (CSS) fraud-like phishing.
  transport : SSL redirection
  availability (DoS)

* Browser extensions: integration with browsers, transparency(require stand-alone proxies)
  IE extensions:
    TmperIE is a browser helper object (BHO)
    IEWatch
    IEHeaders

  Firefox extensions:
    LiveHTTPHeaders: display raw http/s, edit any portion of the request
    TamperData: trace and modify http/s include headers and post
    Modify Headers

* HTTP Proxies:(man in the middles)
  Paros Proxy
  OWASP WebScarab: http proxy, crawler/spider, sessionID analysis, script interface for automation, fuzzer, encoder/decoder utility for all of the popular web format
  (base64, md5...), WSDL and SOAP parser
  ProxMon: analyze WebScarab's Temporary or Save directories, examines all transaction logs, and reports security-relevant events, including important variables in set cookies
  as well as performing vulnerability checkes based on its included library.
  Fiddler: windows only, automatically configures IE to use its local proxy
  Burp Intruder: java-based http proxy with numerous web application security testing features.
  Google Ratproxy: is designed for security professionals with a subtantial understanding of web app security issues and the experience to use it effectively. Command-line tool
  natively in Unix/Linux. To run on Win: need to run in a Unix/Linux emulation environment like Cygwin

* Command-line tools:
  cURL: is a free, multiplatform command-line tool for manipulating HTTP/S. it's particularly powerful when scripted to perform iterative analyses.
  Netcat: "Swiss Army Knife" of networking hacking, is elegant for many tasks
  SSL proxy
  OpenSSL
  Stunnel
  
### tools

### how to prevent/fix
