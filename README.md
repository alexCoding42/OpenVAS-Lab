# Building a Vulnerability Management Lab (OpenVAS)

## Introduction

In this project, I utilized OpenVAS to perform some vulnerability scans on a Windows host, identified and remediated some of them.
First I set up a vulnerable Windows 10 virtual machine on Azure, installed outdated softwares on it and disabled security controls. 
I installed and configured OpenVAS on another Azure virtual machine to perform unauthenticated and credentialed vulnerability scans against the Windows host. 
Then I analyzed the scan results, highlighted the difference between unauthenticated and credentialed scans. 
Finally I remediated some identified vulnerabilities, and verified successful remediation through subsequent scans.

## Architecture
![Visual](https://www.dropbox.com/s/atoiab6qj1n4m39/OpenVAS%20Lab.jpg?raw=1)
