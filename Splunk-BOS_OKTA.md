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


  
