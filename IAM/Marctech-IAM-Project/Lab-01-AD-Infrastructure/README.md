# Lab 1 – Active Directory Infrastructure & Identity Foundation

## Real-World Scenario

Marctech is a growing organization with approximately 250 employees and needs a centralized identity and security infrastructure.

Previously, employee identities and workstation access were not centrally managed. As the organization grows, IT needs a directory service that can provide centralized authentication, authorization, user administration, and security management.

The Systems Administrator is tasked with establishing the organization's Active Directory environment.

---

## Business Objective

The objective of this lab was to establish the foundation of Marctech's Identity and Access Management (IAM) environment by deploying **Active Directory Domain Services (AD DS)**.

The implementation needed to provide:

* Centralized identity management
* Centralized authentication
* Organizational structure for employees
* Security group management
* A foundation for access control
* A platform for future Group Policy and IAM administration

---

# Lab Environment

| Component         | Configuration                        |
| ----------------- | ------------------------------------ |
| Server            | DC01                                 |
| Operating System  | Windows Server 2025                  |
| Directory Service | Active Directory Domain Services     |
| Domain            | `marctech.local`                     |
| Virtualization    | Oracle VirtualBox                    |
| Client            | PC01 – Windows 11                    |
| Management Tools  | Active Directory Users and Computers |

---

# Implementation

## 1. Windows Server Preparation

The Windows Server virtual machine was prepared to serve as the foundation for the Marctech domain environment.

The server was configured as:

```text
Hostname: DC01
```

DC01 would eventually provide centralized directory services for the Marctech environment.

---

## 2. Active Directory Domain Services

The **Active Directory Domain Services (AD DS)** role was installed on DC01.

AD DS provides the directory service used to centrally manage:

* Users
* Computers
* Groups
* Organizational Units
* Authentication
* Authorization

---

## 3. Domain Controller Promotion

After installing AD DS, DC01 was promoted to a Domain Controller.

The new Active Directory forest/domain was established as:

```text
marctech.local
```

This created the identity foundation for the Marctech environment.

---

## 4. Organizational Structure


An initial Organizational Unit (OU) structure was created to provide a logical organization for the Marctech Active Directory environment.

The structure included:

```text
marctech.local
│
├── Employees
└── Groups

Organizational Unit.

The OU provides a structured location for employee accounts and allows administrative policies to be applied logically as the environment expands.

---

## 5. Users and Security Groups

Initial Active Directory users and security groups were created as part of establishing the identity environment.

Security groups provide a foundation for implementing:

* Role-Based Access Control (RBAC)
* Department-based access
* Resource permissions
* Least-privilege access

These groups were used extensively in later IAM labs.

---

# Validation & Testing

After the Active Directory environment was configured, several validation activities were performed.

### Domain Verification

The Active Directory domain was verified as:

```text
marctech.local
```

### Active Directory Verification

The Active Directory Users and Computers console was used to verify:

* Domain structure
* Organizational Units
* User accounts
* Security groups

### Domain Controller Verification

DC01 was verified as the Domain Controller for the Marctech environment.

### Client Connectivity

PC01 was later configured as a Windows 11 domain client and used to validate communication with the domain environment.

---

# Security Relevance

Active Directory forms a major part of many Windows enterprise environments and is closely connected to cybersecurity and IAM.

The implementation established the ability to centrally control:

**Identity → Authentication → Authorization → Access**

This foundation allows later security controls such as:

* Group Policy
* Password policies
* RBAC
* Account lifecycle management
* Access control
* Auditing
* Administrative delegation

to be implemented consistently.

---

# Troubleshooting & Lessons Learned

During the broader Marctech environment build, several infrastructure and connectivity issues were encountered and investigated.

Common troubleshooting tools used throughout the environment included:

```powershell
ipconfig
ping
nslookup
```

These tools helped validate:

* IP configuration
* Network connectivity
* DNS resolution
* Domain communication

A key lesson from the project was that **DNS is critical to Active Directory functionality**. Domain services depend heavily on reliable name resolution, so DNS configuration must be considered when troubleshooting domain connectivity and authentication.

---

# Skills Demonstrated

* Windows Server administration
* Active Directory Domain Services
* Domain Controller deployment
* Active Directory domain creation
* Organizational Units
* User management
* Security groups
* Identity infrastructure
* Authentication concepts
* Authorization concepts
* DNS troubleshooting
* Client/server connectivity
* Virtual machine administration

---

# Evidence

The following screenshots provide implementation and validation evidence
from the Marctech Active Directory lab environment.

## 1. DC01 Server

[View DC01 Server Evidence](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/blob/main/IAM/Marctech-IAM-Project/Lab-01-AD-Infrastructure/Screenshots/01-DC01-Server.png)

This screenshot shows the Windows Server system used as the foundation
of the Marctech Active Directory environment.

---

## 2. Active Directory Domain

[View Active Directory Domain Evidence](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/blob/main/IAM/Marctech-IAM-Project/Lab-01-AD-Infrastructure/Screenshots/02-AD-Domain.png)

This screenshot provides evidence of the `marctech.local` Active
Directory domain established for the Marctech environment.

---

## 3. Active Directory Organizational Structure

[View OU Structure Evidence](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/blob/main/IAM/Marctech-IAM-Project/Lab-01-AD-Infrastructure/Screenshots/03-AD-OU-Structure.png)

This screenshot shows the initial organizational structure containing
the `Employees` and `Groups` Organizational Units.

---

## 4. Employee User Accounts

[View Employee Users Evidence](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/blob/main/IAM/Marctech-IAM-Project/Lab-01-AD-Infrastructure/Screenshots/04-Employee-Users.png)

This screenshot shows employee identity objects organized within the
`Employees` OU.

---

## 5. Security Groups

[View Security Groups Evidence](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/blob/main/IAM/Marctech-IAM-Project/Lab-01-AD-Infrastructure/Screenshots/05-Security-Groups.png)

This screenshot shows the security groups organized within the `Groups`
OU. These groups provide the foundation for access control and
Role-Based Access Control (RBAC) in later IAM activities.

---

> **Security note:** Screenshots published in this portfolio are limited
> to the fictional Marctech lab environment. Sensitive credentials,
> passwords, and unnecessary personal information are not published.

---


# Key Takeaway

This lab established the **identity foundation** for the Marctech cybersecurity environment.

The deployment of Active Directory transformed the environment from independently managed systems into a centralized identity infrastructure capable of supporting:

```text
Centralized Identity
        ↓
Authentication
        ↓
Authorization
        ↓
Access Control
        ↓
Security Management
```

All subsequent Marctech IAM labs build on this foundation.
