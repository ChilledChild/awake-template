---
title: BTLO Pro Lab - Total Recall
subtitle: Remember the What and How
category:
  - Digital Forensics
  - Security Blue Team & BTLO
author: Danny Child
date: 2021-12-20T17:30:00.000Z
featureImage: /uploads/cmtweq6b8hpfptnlnqzq.png
---
# **Challenge Preface, Takeaways**

In [Total Recall](https://blueteamlabs.online/home/investigation/11), the goal is to discover any potential malicious activity on a computer from an employee who was let go due to company downsizing. Suspicious activity was observed on this device prior to their confirmed termination. Host event logs are presented in [Redline](https://www.fireeye.com/services/freeware/redline.html), a Windows log analysis tool created by [FireEye](https://www.fireeye.com/).

The offboarding process of an employee includes revoking all access to accounts, applications, and physical mediums. Failing to fully execute this process completely can lead to the same result as giving a malicious actor the keys to the kingdom.

# **Questions and Answers**

### **The user tried to download an .exe file to the system but cancelled it. What was the filename?**

On the Desktop, open the AnalyzeMe file in the Investigations folder. After opening redline and navigating to File Download History tab. Redline identified which files have been recently attempted to download on the host. Filtering the File Name column with “.exe” provides a list of 10 executables that were downloaded, or attempted. The Bytes Downloaded column shows that one of these executables have a total of 0 bytes downloaded compared to the file size of 72,072 bytes, and the state column says the file was cancelled.

Answer: OpenVPN (1).exe

![List of executables downloaded by the malicious insider. Open VPN is listed in the downloads.](/uploads/screenshot-2021-12-19-192512.jpg)

### **What is the IP and port used to download other files to the system?**

From the previous search, the Source URL column shows the IP address and the port that was used.

Answer: 10.201.1.105:8080

### **Can you find two scheduled tasks created by the malicious insider? (alphabetical order)**

Navigating to the Tasks tab in Redline shows each task on the host. Filtering the Creator column for “hacker” shows each task that was created by the insider’s account.

Answer: DailyTask, OnIdleTask

![List of two tasks created by the malicious insider](/uploads/screenshot-2021-12-19-194608.jpg)

### **What is the time creation for these scheduled tasks? (alphabetical order)**

From the previous search, the Created column contains the creation timestamps for each scheduled task.

Answer: 2021-03-03 21:41:23Z, 2021-03-03 21:43:08Z

### **The task will grab the file from the attacker’s machine. What file is scheduled to run on the tasks? Include the full path to the file within the URL**

Navigating to the Actions tab and expanding the Executable Arguments column shows each action that tasks will perform and their location. A suspicious executable argument that uses PowerShell in non-interactive mode and downloading an executable can be immediately observed on opening this tab. The string inside the variable “downloadstring” contains the answer.

Answer: http://10.201.1.105:8080/catchmeifyoucan.exe

![Logs containing the url of a malicious executable that was downloaded.](/uploads/screenshot-2021-12-19-195502.jpg)

### **What user accounts were created by the insider? (alphabetical order)**

Navigating to the Users tab in Redline shows each user that was created on the host. The attacker’s account has an older creation timestamp while all other account that are not default to Windows have a newer creation timestamp. Additionally, navigating to the Event Logs tab and filtering the Message column for “A user account was created” shows 6 unique events associated. One of these belongs to the “hacker” account, and the other account belong to the insider.

Answer: Alice, Bob, Carlos, Jason, Smith

![List of user accounts created by the malicious insider.](/uploads/screenshot-2021-12-19-193323.jpg)

### **What service was enabled by the attacker between 7-8 PM on 03/03/2021 which involves the netsh command and exception on the firewall? Provide the protocol and execution PID**

Navigating to the Event Logs tab in Redline shows all recorded events on the host. Applying the timestamp in the Generated column, and filtering the Message tab for the word “firewall” shows events where the firewall was being modified for a new exception. Hovering over the Message field or selecting the “Show Details” text in the bottom right will show what was configured.

Answer: RDP, 1028

### **An attempt was made to reset a newly-created user's password some time after 9 PM on 03/03/2021. Find the Execution PID and Execution Thread ID**

Filtering the timestamps from 8:30 PM to 10:00 PM on 03/03/2021, the message states that a user account's password was attempted to be reset. Selecting the “Show Details” text in the bottom right will show what was configured.

Answer: 472, 2872

### **The insider has likely utilized ATT&CK ID T1547.001 to obtain persistence. Find the malicious registry entry and submit the Registry Key Value and modified date**

Reviewing <https://attack.mitre.org/techniques/T1547/001/> shows that there are registry keys that can be modified to execute programs on startup. After reviewing the listed registry paths, “HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Userinit” contained a custom registry key that appears malicious.

Answer: Userinit.exe, evil.exe, 2021-03-07 11:15:29Z

![List of two executables that run regularly, set up by the malicious insider. ](/uploads/screenshot-2021-12-19-200114.jpg)

### **Another common persistence method is using Windows Services. Identify any suspicious running services**

Navigating to the Windows Service tab and filtering the Path Signature Description for “The file is not signed” shows a single service that leads to a [Meterpreter](https://www.offensive-security.com/metasploit-unleashed/about-meterpreter/) instance. Also found in the registry is a list of entries that point to the same Meterpreter service.

Answer: C:\Users\hacker\AppData\Local\Temp\OHpObWvB\metsvc.exe, 31337

![List of suspicious services that the malicious actor set up](/uploads/screenshot-2021-12-19-200323.jpg)