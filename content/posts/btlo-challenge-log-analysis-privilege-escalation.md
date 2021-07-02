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

A server with sensitive data was accessed by an attacker and the files were posted on an underground forum. Bash history logs are presented for analysis, with only 63 commands recorded.
While this log does not show the entry point of the attack, enough data is present to show actions of reconnaissance, persistence, defense evasion, exploitation, and collection of private data.

# **Questions and Answers (Coming Soon)**

### **What user (other than ‘root’) is present on the server?**

### **What script did the attacker try to download to the server?**

### **What packet analyzer tool did the attacker try to use?**

### **What file extension did the attacker use to bypass the file upload filter implemented by the developer?**

### **Based on the commands run by the attacker before removing the php shell, what misconfiguration was exploited in the ‘python’ binary to gain root-level access? 1- Reverse Shell ; 2- File Upload ; 3- File Write ; 4- SUID ; 5- Library load.**