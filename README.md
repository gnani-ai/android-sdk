# Android Library for gnani-speech to text






# Steps

Clone the given repo 

 speechtotext.aar file (binary) is our android library to record and connect to our backend service

You can follow below link to learn how to  add AAR file to your project

[http://docs.onemobilesdk.aol.com/android-ad-sdk/adding-aar-files.html](http://docs.onemobilesdk.aol.com/android-ad-sdk/adding-aar-files.html)


# Add certificate for TLS :

1) Add a new android resource raw directory inside res directory
2) Copy and paste the "cert.pem" file inside raw directory

# Add Netwrok Security for TLS :

1) Add a new android resource xml directory inside res directory
2) Add a new xml resource file inside xml directory and name it as "network_security_config.xml"
3) Copy and paste the following code in "network_security_config.xml"

<network-security-config>
    <domain-config cleartextTrafficPermitted="false">
        <domain includeSubdomains="true">gnani.ai</domain>
        <trust-anchors>
            <certificates src="@raw/cert"/>
        </trust-anchors>
    </domain-config>
</network-security-config>

# Enable TLS in Manifest :
1) Copy and paste the following code in application tag inside "AndroidManifest.xml"

android:networkSecurityConfig="@xml/network_security_config"


# Credentials and Access

You have to declare our service in the app where you are using the aar file
```xml
<service android:name="com.gnani.speechtotext.SpeechService"/>
```
1) Add a new android resource xml directory inside res directory
2) Add a new xml resource file inside xml directory and name it as "network_security_config.xml"
3) Copy and paste the following code in "network_security_config.xml"
```xml
<network-security-config>
    <domain-config cleartextTrafficPermitted="false">
        <domain includeSubdomains="true">gnani.ai</domain>
        <trust-anchors>
            <certificates src="@raw/cert"/>
        </trust-anchors>
    </domain-config>
</network-security-config>


```
## import Recorder and SpeechService from aar library
1.  Implement these two intefaces to your activity or fragment or service

SpeechService.Listener, Recorder.RecordingStatusListener

2.  Add the following code in onCreate method



Recorder.bind(yourContext);

3.  Add the following code in clicklisetner of view with which you want to start the recording

Recorder.onRecord(languageCode);

4.  Recording will be stopeed in two cases :

a) If you click same view again b) after 15 seconds

5.  Add the following code in onDestroy method

Recorder.unbind(yourContext);



