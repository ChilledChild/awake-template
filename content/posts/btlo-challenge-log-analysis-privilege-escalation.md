---
title: BTLO Challenge - Log Analysis - Privilege Escalation
subtitle: Identifying vulnerabilities from basic logs
category:
  - Security Blue Team & BTLO
author: Danny Child
date: 2021-07-02T14:31:16.109Z
featureImage: /uploads/500_x_500_logo_white_border.png
---
# **Preface, Takeaways**

In [this challenge](https://blueteamlabs.online/home/challenge/4), a server with sensitive data was accessed by an attacker and the files were posted on an underground forum. Bash history logs are presented for analysis, with only 63 commands recorded.
While this log does not show the entry point of the attack, enough data is present to show actions of reconnaissance, persistence, defense evasion, exploitation, and collection of private data.

# **Questions and Answers**

### **What user (other than ‘root’) is present on the server?**

Non-system users have a folder created for them under the home directory. Searching for “home” in this log shows that line 21 contains the username from this server.

Answer: daniel

### **What script did the attacker try to download to the server?**

The command wget was used to download a malicious script from a GitHub URL, in line 32.

Answer: linux-exploit-suggester.sh

### **What packet analyzer tool did the attacker try to use?**

Previous knowledge on common packet analyzers helps with finding this answer. Line 41 to line 47 shows that the malicious actor attempted to gather information on the server’s network connections and files generating network activity.

Answer: tcpdump

### **What file extension did the attacker use to bypass the file upload filter implemented by the developer?**

While the upload filter configuration cannot be viewed in this log, various extensions are found in some commands. Line 63 shows that a file in the uploads folder under /var/www/html was removed. This file potentially has data that the upload filter would have otherwise flagged. One security feature of web filters is examining the extension to include or exclude, which this extension was able to bypass.

Answer: .phtml

### **Based on the commands run by the attacker before removing the php shell, what misconfiguration was exploited in the ‘python’ binary to gain root-level access? 1- Reverse Shell ; 2- File Upload ; 3- File Write ; 4- SUID ; 5- Library load.**

Python is directly referenced in lines 26, 27 and 62. Line 27 shows that python was used to spawn a shell in bin/sh/. Line 62 shows that python was used to create a shell. The SUID indicates who has permissions to a file. By creating a shell in that location, root access is granted, allowing the malicious file to be uploaded.

Answer: 4