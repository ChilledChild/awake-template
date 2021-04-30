---
title: BTLO Challenge - Malicious PowerShell Analysis
subtitle: Critical malware requires critical response
category:
  - Security Blue Team & BTLO
  - Programming
author: Danny Child
date: 2021-04-30T06:30:00.000Z
featureImage: /uploads/500_x_500_logo_white_border.png
---
# **Challenge Preface, Takeaways**

In [Malicious PowerShell Analysis](https://blueteamlabs.online/home/challenge/7) a malicious PowerShell script that was executed from an email attachment is provided for analysis. As an incident responder, decode the PowerShell script and identify the type of malware responsible.

Both public services and enterprise companies have access to email filtering services. Email content and attachments can be reviewed and compared to known malicious indicators before the email arrives in an inbox. Additionally, email can be assigned as spam by configured filtering rules so that caution is advised. If a file appears suspicious, it can be analyzed by [VirusTotal](https://www.virustotal.com/gui/) for malicious indicators.

# **Questions and Answers**

The parameter `-ENCOD` makes all text Base64 encoded, so this will have to be decoded in Base64. After cleaning up the code of extra periods, unnecessary variables, tick marks, and concatenating strings, the code’s intentions become clear. While this can be further simplified, the code below marks where everything needed to solve this challenge can be found. Code related to the decrypted malware can be found [here](https://github.com/ChilledChild/BTLO-Labs-and-Challenges/blob/main/Malicious%20PowerShell%20Analysis/malicious_script.ps1).

### **What security protocol is being used for the communication with a malicious domain?**

Line 5 specifies which security protocol to use. This is used in combination with line 2, where variable mbu links the protocol with ServicePointManager. ServicePointManager is a static class that assists with maintaining connections presented by a URI.

Answer: TLS 1.2

### **What directory does the obfuscated PowerShell create? (Starting from \HOME)**

On line 4, the snippet `(DIr VariabLE:Mku).VaLUe::cREAtedIRECTORy` is utilized. The text that follows is the specified directory to be created. This can be found in lines 4 and 6.

Answer: \HOME\Db_bh30\Yf5be5g

### **What file is being downloaded (full name)?**

Answer: A69S.dll

### **What is used to execute the downloaded file?**

Answer: rundll32

### **What is the domain name of the URI ending in ‘/6F2gd/’**

Answer: wm.mcdevelop.net

### **Based on the analysis of the obfuscated code, what is the name of the malware?**

Answer: emotet