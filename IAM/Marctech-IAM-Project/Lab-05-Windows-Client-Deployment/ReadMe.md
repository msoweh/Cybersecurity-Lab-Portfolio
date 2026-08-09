
# Lab 5 – Windows Client Deployment & Active Directory Domain Join

## Real-World Scenario

Marctech has hired a new employee, **Marie Joan**, who has completed the identity onboarding process through Human Resources and the Identity & Access Management team.

Marie Joan's identity already exists in Active Directory.

The Infrastructure Team has received a service request to deploy and prepare a Windows 11 workstation for production use.

The workstation must:

* Join the corporate Active Directory domain
* Authenticate using centralized identity
* Receive Group Policy
* Enforce the organization's password policy
* Recognize the employee's Active Directory group memberships
* Be registered as a computer object in Active Directory

The Identity & Access Management team is responsible for validating that the workstation and employee identity are successfully integrated into the corporate environment.

---

## Business Objective

The objective of this lab was to deploy **PC01**, integrate it with the `marctech.local` Active Directory environment, and validate successful employee authentication.

The implementation needed to demonstrate:

* Workstation network configuration
* DNS configuration for Active Directory
* Windows workstation domain joining
* Domain authentication
* Password policy enforcement
* Group Policy application
* Active Directory computer registration
* Employee identity and workstation integration
* Recognition of existing RBAC group memberships

---

# Service Request

| **Field**        | **Details**                                            |
| ---------------- | ------------------------------------------------------ |
| Ticket Number    | `LAB5-002`                                             |
| Requested By     | Infrastructure Operations                              |
| Assigned To      | Identity & Access Management Team                      |
| Employee         | Marie Joan                                             |
| Department       | IT                                                     |
| Role             | Systems Administrator                                  |
| Workstation      | PC01                                                   |
| Requested Action | Deploy and integrate workstation with Active Directory |

---

# Lab Environment

## Domain Controller

| **Component**    | **Configuration**                     |
| ---------------- | ------------------------------------- |
| Computer Name    | DC01                                  |
| Operating System | Windows Server 2022                   |
| Domain           | `marctech.local`                      |
| Roles            | Active Directory Domain Services, DNS |

## Client Workstation

| **Component**    | **Configuration** |
| ---------------- | ----------------- |
| Computer Name    | PC01              |
| Operating System | Windows 11 Pro    |
| Network          | Wi-Fi             |
| Domain           | `marctech.local`  |

## Assigned Employee

| **Attribute** | **Value**                   |
| ------------- | --------------------------- |
| Employee      | Marie Joan                  |
| Department    | IT                          |
| Role          | Systems Administrator       |
| Windows Login | `MARCTECH\marie.joan`       |
| UPN           | `marie.joan@marctech.local` |

---

# Implementation

## 1. Configure Workstation Networking

PC01 was connected to the lab network through Wi-Fi.

The workstation's network configuration was reviewed to confirm DHCP addressing and DNS configuration.

DNS was configured to use the Domain Controller because Active Directory relies on DNS for domain discovery and locating domain services.

---

## 2. Join PC01 to Active Directory

PC01 was successfully joined to:

```text
marctech.local
```

The domain join was performed using an authorized administrative account.

Windows displayed:

```text
Welcome to the marctech.local domain.
```

This confirmed that the workstation successfully established membership in the Active Directory domain.

---

## 3. Restart the Workstation

PC01 was restarted after the domain join.

The restart allowed Windows to complete the domain-join process and establish the workstation's secure relationship with the Domain Controller.

---

## 4. Validate Employee Authentication

After the workstation restart, Marie Joan authenticated using:

```text
MARCTECH\marie.joan
```

The successful login demonstrated that PC01 could authenticate the employee against the centralized Active Directory environment.

---

## 5. Validate Password Policy Enforcement

During Marie Joan's first domain logon, Windows required the user to change the temporary password.

The initial password change attempt was rejected because it did not satisfy the organization's password policy.

The password was subsequently changed to meet the requirements established in the previous Group Policy lab, including:

* Minimum password length of 14 characters
* Password complexity requirements

The password was then accepted successfully.

### Security Significance

This demonstrated that the password policy configured centrally through Group Policy was being enforced when the employee authenticated from the newly deployed workstation.

---

## 6. Create Domain User Profile

After successful authentication, Windows created Marie Joan's domain user profile on PC01.

The workstation displayed:

```text
Welcome Marie Joan
```

This demonstrated successful first-time profile creation for the domain user.

---

## 7. Validate Group Policy and RBAC Integration

The workstation was validated to confirm that the expected Group Policy was being applied.

The applied Group Policy Objects included:

```text
Workstation Security Policy
```

The authenticated user's existing Active Directory group memberships were also recognized, including:

```text
SG_IT_Users
DL_IT_AdminTool_RW
```

This demonstrated that the workstation deployment was integrating with the existing IAM and RBAC configuration established in previous labs.

---

# Validation & Testing

## Workstation Validation

The following validation activities were completed:

| **Validation**                     | **Result** |
| ---------------------------------- | ---------- |
| Logged in using domain credentials | ✅          |
| Computer joined to domain          | ✅          |
| Domain authentication              | ✅          |
| Password policy enforced           | ✅          |
| Group Policy applied               | ✅          |
| DNS configured correctly           | ✅          |
| Communication with DC01            | ✅          |

---

## Active Directory Validation

PC01 was also verified within Active Directory.

| **Validation**                        | **Result** |
| ------------------------------------- | ---------- |
| PC01 appears in Active Directory      | ✅          |
| Computer account enabled              | ✅          |
| Secure trust relationship established | ✅          |

The computer object confirmed that PC01 had successfully become part of the Marctech Active Directory environment.

---

## Domain Authentication Validation

The authenticated identity was verified using Windows identity information.

The expected identity was:

```text
MARCTECH\marie.joan
```

This provided client-side evidence that the workstation was using centralized Active Directory authentication.

---

## Group Policy Validation

Group Policy processing was validated using:

```powershell
gpresult /r
```

The results showed the expected:

```text
Workstation Security Policy
```

This confirmed that PC01 was receiving centralized security configuration from the Marctech Active Directory environment.

---

# Troubleshooting

## Issue 1 – Virtual Machine Resource Limitations

The lab environment had insufficient memory to run multiple Windows virtual machines simultaneously.

### Resolution

The lab architecture was adapted to use:

* Virtualized Domain Controller
* Physical Windows 11 workstation

This configuration also reflects a realistic enterprise scenario in which Domain Controllers may be virtualized while employee workstations are physical devices.

---

## Issue 2 – DNS Configuration Prevented Domain Discovery

The initial workstation DNS configuration prevented PC01 from successfully discovering the Active Directory domain.

### Resolution

The workstation's DNS configuration was changed to point directly to DC01.

After correcting DNS, domain discovery and the domain-join process succeeded.

### Lesson Learned

Active Directory depends heavily on DNS.

A workstation can have general Internet or network connectivity and still be unable to join an Active Directory domain if it cannot correctly resolve the Domain Controller and required domain services.

---

## Issue 3 – Password Rejected During First Logon

The initial password-change attempt during Marie Joan's first logon was rejected.

### Resolution

The password was changed to meet the organization's configured requirements:

* Minimum length of 14 characters
* Complexity requirements

The password was then accepted successfully.

### Lesson Learned

Password policies configured through Group Policy are enforced during user authentication and password changes.

---

# Security Relevance

This lab demonstrated that IAM extends beyond creating a user account in Active Directory.

A complete identity lifecycle requires the identity to be successfully connected to the resources the employee needs to perform their job.

The process demonstrated:

```text
Employee Identity
       ↓
Active Directory Account
       ↓
Workstation Deployment
       ↓
Domain Join
       ↓
Centralized Authentication
       ↓
Password Policy
       ↓
Group Policy
       ↓
RBAC Group Membership
       ↓
Managed Workstation
```

This represents an important real-world IAM principle:

> **An employee identity is not fully operational until the identity can securely authenticate to the systems and resources required for the employee's role.**

The lab also demonstrated the dependency between **DNS, Active Directory, authentication, Group Policy, and endpoint management**.

---

# IAM Concepts Reinforced

* Centralized identity
* Active Directory authentication
* Domain membership
* Domain trust relationships
* Kerberos authentication concepts
* DNS dependency for Active Directory
* Password policy enforcement
* Group Policy processing
* User profile provisioning
* Role-Based Access Control (RBAC)
* Workstation registration
* Identity lifecycle completion
* Endpoint identity integration

---

# Skills Demonstrated

* Windows 11 deployment
* Windows workstation administration
* Active Directory administration
* DNS configuration
* DNS troubleshooting
* Domain joining
* Domain authentication
* Password policy troubleshooting
* Group Policy validation
* Active Directory computer management
* Identity verification
* RBAC validation
* Enterprise workstation deployment
* IAM operational validation

---

# Evidence


The following screenshots provide implementation and validation evidence from the Marctech Windows Client Deployment and Active Directory Domain Join lab.

## 1. Active Directory Domain Join

[View Domain Join Success Evidence](./Screenshots/01-Domain-Join-Success.png)

This screenshot shows Windows confirming that PC01 successfully joined the `marctech.local` Active Directory domain.

This provides evidence that the workstation was successfully integrated into the organization's centralized identity environment.

---

## 2. Domain User Authentication

[View Domain User Authentication Evidence](./Screenshots/02-Domain-User-Authentication.png)

This screenshot provides evidence of successful authentication using the centralized Marctech domain identity:

```text
MARCTECH\marie.joan
```

This demonstrates that the employee was able to authenticate to the Windows workstation using Active Directory credentials.

---

## 3. Identity and Workstation Validation

[View Identity and Workstation Validation Evidence](./Screenshots/03-Identity-Workstation-Validation.png)

This screenshot provides client-side validation of the authenticated identity and workstation.

The validation includes:

```text
whoami
hostname
```

The expected results identify the authenticated user as:

```text
MARCTECH\marie.joan
```

and the workstation as:

```text
PC01
```

This connects the employee's centralized identity to the correctly deployed workstation.

---

## 4. Employee Profile Creation

[View Employee Profile Creation Evidence](./Screenshots/04-Employee-Profile-Creation.png)

This screenshot provides evidence that Windows successfully created Marie Joan's domain user profile following her first successful authentication.

The profile creation demonstrates that the domain identity was successfully recognized by the Windows client.

---

## 5. Group Policy Validation

[View Group Policy Validation Evidence](./Screenshots/05-Group-Policy-Validation.png)

This screenshot shows the output of:

```powershell
gpresult /r
```

The results provide evidence that the expected:

```text
Workstation Security Policy
```

was applied to PC01.

This demonstrates that the workstation successfully received centralized security policy from the Marctech Active Directory environment.

---

## 6. PC01 Active Directory Registration

[View PC01 Active Directory Evidence](./Screenshots/06-PC01-Active-Directory.png)

This screenshot shows PC01 registered as a computer object within **Active Directory Users and Computers**.

This provides server-side evidence that the workstation successfully became a member of the `marctech.local` domain.

---

## 7. Marie Joan Active Directory Identity

[View Marie Joan Active Directory Evidence](./Screenshots/07-Marie-Joan-Active-Directory.png)

This screenshot shows Marie Joan's Active Directory account and relevant identity information.

Where visible, the evidence also demonstrates the employee's existing Active Directory group memberships, including:

```text
SG_IT_Users
DL_IT_AdminTool_RW
```

This connects the employee's centralized identity and existing RBAC configuration to the workstation authentication demonstrated in this lab.

---

> **Security note:** Screenshots published in this portfolio are limited to the fictional Marctech lab environment. Sensitive credentials, passwords, private information, and unnecessary security-sensitive details are not published.

---

# Key Takeaway

This lab demonstrated the complete integration of an employee identity with a Windows workstation in an Active Directory environment.

The deployment progressed from:

```text
Network Configuration
        ↓
DNS Configuration
        ↓
Domain Join
        ↓
Computer Registration
        ↓
Employee Authentication
        ↓
Password Policy Enforcement
        ↓
User Profile Creation
        ↓
Group Policy
        ↓
RBAC Recognition
```

The successful deployment demonstrated that **Identity and Access Management extends beyond account creation**.

A production-ready identity must be able to securely authenticate to managed systems, receive appropriate security policies, and access resources according to the user's role.

The lab also reinforced the operational importance of DNS, Active Directory, Group Policy, and RBAC working together as part of an enterprise IAM environment.
