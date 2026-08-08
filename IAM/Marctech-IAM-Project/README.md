# Marctech Identity & Access Management Project

## Enterprise-Style IAM Hands-On Lab Environment

The **Marctech IAM Project** is a hands-on Identity and Access Management environment designed to simulate the identity and security operations of a small enterprise.

The project uses a fictional organization, **Marctech**, with approximately 250 employees. The environment provides a practical setting for implementing, testing, troubleshooting, and documenting common IAM and Windows security processes.

The project is part of the broader **Cybersecurity Lab Portfolio** and represents the portfolio's initial focus on Identity and Access Management.

---

## Project Objective

The objective of this project is to build and operate an enterprise-style identity environment while developing practical skills in:

* Identity provisioning
* Identity lifecycle management
* Authentication
* Authorization
* Role-Based Access Control (RBAC)
* Active Directory administration
* Group Policy
* Access control
* Windows security
* Network identity services
* PowerShell automation
* Troubleshooting and validation

The project emphasizes not only configuration, but also the ability to explain **why a control is needed, how it works, how it is validated, and how problems are resolved**.

---

# Business Scenario

Marctech is a growing organization with approximately 250 employees across multiple departments.

As the organization grows, IT needs a centralized system to manage:

* Employee identities
* Authentication
* Authorization
* Departmental access
* Workstations
* Security policies
* Network configuration
* File access
* User onboarding
* Administrative reporting

The project simulates the responsibilities of an IT/IAM team supporting this environment.

---

#  Lab Environment

| Component          | Configuration                    |
| ------------------ | -------------------------------- |
| Domain             | `marctech.local`                 |
| Domain Controller  | DC01                             |
| Client Workstation | PC01                             |
| Server OS          | Windows Server 2025              |
| Client OS          | Windows 11                       |
| Directory Service  | Active Directory Domain Services |
| Virtualization     | Oracle VirtualBox                |
| Automation         | PowerShell                       |
| Network Services   | DNS / DHCP                       |
| Access Control     | Security Groups / RBAC           |
| Policy Management  | Group Policy                     |
| File Security      | NTFS Permissions                 |

---

# 🗺️ Project Architecture

At a high level, the environment follows this model:

```text
                         Marctech IAM Environment
                                  │
                                  │
                         Active Directory
                                  │
                    ┌─────────────┴─────────────┐
                    │                           │
                  DC01                        PC01
             Domain Controller             Windows 11
                    │                           │
                    ├── Users                   │
                    ├── Groups                  │
                    ├── OUs                     │
                    ├── Group Policy            │
                    ├── DNS                     │
                    └── DHCP                    │
```

The environment is expanded throughout the labs as additional identity, access, security, and automation capabilities are implemented.

---

# IAM Concepts Covered

The project demonstrates practical implementation of:

### Identity Management

* User provisioning
* Account administration
* Identity lifecycle management
* Joiner/Mover/Leaver processes
* Account enablement and disablement
* Password administration

### Access Management

* Authentication
* Authorization
* RBAC
* Security groups
* Least privilege
* Department-based access

### Directory Services

* Active Directory
* Domain Controllers
* Organizational Units
* Users
* Security Groups
* Group Policy

### Infrastructure & Security

* DNS
* DHCP
* Windows security
* NTFS permissions
* Domain-joined clients
* Network troubleshooting

### Automation

* PowerShell
* CSV-based provisioning
* Bulk account creation
* Access assignment
* Administrative reporting

---

# Completed Labs

| Lab                                                                                          | Focus                                    | Status      |
| -------------------------------------------------------------------------------------------- | ---------------------------------------- | ----------- |
| [Lab 1 – Active Directory Infrastructure & Identity Foundation](./Lab-01-AD-Infrastructure/) | AD DS and identity foundation            | ✅ Completed |
| Lab 2 – Identity Lifecycle Management                                                        | Joiner/Mover/Leaver                      | ✅ Completed |
| Lab 3 – RBAC & Access Management                                                             | Role-based access control                | ✅ Completed |
| Lab 4 – Group Policy & Account Security                                                      | Centralized security policy              | ✅ Completed |
| Lab 5 – Windows Client Deployment                                                            | Domain joining and client administration | ✅ Completed |
| Lab 6 – File Server & NTFS Permissions                                                       | File access control                      | ✅ Completed |
| Lab 7 – DHCP & Network Identity Infrastructure                                               | DHCP and network configuration           | ✅ Completed |
| Lab 8 – PowerShell IAM Automation                                                            | Identity and access automation           | ✅ Completed |

> Detailed documentation for each completed lab is being added to the repository as the project is documented.

---

# IAM Workflow

The project follows an enterprise-style identity and access workflow:

```text
Employee / HR Event
        ↓
Identity Provisioning
        ↓
Authentication
        ↓
Access Assignment
        ↓
Security Policy
        ↓
Resource Access
        ↓
Monitoring / Validation
        ↓
Lifecycle Change
        ↓
Disable / Remove Access
```

This represents the broader IAM lifecycle rather than treating user creation as an isolated administrative task.

---

# Troubleshooting Approach

Troubleshooting is treated as an important part of the project rather than an afterthought.

Issues encountered during the labs have included:

* DNS configuration
* Domain connectivity
* Domain authentication
* DHCP configuration
* Active Directory OU references
* PowerShell syntax and parameter errors
* Network adapter issues
* Client/server communication
* Account administration problems

The troubleshooting process generally follows:

```text
Identify
   ↓
Collect Evidence
   ↓
Isolate the Problem
   ↓
Apply a Controlled Fix
   ↓
Retest
   ↓
Document the Result
```

---

# Evidence & Documentation

Each lab will include appropriate evidence where available, such as:

* Active Directory screenshots
* Group Policy configuration
* PowerShell output
* Network configuration
* Validation results
* Access-control testing
* Generated reports
* Architecture diagrams
* Troubleshooting evidence

Sensitive information will be removed or sanitized before publication.

---

# Project Progress

The project is actively being developed.

Completed work is documented as it is finished, while future IAM capabilities will be added to this project as the hands-on labs are completed.

The broader cybersecurity portfolio will eventually include projects outside IAM.

---

# Key Takeaway

The Marctech IAM Project demonstrates how identity and access management supports cybersecurity by controlling:

**Who can access the environment → How they authenticate → What they are authorized to access → How access is managed throughout the identity lifecycle.**

The project combines IAM concepts with practical Active Directory, Windows administration, networking, access control, troubleshooting, and automation.
