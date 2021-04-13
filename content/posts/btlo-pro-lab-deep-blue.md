---
title: BTLO Pro Lab - Deep Blue
subtitle: Between the Attacker and the Deep Blue C drive
category:
  - Security Blue Team & BTLO
author: Danny Child
date: 2021-04-12T22:00:00.000Z
featureImage: /uploads/25e54a30fb8f836f469ffcf348d0d5759d26e4bd.png
---
# **Lab Preface, Takeaways**

In [Deep Blue](https://blueteamlabs.online/home/investigation/32) the goal is to verify malicious actions that involved a [Meterpreter](https://www.offensive-security.com/metasploit-unleashed/about-meterpreter/) session and internet-facing RDP on a windows workstation. Internet facing communication can be abused if proper authentication and authorization is not established. Security.evtx and System.evtx log exports from the compromised system are presented, with [DeepBlueCLI](https://github.com/sans-blue-team/DeepBlueCLI) as a special threat hunting tool.

# **Questions and Answers (Coming Soon)**

### **Using DeepBlueCLI, investigate the recovered Security log (Security.evtx). Which user account ran GoogleUpdate.exe?**

### **Using DeepBlueCLI investigate the recovered Security.evtx log. At what time is there likely evidence of Meterpreter activity?**

### **Using DeepBlueCLI investigate the recovered System.evtx log. What is the name of the suspicious service created?**

### **Investigate the Security.evtx log in Event Viewer. Process creation is being audited (event ID 4688). Identify the malicious executable downloaded that was used to gain a Meterpreter reverse shell, between 10:30 and 10:50 AM on the 10th of April 2021.**

### **It's also believed that an additional account was created to ensure persistence between 11:25 AM and 11:40 AM on the 10th April 2021. What was the command line used to create this account?**

### **What two local groups was this new account added to?**