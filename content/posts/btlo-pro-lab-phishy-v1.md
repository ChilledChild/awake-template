---
title: BTLO Pro Lab - Phishy v1
subtitle: A small phish in a big pond
category:
  - Security Blue Team & BTLO
author: Danny Child
date: 2021-04-29T01:30:00.000Z
featureImage: /uploads/5ke2npvursjma2k1on5g.png
---
# **Lab Preface, Takeaways**

In [Phishy v1](https://blueteamlabs.online/home/investigation/4), a malicious phishing link is presented, and threat intelligence must be performed to identify malicious site indicators. Actions taken in this lab is part of the standard responsibilities of a SOC analyst when investigating a malicious website. The malicious site can be analyzed live from the browser, or statically from the original phishing kit. Had the malicious actor fixed the variable names and not included the phishing kit package on the site, successful phishing attempts would have significantly increased.

While not available in this lab, [Burp Suite](https://portswigger.net/burp) is a web toolkit for analyzing application traffic and sending modified traffic. This tool can be used to discover more about a public facing application and for offensive security purposes. As part of a SOC analyst's toolkit, this would assist with analysis outside of using the native web browser while utilizing additional community tools.

# **Questions and Answers (Coming Soon)**

### **The HTML page used on securedocument.net is a decoy. Where was this webpage mirrored from, and what tool was used? (Use the first part of the tool name only)**

### **What is the full URL of the background image which is on the phishing landing page?**

### **What is the name of the php page which will process the stolen credentials?**

### **What is the SHA256 of the phishing kit in ZIP format? (Provide the last 6 characters)**

### **What email address is setup to receive the phishing credential logs?**

### **What is the function called to produce the PHP variable which appears in the index1.html URL?**

### **What is the domain of the website which should appear once credentials are entered?**

### **There is an error in this phishing kit. What variable name is wrong causing the phishing site to break? (Enter any of 4 potential answers)**