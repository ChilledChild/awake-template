---
title: BTLO Challenge - The Planet's Prestige
subtitle: What is a King without a Crown?
category:
  - Security Blue Team & BTLO
author: Danny Child
date: 2021-04-30T17:00:00.000Z
featureImage: /uploads/500_x_500_logo_white_border.png
---
# **Challenge Preface, Takeaways**

In [The Planet's Prestige](https://blueteamlabs.online/home/challenge/10), a hypothetical scenario is presented where a planetary president's daughter has disappeared. Amidst a multi-planet revolution, a ransom note is sent via email with a pricy task request. Clues throughout the email will lead to the rescue of the President's daughter and save countless lives.

This challenge was available during the [beta of BTLO](https://dannychild.com/blue-team-labs-online-beta-testing). Simple tricks and red herrings can be expected from a malicious actor looking to deceive. Diversifying skills in technology brings new ideas and talents in any situation presented.

# **Questions and Answers**

### **What is the email service used by the malicious actor?**

Email headers contain information about the source of the email, and where it has traveled in order to land in your inbox. It is important to note that some headers can be faked if an environment is set correctly. To view the email header information, The email can be opened in a text editor such as [Notepad++](https://notepad-plus-plus.org/). Line 28 shows that the email was sent from IP 93.99.104.210, with the sending domain. 

Answer: emkei.cz

### **What is the Reply-To email address?**

The reply-to field shows where any response to this email will be sent to. The email address domain is the service being used by the malicious actor. This can be found on line 44 in a text editor, or by searching for the Reply-To field.

Answer: negeja3921@phashter.com

### **What is the filetype of the received attachment which helped to continue the investigation?**

The email attachment arrived as a pdf file, however a browser cannot properly view the PDF. This is because the PDF is actually a zip file. This could be discovered if the file is opened in a text editor, names of contained files will appear, implying that this is a zip file. [7-zip](https://www.7-zip.org/) can also “open inside” the file, revealing all contained files.

Answer: .zip

### **What is the name of the malicious actor?**

By using [exiftool](https://exiftool.org/), metadata about the PDF can be discovered, where other tools might only identify anticipated metadata fields based on the file type. One of the metadata fields includes the author of this document.

Answer: Pestero Negeja

### **What is the location of the attacker in this Universe?**

The previously analyzed PDF specifies which file to look at, Money.xlsx. This file can be discovered by a number of ways, but ultimately can be made visible in the same directory as  the PDF by selecting “show hidden files”.

![Screenshot of excel spreadsheet showing sheet 3 with a highlighted cell containing the encrypted location of the malicious actor.](/uploads/screenshot-2021-04-30-100445.jpg)

There are two pages with text. While there are numerous ways the answer can be located, I created a conditional formatting rule to highlight all cells that contains any text. The text is in the second page. Using Cyberchef to decode this, the location of the malicious actor was revealed.

Answer: The Martian Colony, Beside Interplanetary Spaceport

### **What could be the probable C&C domain to control the attacker’s autonomous bots?**

Since all mail that responds to this email goes to the listed Reply-To, it is probable that the autonomous bots are controlled under the same domain, and are listening for events sent by that domain.

Answer: phashter.com