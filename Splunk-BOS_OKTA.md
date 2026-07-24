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


  
