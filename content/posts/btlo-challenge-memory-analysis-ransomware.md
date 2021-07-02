---
title: BTLO Challenge - Memory Analysis - Ransomware
subtitle: Identifying Ransomware from a memory dump
category:
  - Digital Forensics
  - Security Blue Team & BTLO
author: Danny Child
date: 2021-07-02T05:25:19.272Z
featureImage: /uploads/500_x_500_logo_white_border.png
---
# **Preface, Takeaways**

In [this challenge](https://blueteamlabs.online/home/challenge/1), an executive states he can’t access any files on his computer and keeps receiving a pop-up stating that his files have been encrypted. After the computer is removed from the network, a memory dump is generated and provided for forensic analysis. This scenario suggests using [Volatility 2](https://github.com/volatilityfoundation/volatility) to identify indicators of compromise.

Wiping a device when malware is found is not always an option, especially when it could contain business critical files of a company executive. Disconnecting the device from the network is an option, so long as the malware does not negatively impact the device on loosing a network connection. Identifying the malware family can determine the next steps to remediation and preventing further impact.

# **Questions and Answers (Coming Soon)**

### **Run “vol.py -f infected.vmem --profile=Win7SP1x86 psscan” that will list all processes. What is the name of the suspicious process?**

### **What is the parent process ID for the suspicious process?**

### **What is the initial malicious executable that created this process?**

### **If you drill down on the suspicious PID (vol.py -f infected.vmem --profile=Win7SP1x86 psscan | grep (PIDhere)), find the process used to delete files.**

### **Find the path where the malicious file was first executed.**

### **Can you identify what ransomware it is? (Do your research!)**

### **What is the filename for the file with the ransomware public key that was used to encrypt the private key? (.eky extension)**