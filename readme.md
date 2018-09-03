# HTTPS Service with Basic Authorization

To build a https service in mule we need the following steps.

## Requirement
   1. Generating a self signed certificate
   2. HTTPS Listener with TLS Configuration
   3. Configuring Spring Authentication Manager for basic auth username and password
   
## Generating Certificate

   Generate a keystore if you don’t have one already.
   The below command creates a file named keystore.jks. Before proceeding, verify that this file exists and appears in the folder    src/main/resources.

```
keytool -genkeypair -keystore keystore.jks   -dname "CN=localhost, OU=Unknown, O=Unknown, L=Unknown, ST=Unknown, C=Unknown"  
-keypass password  -storepass password  -keyalg RSA  -sigalg SHA1withRSA  -keysize 2048  -alias mule  -ext SAN=DNS:localhost,IP:127.0.0.1 -validity 9999
```

## HTTPS Listener with TLS Configuration

   1. Keep the jks file under src/main/resources
   2. Configure an HTTPS connector inside your Mule configuration:
      
      ![ScreenShot](https://raw.githubusercontent.com/indiramallick1988/Demo2/master/HTTPS/HTTPS1.png)


## Configuring Username and Password
   
   1. Configure Spring Authentication Manager for basic authorization username and password inside your Mule configuration:
      
      ![ScreenShot](https://raw.githubusercontent.com/indiramallick1988/Demo2/master/HTTPS/Auth.PNG)
      
## Testing the application
   This application is deployed in Anypoint Cloud environment. 
   To Test the application click the below. It will ask the username and password which is as below.
   
   URL: https://hello-https.us-e2.cloudhub.io/test
   USERNAME: test
   PASSWORD: test123
   
