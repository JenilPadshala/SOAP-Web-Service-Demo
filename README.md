# SOAP-Web-Service-Demo
A simple web app to demonstrate SOAP web service.

## Build an executable JAR
Since this is a maven project, enter the following command in the terminal to generate a JAR file:
<pre><code>
  ./mvnw clean package
  java -jar target/soap-web-service-0.0.1-SNAPSHOT.jar
</code></pre>

## Testing the application
Create a file called ```request.xml``` and add the following SOAP request:
```xml
  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
				  xmlns:gs="http://spring.io/guides/gs-producing-web-service">
   <soapenv:Header/>
   <soapenv:Body>
      <gs:getCountryRequest>
         <gs:name>Spain</gs:name>
      </gs:getCountryRequest>
   </soapenv:Body>
</soapenv:Envelope>
```
Next, use the curl command:
<pre><code>
  curl --header "content-type: text/xml" -d @request.xml http://localhost:8080/ws
</code></pre>

The result should be:
```xml
<?xml version="1.0"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
  <SOAP-ENV:Header/>
  <SOAP-ENV:Body>
    <ns2:getCountryResponse xmlns:ns2="http://spring.io/guides/gs-producing-web-service">
      <ns2:country>
        <ns2:name>Spain</ns2:name>
        <ns2:population>46704314</ns2:population>
        <ns2:capital>Madrid</ns2:capital>
        <ns2:currency>EUR</ns2:currency>
      </ns2:country>
    </ns2:getCountryResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
