# Splunk Boss of the SOC: OKTA 
### Skills: Splunk, IAM, OKTA, Okta’s Privileged Access Management solution, Advanced Server Access (ASA), Log Analysis
#### In this partner experience, you’re assuming the identity of a SOC Analyst for Coffeecase, one of Okta’s newest customers. Coffeecase is a 10-person, entirely-remote company that curates custom, subscription shipments of gourmet coffee to customers around the US. They are running Okta’s latest cloud-native, workforce identity solution: Okta Identity Engine, as well as Okta’s Privileged Access Management solution, Advanced Server Access (ASA). All of the System Logs from these two solutions are ingested in Splunk Enterprise.
### 1 Question:
How many distinct users are found in the data?
Answer guidance: Use only the username, not the domain

Answer:   index = * userName= *.biz
This will return the logs with users that have a .biz email. Our Company's emails are from coffeecase.biz
#### 10
### 2 Question:
Which user locks themselves out the most?

Answer: Spl = index=* this will show all logs.
on the left-hand side select status and then select locked out:
<img width="1131" height="577" alt="image" src="https://github.com/user-attachments/assets/5fa5c046-d4fe-43fc-8cd6-1ecc7f8da6ae" />

Next select user, this will show the counts of the users: 
<img width="1122" height="447" alt="image" src="https://github.com/user-attachments/assets/0ab03da3-960f-4e45-9d4e-89c4109b85a8" />

Bridget will have the highest count. Click " Show as Raw text on the logs, you will see: 
{"id": "00u46jxjdxnx5KrJd0x7", "status": "LOCKED_OUT", "created": "2022-06-01T17:22:52.000Z", "activated": "2022-06-01T17:22:52.000Z", "statusChanged": "2022-07-28T20:41:28.000Z", "lastLogin": "2022-07-28T20:32:20.000Z", "lastUpdated": "2022-07-28T20:41:28.000Z", "passwordChanged": "2022-07-28T19:17:19.000Z", "type": {"id": "oty46f5350PwlkHb20x7"}, "profile": {"firstName": "Bridget", "lastName": "Sive", "mobilePhone": null, "secondEmail": null, "login": "bridget@coffeecase.biz", "email": "bridget@coffeecase.biz"}, "credentials": {"password": {}, "recovery_question": {"question": "What is the food you least liked as a child?"}, "provider": {"type": "OKTA", "name": "OKTA"}}}

Focus on First Name and Last Name:
#### Bridget Sive will be your answer.

### Question 3:
What is the latitude and longitude of the potential adversary located in India?
Answer guidance: Use this format but substitute the actual numbers: 18°32’45”N,71°39’40”E. You may have to Google how to make a degree symbol on your keyboard!

Answer: This question can be answered by going to the dashboard. At the top you will see OKTA example dashboards -> Okta Identity Cloud Overview:
<img width="622" height="360" alt="image" src="https://github.com/user-attachments/assets/981949e8-45b6-40a7-89a7-35ea3f18d84a" />

You will see a chart labeled " Geographic Login Successes and Failures"

Find India and view the longitude and latitude.
#### 18°36’57”N,73°43’42”E



### Question 4:
How many different applications do Coffeecase employees use Okta SSO to access (with the exclusion of any “Okta” apps)?
Answer: Select OKTA stats, Change the time and the # to show:
The logs show 13 apps so, set it to 20. 
<img width="1857" height="671" alt="image" src="https://github.com/user-attachments/assets/2371b05f-83e7-4379-b0a9-a53ada52fee1" />

I exported and counted all apps that were not okta.
#### 6

### Question 5:


SPL = index= * user="luciana@coffeecase.biz" SSO
This will show us all logs with luciana that has SSO in it. The most recent long will be first. After clicking the first log, view the raw text, you will see: {"actor": {"id": "00u4bvrsjigCcoLt20x7", "type": "User", "alternateId": "luciana@coffeecase.biz", "displayName": "Luciana Regla", "detailEntry": null}, "client": {"userAgent": {"rawUserAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36", "os": "Mac OS X", "browser": "CHROME"}, "zone": "null", "device": "Computer", "id": null, "ipAddress": "138.88.55.78", "geographicalContext": {"city": "Laurel", "state": "Maryland", "country": "United States", "postalCode": "20723", "geolocation": {"lat": 39.1181, "lon": -76.8396}}}, "device": {"id": "guo4e9s4nnbtMEHRy0x7", "name": "MacBookPro16,2", "os_platform": "OSX", "os_version": "12.5.0", "managed": false, "registered": true, "device_integrator": "{\"WSC\":{},\"CROWDSTRIKE\":{}}", "disk_encryption_type": "ALL_INTERNAL_VOLUMES", "screen_lock_type": "BIOMETRIC", "jailbreak": null, "secure_hardware_present": true}, "authenticationContext": {"authenticationProvider": null, "credentialProvider": null, "credentialType": null, "issuer": null, "interface": null, "authenticationStep": 0, "externalSessionId": "idxZNHSay7RQdyvMehJe8FT2g"}, "displayMessage": "User single sign on to app", "eventType": "user.authentication.sso", "outcome": {"result": "SUCCESS", "reason": null}, "published": "2022-07-28T19:56:52.862Z", "securityContext": {"asNumber": 701, "asOrg": "verizon", "isp": "verizon", "domain": "ba-dsg.net", "isProxy": false}, "severity": "INFO", "debugContext": {"debugData": {"audience": "google.com", "behaviors": "{New Geo-Location=NEGATIVE, New Device=NEGATIVE, New IP=NEGATIVE, New State=NEGATIVE, New Country=NEGATIVE, Velocity=NEGATIVE, New City=NEGATIVE}", "subject": "luciana@coffeecase.biz", "signOnMode": "SAML 2.0", "authenticationClassRef": "urn:oasis:names:tc:SAML:2.0:ac:classes:Password", "authTime": "2022-07-28T19:56:52.258Z", "requestUri": "/login/token/redirect", "issuer": "google.com/a/coffeecase.biz", "url": "/login/token/redirect?stateToken=02.id.MwmzJt_2erQ99a6knyJxZZjzn9UuXikuV35aYauD", "initiationType": "IDP_INITIATED", "requestId": "YuLqBN1IV7Ry6aQXwSUPhAAAArU", "dtHash": "182a8f29973dc2bf53f8a6ab40d1212716e81c3e422432ed9c977668527e4b42", "expiryTime": "2022-07-28T20:01:52.855Z", "risk": "{level=LOW}", "issuedAt": "2022-07-28T19:56:52.855Z", "threatSuspected": "false", "jti": "id3869677638312502362968841"}}, "legacyEventType": "app.auth.sso", "transaction": {"type": "WEB", "id": "YuLqBN1IV7Ry6aQXwSUPhAAAArU", "detail": {}}, "uuid": "6cf82261-0eaf-11ed-a71c-09a90f974cd2", "version": "0", "request": {"ipChain": [{"ip": "138.88.55.78", "geographicalContext": {"city": "Laurel", "state": "Maryland", "country": "United States", "postalCode": "20723", "geolocation": {"lat": 39.1181, "lon": -76.8396}}, "version": "V4", "source": null}]}, "target": [{"id": "0oa4c11huqM8PmtE10x7", "type": "AppInstance", "alternateId": "Google Workspace", "displayName": "Google Workspace", "detailEntry": {"signOnModeType": "SAML_2_0"}}, {"id": "0ua4dlla0l089VyuF0x7", "type": "AppUser", "alternateId": "luciana@coffeecase.biz", "displayName": "Luciana Regla", "detailEntry": null}]}

#### Focus on the displayName": "Google Workspace

### Question 6:
Which Coffeecase employee uses Google Authenticator?
Answer guidance: Provide first and last name.

SPL = index= * Google Authenticator
On the first log, show raw text and you will see: displayName": "Max Quim

#### Max Quim
