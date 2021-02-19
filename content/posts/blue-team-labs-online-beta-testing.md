---
title: Blue Team Labs Online Private Beta Testing
subtitle: A quick dive into what is to come
category:
  - Security Blue Team & BTLO
author: Danny Child
date: 2021-02-19T15:30:00.000Z
featureImage: /uploads/btlo_beta_tester.png
---
[Security Blue Team](https://securityblue.team/), founded by Joshua Beaman, is a cyber security training vendor for defensive analysts. With the release of the [Blue Team Level 1](https://securityblue.team/why-btl1/) (BTL1) certification and [6 certificate courses](https://securityblue.team/training/), many students have seen success and growth by exercising practical skills through the provided training. In addition, Security Blue Team is creating their online platform [Blue Team Labs Online](https://blueteamlabs.online/) (BTLO).

As a playground for digital defenders, BTLO is a gamified online platform where defensive security professionals can sharpen their skills through online lab environments. In February 2021, I had the opportunity to be a beta tester for BTLO.

Beta testers have access to one lab and three challenges. The challenges focused on web log analysis, PCAP analysis, and email analysis. The online lab provides a forensics scenario. Each fit into respective categories of Incident Response, Digital Forensics, Security Operations, and “CTF-Like”. Tools are suggested for each challenge, along with a short description on what to expect. All labs and challenges have on average 5 to 7 questions to answer, with varying points awarded per question.

**My First Impression**

Each challenge was made interesting and fun by setting interesting and realistic expectations for each investigation. Red herrings made me try all sorts of IOC discovery techniques, which only added to my relief that an answer could be found. I nearly claimed the title for “first blood” for the email analysis challenge had it not been for an obvious trick.

The Wireshark and WordPress Log challenges were relatively simple, as I was able to focus on identifying an isolated piece of information, so long as I knew how to read the logs. The WordPress log challenge had me focus on identifying unique attacks and tools used, along with correlating significant events to a CVE ID.

While my experience with handling digital forensic cases is only foundational, I found the forensics lab was testing my ability to “connect the dots” by recovering deleted files, utilize inherit exposure, and paint a complete picture of major events. Unlike the previous challenges where a single tool was used, a library of tools that focus on unique elements of digital forensics was needed to complete the lab.

The worldwide leaderboard shows each user’s ranking and earned badges. I was at the top for the first part of day 1, until the investigation lab became accessible and others raced to the top as I took a break.

![BTLO Private Beta Profile of Danny Child](/uploads/blueteamlabs.online_home_user_7-2-.png)

**What is BTLO working on now?**

Being in the beta phase, many aspects of BTLO are developing and will continue to grow once open to the public. Servers will be available in many regions worldwide, additional challenges will be published, and the community will continue to grow with time. An additional three new labs will be added at launch that were not previously available during the beta.

**How does BTLO compare to other online platforms?**

BTLO allows students to improve their already existing knowledge as a defender. Similar to [Hack The Box](https://www.hackthebox.eu/) (HTB), BTLO is designed for those who already have some cyber security defense knowledge. Presented challenges focus on an area of expertise, including digital forensics, or network log analysis. Unlike a typical CTF where a fixed string must be found (like “KEY-ABCD-1234”), BTLO challenges require the student to discover significant events and data related to the investigation to answer specific questions. Like HTB, there is a free tier of BTLO, allowing anyone to get a sample of what BTLO offers.

**What is the difference between a lab and a challenge?**

An investigation lab is hosted by BTLO where investigations are performed in the browser. A challenge is a scenario including files that can be downloaded to your computer. All challenges are available for free, as well as one investigation lab. Additional investigation labs are available to BTLO subscribers.

**How much is it a PRO subscription?**

There are 4 options for subscribing:

* 1 month – £ 18.50 ($ 25.89) 
* 3 months – £ 47 ($ 65.77)
* 6 months – £ 89 ($ 124.55) 
* 1 year – £ 167 ($ 233.70)

There is a lot more to come from BTLO. The launch day is February 26, 2021. With my 12-month pro subscription, I’ll be creating additional writeups for BTLO labs and challenges as they release. Due to BTLO rules, writeups can only be published after a lab has been retired so everyone has a fair chance to the leaderboard. I strongly encourage anyone who is looking to get a career as a SOC analyst, incident responder, digital forensics, or network analyst, get an account on BTLO.