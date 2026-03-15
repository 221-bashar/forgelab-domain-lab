# ForgeLab Domain Onboarding Lab

## Overview

This project simulates migrating a company from a workgroup environment to an Active Directory domain.

The environment was built in VMware Workstation using Windows Server 2016 and Windows 10.

---

## Lab Architecture

Domain: forgelab.local  
Domain Controller: DC1  
Client Machine: WS1  

Network: 192.168.50.0/24

DC1: 192.168.50.10  
WS1: 192.168.50.20  

---

## Implemented Features

Active Directory Domain Services  
DNS configuration  
Domain join  
Organizational Units (IT / HR)  
Security Groups  
Logon hour restrictions  
NTFS permissions  
SMB share permissions  
Security log monitoring

---

## Access Control Test

Share:

\\DC1\IT_ONLY

Results:

IT users → access allowed  
HR users → access denied

---

## Security Monitoring

Event IDs observed:

4624 – Successful logon  
4625 – Failed logon  
4740 – Account lockout  

---

## Skills Demonstrated

Active Directory administration  
Windows Server configuration  
Access control and permissions  
Security monitoring  
Blue team detection basics
