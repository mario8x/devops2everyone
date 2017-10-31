# Profiling
* tools:
http://sectools.orgs
https://www.shodan.io/
http://www.cygwin.com/

* Infrastructure Profiling
  * off-the-shelf components of the web application > usually vulnerabilities in these components are easy to identify and subsequent exploit.

* Application Profiling
  * Addresses the unique structure, logic, and features of an individual, highly customized web application. Application vulnerabilities maybe subtle and may take
substantial research to detect and deploy.

## Infrastructure profiling

### Footprinting and Scanning: Defining Scope

#### tools used to perform:

* Internet registrar research
* DNS interrogation
* General organizational research

#### basic Infrastructure reconnaissance

* Server discovery (ping sweeps)
* Network service identification (port scanning)
```
netcat utility: https://nmap.org/download.html
ex: D:\>ncat -nvv 192.168.234.34 80
```

#### Advanced HTTP Fingerprinting

* Unexpected HTTP methods
Notice how even though we send the same invalid request, each server reacts differently.
* tools:
nmap: scan os, ports

## Application profiling
* Manual inspection
* Search tools
* Automated crawling
* Common web application profiles

### Manual Inspection
* Document application: pagename, full path of the page, authentication, ssl, get/post arguments, comments
* some other information:
```
statically and dynamically generated pages
directory struture
common file extensions
common files
helper files
java classes and applets
flash and silverlight objects
html sourcecode
forms
Query string and parameters
common cookies
backend access points
```

### Search tools for profiling
* google

### Automated crawling approaches
```
Maltego: https://www.paterva.com/web7/downloads.php (community version)
Wget: (www.gnu.org/software/wget/wget.html)- command line tools
Burp Suite Spider
Teleport Pro : (www.tenmax.com/teleport/pro/home.htm)

```

### Common Web Application Profiles

* Oracle Application Server
```
ex:
http://www.site.com/cs/Lookup/Main.show?id=4592
```

* BroadVision
```
ex:
http://www.site.com/bvsn/bvcom/ep/
programView.(2)do?(3)pageTypeId=8155&programPage=/jsp/www/content/
generalContentBody.jsp&programId=8287&channelId=-8246&(1)BV_
SessionID=NNNN1053790113.1124917482NNNN&BV_
EngineID=cccdaddehfhhlejcefecefedghhdfjl.0
```
* PeopleSoft

```
http://www.site.com/psp/hrprd/(3)EMPLOYEE/HRMS/c/
ROLE_APPLICANT.ER_APPLICANT_HOME(1).GBL?(2)NAVSTACK=Clear
```

* Lotus Domino

```
http://www.site.com/realtor(1).nsf/pages/MeetingsSpeakers(2)?OpenDocument
```

* Web Sphere

```
http://www.site.com/webapp/commerce/command/(1)ExecMacro/site/macros/proddisp.(2)d2w/(3)report?prrfnbr=3928&prmenbr=991&CATE=&grupo=
```
