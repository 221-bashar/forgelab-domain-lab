# 🏗 ForgeLab Domain Onboarding Lab

## 📖 Overview

This project simulates migrating a small company from a **workgroup environment** to a **centralized Active Directory domain**.

The environment was built using **VMware Workstation Pro**, **Windows Server 2016**, and **Windows 10**.
The lab demonstrates how administrators deploy a domain controller, configure DNS, manage users and groups, enforce access control, and monitor authentication activity.

---

## 🧭 Scenario

ForgeWorks Ltd. is transitioning from a workgroup-based infrastructure to a **domain-based environment**.

Requirements:

* Centralized authentication
* Separate access for **HR** and **IT**
* Visibility into login attempts for administrators

The lab implements these requirements inside an **isolated VMware network**.

---

## 🖥 Lab Architecture

| Component          | Name | IP Address    | Role                   |
| ------------------ | ---- | ------------- | ---------------------- |
| Domain Controller  | DC1  | 192.168.50.10 | Active Directory + DNS |
| Client Workstation | WS1  | 192.168.50.20 | Domain Client          |

Network:

192.168.50.0 /24 (VMnet2 – Host-only)

Domain:

forgelab.local

---

## 🌐 Network Topology

VMnet2 (Host-only) 192.168.50.0/24

[ DC1 192.168.50.10 ] <----> [ WS1 192.168.50.20 ]
AD DS + DNS      Domain Client

---

## ⚙ Implemented Features

* Active Directory Domain Services (AD DS)
* DNS configuration
* Domain join process
* Organizational Units (IT / HR)
* Security groups for role-based access
* Logon hour restrictions
* NTFS permissions
* SMB share permissions
* Security log monitoring

---

## 🗂 Active Directory Structure

### Organizational Units

* IT
* HR

### Users

| IT  | HR  |
| --- | --- |
| IT1 | HR1 |
| IT2 | HR2 |

### Security Groups

| Group  | Members  |
| ------ | -------- |
| IT_GRP | IT1, IT2 |
| HR_GRP | HR1, HR2 |

---

## 🔐 Access Control Test

Shared folder:

\DC1\IT_ONLY

Permissions configured:

| Group    | Permission |
| -------- | ---------- |
| IT_GRP   | Modify     |
| HR Users | No Access  |

Test Results:

* IT users successfully accessed the share and created files.
* HR users received **Access Denied**.

---

## 📊 Security Monitoring

Authentication activity was verified using **Windows Event Viewer**.

| Event ID | Description      |
| -------- | ---------------- |
| 4624     | Successful logon |
| 4625     | Failed logon     |
| 4740     | Account lockout  |

These events allow administrators to detect authentication failures and potential password attack attempts.

---

## 🧪 Attack Simulation

A password-spraying simulation was performed by generating multiple incorrect login attempts.

Detection was verified through:

Event ID 4625 – Failed logon
Event ID 4740 – Account lockout

---

## 🛠 Skills Demonstrated

* Active Directory administration
* Windows Server deployment
* Domain-based authentication
* Access control and permission management
* Security event monitoring
* Basic blue-team detection techniques
