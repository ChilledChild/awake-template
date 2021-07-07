---
title: BTLO Challenge - Memory Analysis - Ransomware
subtitle: Identifying Ransomware from a memory dump
category:
  - Digital Forensics
  - Security Blue Team & BTLO
author: Danny Child
date: 2021-07-02T14:30:19.272Z
featureImage: /uploads/500_x_500_logo_white_border.png
---
# **Preface, Takeaways**

In [this challenge](https://blueteamlabs.online/home/challenge/1), an executive states he can’t access any files on his computer and keeps receiving a pop-up stating that his files have been encrypted. After the computer is removed from the network, a memory dump is generated and provided for forensic analysis. This scenario suggests using [Volatility 2](https://github.com/volatilityfoundation/volatility) to identify indicators of compromise.

Wiping a device when malware is found is not always an option, especially when it could contain business critical files of a company executive. Disconnecting the device from the network is an option, so long as the malware does not negatively impact the device on loosing a network connection. Identifying the malware family can determine the next steps to remediation and preventing further impact.

# **Questions and Answers**

### **Run “vol.py -f infected.vmem --profile=Win7SP1x86 psscan” that will list all processes. What is the name of the suspicious process?**

Psscan is a module used by Volatility to search for all running processes. Filtering for suspicious processes by hand is usually slow and liable to missing intentionally hidden data, but this is a short list. The earliest time any process starts appears around 18:01:10, and other processes around 18:23:00. Knowing that ransomware can encrypt data on a computer, one of the process names appears potentially related.

Answer: @WanaDecryptor

![](/uploads/screenshot-2021-07-01-222307.jpg)

### **What is the parent process ID for the suspicious process?**

From the previous command, the column shows the assigned process ID.

Answer: 2732

### **What is the initial malicious executable that created this process?**

To the right of the process ID is the parent process ID (PPID). The PPID is the PID of the file that generated this process. Searching for this number in the previous output shows the relation between the previously discovered process and this file. The PID that should be searched is 2732.

Answer: or4qtckT.exe

![](/uploads/screenshot-2021-07-01-222228.jpg)

### **If you drill down on the suspicious PID (vol.py -f infected.vmem --profile=Win7SP1x86 psscan | grep (PIDhere)), find the process used to delete files.**

The previously found file appears to be the source of the malicious process and is controlling the other file listed from this command. 

Answer: taskdl.exe

### **Find the path where the malicious file was first executed.**

Now that the source of the ransomware has been found, its location path can be included in a final report presented by the security incident response team. Filescan is a module used by Volatility that can show the location of a file. By grepping the output for the malicious executable, the path, permissions, and memory offset are listed.

Answer: C\Users\hacker\Desktop\or4qtckT.exe

![](/uploads/screenshot-2021-07-01-224816.jpg)

### **Can you identify what ransomware it is? (Do your research!)**

Searching online for the process name from questions 1 and 4 shows multiple reputable sites explaining the history and details of this specific ransomware. This ransomware was especially prevalent in 2017 and stopped by a single domain purchase.

Answer: [Wannacry](https://attack.mitre.org/software/S0366/)

### **What is the filename for the file with the ransomware public key that was used to encrypt the private key? (.eky extension)**

Using the same method as finding the malicious file path, searching for “.eky” shows the file used as the public key.

Answer: 00000000.eky

![](/uploads/screenshot-2021-07-01-232804.jpg)