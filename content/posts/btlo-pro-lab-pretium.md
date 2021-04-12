---
title: BTLO Pro Lab - Pretium
subtitle: Investigating a successful Business Email Compromise
category:
  - Security Blue Team & BTLO
  - Networking
author: Danny Child
date: 2021-04-12T21:30:00.000Z
featureImage: /uploads/n1wgrzgvhv9njoz1rx8j.png
---
# **Lab Preface, Takeaways**

In Pretium, the goal is to find out how a phishing email led to a malicious actor exfiltrating data from a compromised workstation. One responsibility of a SOC employee is investigating fraudulent attempts that are sent via email, ranging from false financial claims, gathering data by impersonation, even executing malware unintentionally. This scenario includes recorded network traffic presented in a PCAP file, and a handoff note from the SOC team including the description of a suspicious email that a company employee interacted with.

To prevent this type of scenario, provide regular security awareness training and email phishing training to all employees. Also add security at the operating system and network level, thereby preventing malicious code from running and communicating to malicious hosts.

# **Questions and Answers**

### **What is the full filename of the initial payload file?**

Opening the PCAP file in Wireshark shows all communication between the compromised host and other systems. The email description specifies that a URL is included, so HTTP traffic to the malicious host should be anticipated if the ULR was interacted with. After filtering for HTTP traffic, the Info column shows a short summary of traffic being requested and sent. Packet number 4502 contains the answer. 

Answer: INVOICE_2021973.pdf.bat

### **What is the name of the module used to serve the malicious payload?**

As an optional field, software and client modules can identify themselves with a User-Agent field so endpoint communication can anticipate how to present data. By looking at the stream where the malicious payload was downloaded, the following HTTP packet contains the Server field, showing the module presenting the data. Packet number 4509 contains the answer.

Answer: SimpleHTTPServer

### **From observing the traffic, can you find out what is the attacker machine IP now?**

The IP address where the malware was downloaded from is also the command-and-control server. This is observed as much unanticipated communication occurs between this IP address and the compromised host. This can be found in the URL that the malware was downloaded from, or in the packet columns source/destination fields.

Answer: 192.168.1.9

### **Now that you know the payload name and the module used to deliver the malicious files, what is the URL that was embedded in the malicious email?**

Revisiting the original request to download the payload, all information can be gathered from individual fields, or be found complete in the Packet Details window of Wireshark. Packet number 4509 contains the answer.

Answer: http://192.168.1.9:443/INVOICE_2021973.pdf.bat

### **Find the PowerShell launcher string (you don’t need to include the base64 encoded script)**

The Packet Bytes section in Wireshark shows the text and hexadecimal stream for each packet. The packet where the payload is downloaded contains the PowerShell code. The answer is the text before the base64 encoded text.

Answer: powershell -noP -sta -w 1 -enc

### **What is the default user agent being used for communications?**

The PowerShell payload must be decoded form base64. After cleaning up the PowerShell code, the user agent is clearly visible as a hardcoded value.

Answer: Mozilla/5.0

### **You are seeing a lot of HTTP traffic, what is the name of a process where malware communicates with C2 server asking for instructions at set time intervals?**

A quick online search for “C2 communications” shows that malware will call out to a C2 server to make the recipient aware it is still active or wait for additional actions based on specific triggers.

Answer: Beaconing

### **What is the URI containing ‘login’ that the victim machine is communicating to?**

To find all URIs containing ‘login’, use the hotkey “ctrl” and “f” to use the display filter to show only packets containing the word “login”.  This can also be applied specifically to the URI field. The first occurrence is in packet 4947.

Answer: http://192.168.1.9:443/login/process.php

### **Can you name the post-exploitation framework used for C2 communication now to our victim machine?**

Exploitation frameworks often have unique indicators in their programming. Each discovered .php file can be searched online to find blogs that feature this framework. [This framework](https://github.com/EmpireProject/Empire) utilizes PowerShell and Python to deploy malicious code while evading network detection.

Answer: Empire

### **Using some Blue Team Magic, can detect data exfiltration and find out what have been exfiltrated? Provide the decoded password.**

Ping requests are being generated with varying responses. The final two responses are equals signs, which indicates that the ping responses are actually sending data encoded in base64. These characters can be extracted with tshark. After converting the output to ASCII and base64, the decoded text is revealed.

Answer: Y0uthinky0ucAnc4tchm3$$

### **What is the account’s username? (Include $ at the beginning)**

This is also found from the output of the previous question.

Answer: $sec-account