# Building a Vulnerability Management Lab (OpenVAS)

## Introduction

In this project, I utilized OpenVAS to perform some vulnerability scans on a Windows host, identify, assess, prioritize and remediate some of them.

![Visual](https://www.dropbox.com/s/u8t13p5dzmzxl20/visual.jpg?raw=1)

## Steps
1. I set up a vulnerable Windows 10 virtual machine on Azure, installed outdated softwares on it and disabled security controls.
2. I installed and configured OpenVAS on another Azure virtual machine to perform unauthenticated and credentialed vulnerability scans against the Windows host. 
3. I analyzed the scan results, highlighted the difference between unauthenticated and credentialed scans. 
4. I generated reports to assess and prioritize most critical vulnerabilities
5. I remediated critical vulnerabilities, and verified successful remediation through subsequent scans.
6. I created a list of remediable vulnerabilities to simulate realistic vulnerability remediation scenarios.

## Preparation and Scope
The specific requirements is to be able to detect vulnerabilities caused by the deprecated softwares installed on the Windows 10 host.
The system and network infrastructure are simple : it is only a Windows 10 Virtual Machine, hosted on Azure, for which the security controls and firewalls have been disabled.

## Information Gathering
Regarding the environment it is only a Windows 10 Virtual Machine in Azure with one IP address. The Windows version is Windows 10 22H2.

## Identify Vulnerabilities

### Unauthenticated Scan Results
The first scan is a non credentialed scan. It was not able to detect any critical or high vulnerabilities, although deprecated softwares were installed.

![OpenVAS Dashboard](https://www.dropbox.com/s/r3jg99by7xu3zu4/Unauthenticated%20scan%20report.png?raw=1)

### Authenticated Scan Results
The credentialed scan was able to identify many high vulnerabilities. These vulnerabilities are caused by the presence of deprecated softwares installed on the host. Note that OpenVAS classify both *critical* and *high* vulnerabilities under the same label "High"

![OpenVAS Dashboard](https://www.dropbox.com/s/yx4r6ou4osa8842/Authenticated%20scan%20report.png?raw=1)

## Prioritize Vulnerabilities
By analyzing the report of the authenticated scan we can see that there is a lot of high vulnerabilities, but also some medium vulnerabilities and a bunch of informational ones. We exclude the informational vulnerabilities because there is no severity score for them, and we decide to prioritize only high vulnerabilities.

## Risk Assessment
High vulnerabilities have the highest severity score, so they can potentially impact the host.

## Recommendations
We recommand to remediate high vulnerabilities.

## Remediation Planning
As most of high vulnerabilities are caused by the deprecated softwares, we plan to remove the deprecated softwares from the host.

## Verification

Now that the deprecated softwares were removed on the Windows host, the next authenticated scan reveals that high vulnerabilities have been reduced drastically. By analysing the report we notice that all vulnerabilties caused by the deprecated softwares don't appear anymore.
Nevertheless,there are still some remaining high vulnerabilities. We didn't remediate them in this lab, but we suppose that they are caused by the version of the system itself; Windows 10 22H2 installed on the Azure Virtual Machine.

![OpenVAS Dashboard](https://www.dropbox.com/s/pdxc19o4p7td28h/Authenticated%20scan%20report%20after%20remediation.png?raw=1)

## Scenario: List of remediable vulnerabilities
We wanted to simulate a more realistic scenario concerning vulnerabilities, so we asked ChatGPT about it:

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
In this project, we used OpenVAS scanner to identify, understand and remediate some vulnerabilities. Only authenticated scans were able to find high vulnerabilities, the unauthenticated scan only scrathed the surface and did not detect the vulnerabilities caused by deprecated softwares. We noticed that the more deprecated softwares are installed on a host the more high vulnerabilities can be identified by a scan. So as a good practice to mitigate threats it is important to keep our softwares up to date.
Also in a more realistic scenario, ChatGPT gave us some ideas about vulnerabilities that can be created on purpose and remediated.
