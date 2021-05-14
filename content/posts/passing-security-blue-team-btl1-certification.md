---
title: Passing Security Blue Team BTL1 Certification
subtitle: My experience with a 24-hour practical incident response exam
category:
  - Security Blue Team & BTLO
  - Projects
author: Danny Child
date: 2021-05-14T07:00:00.000Z
featureImage: /uploads/btl1website.png
---
In April 2021, I got news that [I passed the BTL1 exam](https://www.linkedin.com/feed/update/urn:li:activity:6785417984098889728/). This was my first security certification, and practical exam. Waking up to the email notification on April 1 seemed too good to be true. For all the months of studying and 24 hours of anticipation, it was all worth it. I’m happy to have this achievement and share my experience.

# **What Is BTL1?**

[Blue Team Level 1 (BTL1)](https://securityblue.team/why-btl1/) is a practical security certification that covers skills over the following 5 domains: Phishing Analysis, Digital Forensics, Threat Intelligence, SIEM, and Incident Response. The exam for the certification includes 12 hours to investigate an online lab environment, followed by another 12 hours to submit the written report of the investigation.

Actions have already been taken by the malicious actor to compromise a network, and the incident response team provides a summary on what has already been done to contain the incident. My role as the test taker is to gather evidence on all actions taken by each effected employee and the malicious actor, then create a report on the incident.

# **What did I do to pass?**

For being the only person performing the investigation, this is pretty close to the real deal. Having already worked in a SOC role the experience was familiar, except I had total responsibility for how the investigation should be performed. Going into the exam I knew when I should complete each section and felt prepared to use any tools mentioned from the study material.

### **Execute a plan**

I took all 12 hours to gather all my evidence and review any additional details I can provide. I preferred to be confident in my analysis and get everything I could, rather than cherry-pick the necessary parts. If I spent a few minutes on a problem without making any progress, I would record my notes and move on to another IOC. I would take breaks after reaching a stopping point to collect my thoughts and walk myself through potential scenarios. To avoid working to the last second, I planned like I only had 11 hours of lab access. This way I wouldn’t be as pressed for time if a new investigation path was found at an inconvenient time. Having spent most of my energy gathering my findings for 12 hours, I took a 3-hour nap to recharge for the remainder of the written report. Listening to my own needs, I knew that a planned short break would be more effective than an emergency break at an unknown time. 24 hours is plenty of time to finish the exam, I still had time to spare after completing my report.

### **Communicate all findings**

The written portion of the exam plays a large factor on passing or failing. A report should tell events in detail, chronologically, and in context. A pile of information can only be acted on if understood by everyone. Communication and clarity are important skills for everyone, especially when connecting the bridge between people and technology. Any analyst should be able to clearly explain an identified issue and provide next possible steps towards remediation to both technical and non-technical people. If done well, the same sentence that leads towards remediation is understood by both parties.

### **Think from the perspective of the attacker**

Everything that happened in the scenario is repeatable in real life. Between finding obvious IOCs, I found myself asking “how would the attacker get from A to B?” and connecting the dots to each action performed. I don’t claim offensive security as a specialty, though attack methods and vulnerabilities should be standard knowledge for any specialization in IT, especially security. Studying popular attack methods and probable actions from an exposure helps predict the outcome of a successful attack. Some actions are more predictable than others.

### **Know available tools**

The BTL1 study material covers everything needed for the exam. While the entire internet was at my fingertips, the tools in the virtual lab were the most beneficial. I was already familiar with Wireshark and Splunk, but learning Autopsy, Volatility, and Yara made me well equipped for the exam. I could look online for specific commands that I don’t know, because that’s what I can do in a real situation. I don’t have to know each tool perfectly, I just have to know what a tool is capable of. I didn’t use every tool available, only the ones that would help me get questions answered the best way. A significant part of my findings required analyzing IOCs by hand, immersing myself in the investigation came quick.

### **Document everything**

The report is presented in a PDF file. While a malicious file would not be appropriate to attach in this report, screenshots and other identifying data can be presented in the report as evidence. I remember recording a piece of evidence that I though was minor at first, it later became a pivot point for additional analysis. Had I not saved a screenshot of that event, I wouldn’t have scored as well. Not only was I recording malicious actions taken by the attacker, but also poor practices and questionable configurations within the environment.

# **To sum it up**

BTL1 costs £499, which is a fair price considering that two attempts and a personal review are included. Through [over 300 provided lessons](https://securityblue.team/why-btl1/#coursecontent), I became more confident in my analysis skills, introduced to practical methods of digital forensics and other technical skills, and was set up for success. [BTL1 is unique](https://pauljerimy.com/security-certification-roadmap/) for being a reasonably priced practical certification that’s obtainable by those looking to move to cyber security, or those who are in their first years in the field. It's not an easy certification, but it's one worth getting. I recommend this exam to anyone who is looking to level up their role in cyber security.