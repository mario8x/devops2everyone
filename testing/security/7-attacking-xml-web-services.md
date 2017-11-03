# attacking xml web services

* what is a web service ?
is a self-contained software component that performs specific functions and publishes information about its capabilities.

## technologies

* web services definition language (WSDL)
https://www.w3schools.com/xml/xml_wsdl.asp
```
<definitions>

<types>
  data type definitions........
</types>

<message>
  definition of the data being communicated....
</message>

<portType>
  set of operations......
</portType>

<binding>
  protocol and data format specification....
</binding>

</definitions>
```
* Universal Description Discovery, and Integration(UDDI):
https://www.tutorialspoint.com/uddi/uddi_data_model.htm
  * businessEntity
    ```
    <businessEntity businessKey = "uuid:C0E6D5A8-C446-4f01-99DA-70E212685A40"
       operator = "http://www.ibm.com" authorizedName = "John Doe">
       <name>Acme Company</name>
       <description>
          We create cool Web services
       </description>

       <contacts>
          <contact useType = "general info">
             <description>General Information</description>
             <personName>John Doe</personName>
             <phone>(123) 123-1234</phone>
             <email>jdoe@acme.com</email>
          </contact>		
       </contacts>

       <businessServices>
          ...
       </businessServices>
       <identifierBag>
          <keyedReference tModelKey = "UUID:8609C81E-EE1F-4D5A-B202-3EB13AD01823"
             name = "D-U-N-S" value = "123456789" />
       </identifierBag>

       <categoryBag>
          <keyedReference tModelKey = "UUID:C0B9FE13-179F-413D-8A5B-5004DB8E5BB2"
             name = "NAICS" value = "111336" />			
       </categoryBag>		
    </businessEntity>
    ```
    * businessService data structure:
     ```
      <businessService serviceKey = "uuid:D6F1B765-BDB3-4837-828D-8284301E5A2A"
     businessKey = "uuid:C0E6D5A8-C446-4f01-99DA-70E212685A40">
     <name>Hello World Web Service</name>
     <description>A friendly Web service</description>
     <bindingTemplates>
        ...
     </bindingTemplates>
     <categoryBag />
     </businessService>
     ```

    * bindingTemplate Data Structure
      ```
      <bindingTemplate serviceKey = "uuid:D6F1B765-BDB3-4837-828D-8284301E5A2A"
     bindingKey = "uuid:C0E6D5A8-C446-4f01-99DA-70E212685A40">
     <description>Hello World SOAP Binding</description>
     <accessPoint URLType = "http">http://localhost:8080</accessPoint>
     <tModelInstanceDetails>
        <tModelInstanceInfo tModelKey = "uuid:EB1B645F-CF2F-491f-811A-4868705F5904">
           <instanceDetails>
              <overviewDoc>
                 <description>
                    references the description of the WSDL service definition
                 </description>

                 <overviewURL>
                    http://localhost/helloworld.wsdl
                 </overviewURL>
              </overviewDoc>
           </instanceDetails>
        </tModelInstanceInfo>
        </tModelInstanceDetails>
      </bindingTemplate>
      ```
    * tModel data structure
    ```
      <tModel tModelKey = "uuid:xyz987..." operator = "http://www.ibm.com"
     authorizedName = "John Doe">
     <name>HelloWorldInterface Port Type</name>
     <description>
        An interface for a friendly Web service
     </description>

     <overviewDoc>
        <overviewURL>
           http://localhost/helloworld.wsdl
        </overviewURL>
     </overviewDoc>
      </tModel>
    ```
    * publisherAssertion data structure
     ```
     <element name = "publisherAssertion" type = "uddi:publisherAssertion" />
      <complexType name = "publisherAssertion">
         <sequence>
            <element ref = "uddi:fromKey" />
            <element ref = "uddi:toKey" />
            <element ref = "uddi:keyedReference" />
         </sequence>
      </complexType>
     ```

     * DISCO
     ```
     <?xml version="1.0" encoding="utf-8" ?>
     <discovery xmlns:xsd="http://www.w3.org/2001/XMLSchema"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xmlns="http://schemas.xmlsoap.org/disco/">
    <contractRef ref="http://www.contoso.com/Counter.asmx?wsdl"
                docRef="http://www.contoso.com/Counter.asmx"
                xmlns="http://schemas.xmlsoap.org/disco/scl/" />
    <soap address="http://www.contoso.com/Counter.asmx"
        xmlns:q1="http://tempuri.org/"
        binding="q1:CounterSoap"
        xmlns="http://schemas.xmlsoap.org/disco/soap/" />
     </discovery>
     ```
* Simple Object Access Protocol (SOAP)
    ```
     soap message structure:
      SOAP envelop
        SOAP header
          Header block 1
          Header block 2
        SOAP body
          Body sub-element 1
          Body sub-element 2
    ```

## attacking techniques

### WSDL and DISCO disclosure

* disclosure

```
dumping wsdl, and disco information from a remote webservice using ?disco/?wsdl argument
http://www.webservicex.com/globalweather.asmx?WSDL
http://www.webservicex.com/globalweather.asmx?disco
```

* countermeasures
```
Avoid creating the relevant .wsdl, .discomap, .disco, and .xsd files for the service.
If these files are available, they are designed to be published.
```

### input injection
#### sql injection, and external entity injection
* injection
```
sql injection
http://www.unixwiz.net/techtips/sql-injection.html

http://www.webservicex.com/globalweather.asmx
http://www.webservicex.com/globalweather.asmx?op=GetWeather
input value:
' or '1'='1
1' OR 1 LIMIT 1; -- '
it will becom:
SELECT * FROM USERS WHERE USER='' or '1'='1' AND PASS='' or '1'='1';

external entity injection:
XML allows a document or file to be embedded into the original XML document through the use of external entities.
<?xml version="1.0" encoding="UTF-8" standalone="no"?>    <!DOCTYPE foo [<!ENTITY test SYSTEM "http://www.test.com/test.txt"><!ELEMENT foo ANY>]>


the service server then return the following response:
<?xml version="1.0"?>    <!DOCTYPE test [    <!ENTITY test SYSTEM "http://www.test.com/test.txt";>   
<foo>... This is the content from the file test.txt ...</foo>

There are several things can be done by using this technique:
- Read file off the system using relative paths included in the external entity
- Retrieve files from other web server using the SOAP server as the gateway
- Dos the SOAP server by sending malicious filenames
- Use the SOA server to do anonymous port scanning of other systems
```

* countermeasures
```
If you handle untrusted XML input, you should prohibit external entities.
This is best done by specifying a handler for your XML parser that aborts when it encounters external entities.
```

#### xpath injection( the same as sql injection but it is xquery)
```
xpath injection and countermeasures:
https://www.owasp.org/index.php/XPATH_Injection

```

## tools

* WebService Studio: free tool

```
     http://code.msdn.microsoft.com/webservicestudio20/
     http://webservicestudio.codeplex.com.
```

* SoapUI
* WSDigger
* WSFuzzer
`https://sourceforge.net/projects/wsfuzzer/`
* SoapClient.com
