## Hands-On Cybersecurity Projects & Labs
Hello, and welcome to my cybersecurity lab portfolio!

I'm Marceline, focused on developing and demonstrating practical cybersecurity skills through hands-on labs, projects, troubleshooting, validation, and security-focused automation.

This portfolio documents my work building and validating cybersecurity solutions in realistic, enterprise-style environments. My current area of focus is **Identity and Access Management (IAM)**, including identity lifecycle management, authentication, authorization, RBAC, Active Directory, access control, Windows security administration, and PowerShell automation.

As the portfolio grows, it will expand into additional areas of cybersecurity while maintaining the same hands-on approach:

**Build → Configure → Test → Troubleshoot → Validate → Document**

---

# Current Focus: Identity & Access Management

The first major project documented in this portfolio is a simulated enterprise IAM environment for **Marctech**, a fictional organization with approximately 250 employees.

The environment provides a practical setting for implementing and validating common IAM and cybersecurity concepts.

### Marctech Lab Environment

| Component          | Configuration                    |
| ------------------ | -------------------------------- |
| Directory Service  | Active Directory Domain Services |
| Domain             | `marctech.local`                 |
| Domain Controller  | DC01                             |
| Client Workstation | Windows 11 PC01                  |
| Server Platform    | Windows Server 2025              |
| Virtualization     | Oracle VirtualBox                |
| Automation         | PowerShell                       |
| Access Control     | RBAC / Security Groups           |
| Network Services   | DNS / DHCP                       |
| Policy Management  | Group Policy                     |
| File Security      | NTFS Permissions                 |

---

# Marctech IAM Project

The Marctech project follows an enterprise-style approach to Identity and Access Management, progressing from infrastructure and identity creation to access control, security policies, network services, and automation.

## Completed Labs

| Lab       | Focus                                                 | Status      |
| --------- | ----------------------------------------------------- | ----------- |
| **Lab 1** | Active Directory Infrastructure & Identity Foundation | ✅ Completed |
| **Lab 2** | Identity Lifecycle Management (JML)                   | ✅ Completed |
| **Lab 3** | RBAC & Access Management                              | ✅ Completed |
| **Lab 4** | Group Policy & Account Security                       | ✅ Completed |
| **Lab 5** | Windows Client Deployment & Domain Administration     | ✅ Completed |
| **Lab 6** | File Server & NTFS Permissions                        | ✅ Completed |
| **Lab 7** | DHCP & Network Identity Infrastructure                | ✅ Completed |
| **Lab 8** | PowerShell IAM Automation                             | ✅ Completed |

Detailed documentation and supporting evidence for each completed lab are being added to this repository.

---

# Cybersecurity & IAM Skills Demonstrated

### Identity & Access Management

* Identity provisioning
* Identity lifecycle management
* Joiner/Mover/Leaver processes
* Authentication
* Authorization
* Role-Based Access Control (RBAC)
* Least privilege
* Security group management
* Access provisioning
* Account administration

### Active Directory & Windows Security

* Active Directory Domain Services
* Domain Controllers
* Organizational Units
* User administration
* Security groups
* Group Policy
* Domain joining
* Windows authentication
* Account security
* NTFS permissions

### Network & Infrastructure Security

* DNS
* DHCP
* IP addressing
* Client/server connectivity
* Network troubleshooting
* Domain name resolution
* DHCP scopes and reservations

### Security Automation

* PowerShell
* Bulk identity provisioning
* CSV-based user provisioning
* Security group automation
* Administrative reporting
* IAM workflow automation

---

#  PowerShell Automation

The Marctech IAM project includes practical PowerShell automation for repetitive identity and access management tasks.

Current scripts include:

```text
Create-MarctechInterns.ps1
Assign-DepartmentAccess.ps1
Generate-Intern-Report.ps1
```

These scripts demonstrate how common IAM activities can be automated instead of performed manually.

The automation workflow follows:

```text
HR Employee Data
       ↓
Identity Provisioning
       ↓
Access Provisioning
       ↓
Validation & Reporting
```

---

# Hands-On Validation & Troubleshooting

A major part of this portfolio is validating that configurations actually work.

Labs include hands-on testing using tools and commands such as:

```text
ipconfig
ping
nslookup
Get-ADUser
Get-ADGroupMember
Get-ADOrganizationalUnit
```

Troubleshooting scenarios have included:

* DNS configuration
* Domain connectivity
* Domain authentication
* DHCP configuration
* Active Directory configuration
* Organizational Unit references
* PowerShell script errors
* Account administration
* Client/server communication
* Network adapter and connectivity issues

The goal is not simply to configure a service, but to understand how to **verify, troubleshoot, and validate** the resulting environment.

---

# Evidence & Documentation

Where appropriate, completed labs include supporting evidence such as:

* Configuration screenshots
* Active Directory screenshots
* Group Policy screenshots
* PowerShell output
* Network configuration
* Validation results
* Generated reports
* Architecture diagrams
* Troubleshooting evidence

Sensitive information will not be published. Passwords, credentials, personal information, and other sensitive configuration data will be sanitized or replaced with placeholders before being added to the public repository.

---

# Learning & Project Methodology

Each lab follows a practical cybersecurity workflow:

```text
Real-World Scenario
        ↓
Business / Security Objective
        ↓
Technical Implementation
        ↓
Testing
        ↓
Validation
        ↓
Troubleshooting
        ↓
Documentation
        ↓
Lessons Learned
```

This approach focuses not only on **what** was configured, but also:

* Why it was needed
* How it was implemented
* How it was tested
* What went wrong
* How issues were resolved
* What security principles were demonstrated

---

# Future Cybersecurity Work

The portfolio will continue to grow beyond the current IAM project.

Future projects will explore additional areas of cybersecurity as they are completed, documented, and validated through hands-on work.

Potential areas include:

* Network Security
* Security Operations
* Vulnerability Management
* Incident Response
* Cloud Security
* Endpoint Security
* Security Monitoring
* Security Automation
* Additional Identity Security topics
  
---

# Portfolio Goal

The goal of this portfolio is to demonstrate the ability to apply cybersecurity concepts in practical environments through implementation, security, troubleshooting, validation, automation, and documentation.

The portfolio will continue to evolve as new cybersecurity projects and hands-on labs are completed.
