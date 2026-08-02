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
<img width="1122" height="447" alt="image" src="https://github.com/user-attachments/assets/0d5c716f-db83-4072-a895-b2c2b884cd88" />
Focus on First Name and Last Name:
Bridget Sive will be your answer.


  
