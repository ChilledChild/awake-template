---
title: BTLO Pro Lab - Pretium
subtitle: Investigating a successful Business Email Compromise
category:
  - Security Blue Team & BTLO
author: Danny Child
date: 2021-03-30T07:00:00.000Z
featureImage: /uploads/euidzkbwsam27og.jpg
---
# **Lab Preface, Takeaways**

In Pretium, the goal is to find out how a phishing email led to a malicious actor exfiltrating data from a compromised workstation. One responsibility of a SOC employee is investigating fraudulent attempts that are sent via email, ranging from false financial claims, gathering data by impersonation, even executing malware unintentionally. This scenario includes recorded network traffic presented in a PCAP file, and a handoff note from the SOC team including the description of a suspicious email that a company employee interacted with.

To prevent this type of scenario, provide regular security awareness training and email phishing training to all employees. Also add security at the operating system and network level, thereby preventing malicious code from running and communicating to malicious hosts.

# **Questions and Answers (Coming Soon)**

### **What is the full filename of the initial payload file?**

### **What is the name of the module used to serve the malicious payload?**

### **From observing the traffic, can you find out what is the attacker machine IP now?**

### **Now that you know the payload name and the module used to deliver the malicious files, what is the URL that was embedded in the malicious email?**

### **Find the PowerShell launcher string (you don’t need to include the base64 encoded script)**

### **What is the default user agent being used for communications?**

### **You are seeing a lot of HTTP traffic, what is the name of a process where malware communicates with C2 server asking for instructions at set time intervals?**

### **What is the URI containing ‘login’ that the victim machine is communicating to?**

### **Can you name the post-exploitation framework used for C2 communication now to our victim machine?**

### **Using some Blue Team Magic, can detect data exfiltration and find out what have been exfiltrated? Provide the decoded password.**

### **What is the account’s username? (Include $ at the beginning)**