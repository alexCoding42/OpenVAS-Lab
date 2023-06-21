# Building a Vulnerability Management Lab (OpenVAS)

## Introduction

In this project, I utilized OpenVAS to perform some vulnerability scans on a Windows host, identified and remediated some of them.
First I set up a vulnerable Windows 10 virtual machine on Azure, installed outdated softwares on it and disabled security controls. 
I installed and configured OpenVAS on another Azure virtual machine to perform unauthenticated and credentialed vulnerability scans against the Windows host. 
Then I analyzed the scan results, highlighted the difference between unauthenticated and credentialed scans. 
Finally I remediated some identified vulnerabilities, and verified successful remediation through subsequent scans.
I also created a list of remediable vulnerabilities to simulate realistic vulnerability remediation scenarios.

## Lab Architecture
![Visual](https://www.dropbox.com/s/atoiab6qj1n4m39/OpenVAS%20Lab.jpg?raw=1)

## Unauthenticated Scan Results
Although I installed deprecated softwares on the Windows virtual machine, the scan was not able to identify them as vulnerabilities. 

![OpenVAS Dashboard](https://www.dropbox.com/s/r3jg99by7xu3zu4/Unauthenticated%20scan%20report.png?raw=1)

## Authenticated Scan Results
The scan with credentials (SMB) was able to identify many high vulnerabilities, most of them caused by the deprecated softwares installed.

![OpenVAS Dashboard](https://www.dropbox.com/s/yx4r6ou4osa8842/Authenticated%20scan%20report.png?raw=1)

## Remediation + Authenticated Scan Results
As remediation I uninstalled the deprecated softwares, and run a new authenticated scan. This time most of the high vulnerabilities linked to deprecated softwares were not detected, but some of them still exist maybe because of the version of Windows which is used (Windows 10 Pro 21H2)

![OpenVAS Dashboard](https://www.dropbox.com/s/pdxc19o4p7td28h/Authenticated%20scan%20report%20after%20remediation.png?raw=1)

## List of remediable vulnerabilities (scenario)
I wanted to simulate a more realistic scenario concerning vulnerabilities, so I asked ChatGPT about it:

### Prompt
I'm creating a vulnerability management lab where I create and then remediate vulnerabilities on a windows 10 computer for practice. What are some easy vulnerabilities I can create to practice remediating?

### ChatGPT Answer
Building a vulnerability management lab is an excellent idea for practical cybersecurity education. Here are some basic, easily-remediable vulnerabilities you can introduce in a Windows 10 environment for students to practice:
- Unpatched Software: Install older versions of popular software like Adobe Reader, Java, or browsers like Chrome, Firefox, etc. These older versions usually have well-documented vulnerabilities that can be identified and then patched to the latest version to remediate.
- Default/Weak Passwords: Set up accounts with weak or default passwords. This is a common vulnerability in real-world scenarios and teaching students to identify and rectify this can be valuable.
- Unused Services: Enable unnecessary services that could potentially be exploited. For example, Telnet. Have students disable unnecessary services as part of hardening the system.
- Unsecured Network Settings: Configure the system to allow insecure remote desktop connections, or create overly broad firewall rules. Students can then practice securing these settings.
- Missing Windows Updates: Disable automatic Windows updates and let the system become outdated. Students can then identify missing critical updates or patches using a vulnerability scanner.
- Insecure User Account Control (UAC) Settings: Lower the UAC settings on the system. This could allow certain programs to run with higher privileges without notifying the user.
- Publicly Shared Folders: Set some folders to be publicly shared with full control permissions. This vulnerability can be identified and remediated by adjusting the sharing permissions.
- Insecure Windows Registry Settings: For more advanced practice, make insecure changes to the Windows Registry. For example, disable User Account Control (UAC), or enable automatic login.
Outdated Antivirus Software: Install an outdated version of an antivirus software. Students can then identify this and update the software to its latest version.


## Conclusion
In this project, I used OpenVAS scanner to identify, understand and remediate some vulnerabilities. Only authenticated scans were able to find high vulnerabilities, the unauthenticated scan only scrathed the surface and did not detect the vulnerabilities caused by deprecated softwares. We noticed that the more deprecated softwares are the more high vulnerabilities can be identified. So as a good practice for remediation and mitigation it is important to keep our machine and softwares up to date.
Also in a more realistic scenario, ChatGPT gave us some ideas about vulnerabilities that can be created on purpose and remediated.
