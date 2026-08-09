# Lab 6 – Windows File Server & Role-Based Access Control (RBAC)

## Real-World Scenario

Marctech Solutions has expanded its workforce across multiple departments, including IT, Human Resources, Finance, Sales, Marketing, and Executive Management.

Employees require access to department-specific documents to perform their job responsibilities. However, unrestricted access to departmental resources creates unnecessary security risk and violates the organization's **Principle of Least Privilege**.

The IT department requested a secure file-sharing solution where authorized IT personnel could access sensitive IT documentation while users from other departments were prevented from accessing those resources.

As the Systems Administrator, I was tasked with implementing a Windows File Server using **Active Directory security groups, Role-Based Access Control (RBAC), and the AGDLP model**.

---

## Business Objective

The objective of this lab was to implement a secure departmental file-sharing solution that:

* Restricts access based on job roles
* Uses Active Directory security groups instead of individual user permissions
* Implements the AGDLP security model
* Enforces the Principle of Least Privilege
* Separates identity management from resource permissions
* Allows administrators to manage access through security groups
* Validates both authorized and unauthorized access

The implementation demonstrates how enterprise organizations can manage file access through **group-based authorization rather than assigning permissions directly to individual employees**.

---

# Lab Environment

| Component         | Configuration                    |
| ----------------- | -------------------------------- |
| Domain            | `marctech.local`                 |
| Domain Controller | DC01                             |
| File Server       | DC01                             |
| Client            | PC01 – Windows 11 Pro            |
| Directory Service | Active Directory Domain Services |
| File Protocol     | SMB                              |
| Access Model      | RBAC                             |
| Permission Model  | AGDLP                            |
| Virtualization    | Oracle VirtualBox                |

---

# Implementation

## 1. File Server Configuration

Windows File Server functionality was verified on DC01.

DC01 was used as the file server for the Marctech lab environment.

The file server provides centralized storage that can be accessed by authorized domain users through SMB network shares.

---

## 2. Departmental Folder Structure

A centralized departmental directory was created:

```text
C:\Departments
│
├── IT
├── HR
├── Finance
├── Sales
├── Marketing
└── Executive
```

The structure provides separate locations for departmental resources.

This allows access controls to be applied according to department and business role.

---

## 3. Role-Based Access Control

Active Directory security groups were used to manage resource access.

Rather than assigning permissions directly to individual employees, users were associated with role-based security groups.

For the IT department, the access model was:

```text
Marie Joan
     ↓
SG_IT_Users
     ↓
DL_IT_File_RW
     ↓
Modify Permission
     ↓
IT File Resources
```

This provides a scalable permission-management model.

If an employee joins the IT department, the administrator can add the employee to the appropriate security group rather than modifying permissions on every IT resource individually.

---

## 4. AGDLP Implementation

The lab followed the **AGDLP** model:

```text
Account
   ↓
Global Group
   ↓
Domain Local Group
   ↓
Permission
```

The Marctech implementation was:

```text
Marie Joan
     ↓
SG_IT_Users
     ↓
DL_IT_File_RW
     ↓
Modify
     ↓
C:\Departments\IT
```

This separates:

**Who the user is**

from:

**What resource the user can access.**

This is an important IAM design principle because access can be managed through role membership rather than individual resource permissions.

---

## 5. NTFS Permission Configuration

NTFS permissions were configured on the IT department folder.

The following actions were performed:

* Disabled permission inheritance on the IT folder
* Converted inherited permissions to explicit permissions
* Removed the general `Users` permission
* Added `DL_IT_File_RW`
* Assigned **Modify** permission
* Retained required administrative and system permissions

The resulting access model allowed authorized members of the IT role group to modify IT resources while preventing unauthorized domain users from accessing the folder.

### Why NTFS Permissions Matter

NTFS permissions determine what users are authorized to do with files and folders on the Windows file system.

Examples include:

```text
Read
Write
Modify
Full Control
```

The **Modify** permission was used for the IT role because IT users needed to work with departmental files without requiring unrestricted Full Control.

This supports the **Principle of Least Privilege**.

---

## 6. SMB Share Configuration

The IT folder was published as an SMB network share:

```text
\\DC01\IT
```

The share name was:

```text
IT
```

The share-level permission was configured as:

```text
Everyone → Full Control
```

NTFS permissions were then used to provide the granular resource authorization.

### Share Permissions vs. NTFS Permissions

This lab demonstrated an important Windows file-server security concept.

**Share permissions** control access when a resource is accessed through the network share.

**NTFS permissions** control access to files and folders on the file system.

For network access, Windows evaluates both.

A useful model is:

```text
Share Permissions
        +
NTFS Permissions
        ↓
Effective Network Access
```

In this implementation, the share permission was intentionally broad while **NTFS permissions provided the granular authorization control**.

---

# Validation & Testing

The access-control design was validated using different user identities representing different organizational roles.

## 1. Authorized Access Test

The IT role was tested using:

```text
MARCTECH\marie.joan
```

The user successfully accessed:

```text
\\DC01\IT
```

The administrator test file was visible and accessible.

**Result: PASS**

This confirmed that the configured RBAC and NTFS permissions allowed the authorized IT user to access the IT resource.

---

## 2. Unauthorized Access Test

An HR user was then used to test unauthorized access:

```text
MARCTECH\jess.curtis
```

The user attempted to access:

```text
\\DC01\IT
```

The system returned:

```text
Access Denied
```

**Result: PASS**

This demonstrated that the access-control configuration prevented an unauthorized department from accessing IT resources.

---

## 3. Authorization Validation

The two tests demonstrated both sides of the access-control model.

### Authorized User

```text
Authorized User
      ↓
IT Security Group
      ↓
Domain Local Resource Group
      ↓
NTFS Permission
      ↓
ACCESS GRANTED
```

### Unauthorized User

```text
Unauthorized User
      ↓
No Required IT Access Group
      ↓
NTFS Authorization Check
      ↓
ACCESS DENIED
```

This provided practical validation of:

* Authentication
* Authorization
* RBAC
* Least Privilege
* Group-based access control

---

# Security Relevance

File servers are common enterprise resources and require carefully designed access controls.

Poorly configured file permissions can result in:

* Unauthorized access to sensitive information
* Excessive user privileges
* Accidental modification or deletion
* Data exposure between departments
* Difficult access administration

The RBAC and AGDLP implementation addresses these risks by separating:

```text
Identity
   ↓
Role
   ↓
Access Group
   ↓
Resource Permission
```

This approach supports:

* Role-Based Access Control
* Least Privilege
* Centralized authorization
* Separation of duties
* Scalable access administration
* Easier employee onboarding and offboarding

The lab also reinforced the important IAM distinction between:

> **Authentication — Who are you?**

and:

> **Authorization — What are you allowed to access?**

---

# Troubleshooting

## Issue 1 – Unable to Remove Users Permission

### Problem

The `Users` permission could not initially be removed from the IT folder because the permission was inherited from the parent directory.
The inherited permission was identified as broader than the access required for the IT departmental resource.

### Resolution

The folder's permission inheritance was reviewed before making changes.

Because the IT folder required a more restrictive permission model than its parent, inheritance was disabled for that specific folder and the existing inherited permissions were converted to explicit permissions.

The unnecessary `Users` permission was removed, while the required administrative, system, and role-based permissions were retained.

### Lesson Learned

Windows NTFS inheritance can cause permissions to appear on child folders even when they were not explicitly configured there.

Understanding inheritance is important when troubleshooting unexpected access.

---

## Issue 2 – Password Complexity Error

### Problem

An account password did not meet the existing domain password policy.

### Resolution

The password was reset using a password that satisfied the configured domain requirements, including the 14-character minimum and complexity requirements.

### Lesson Learned

Active Directory password policy affects account provisioning and password-reset operations.

---

## Issue 3 – Security Context Error

### Problem

A user encountered a security-context authentication issue during the first-logon process.

### Resolution

The user's password was reset and the initial logon process was completed successfully.

### Lesson Learned

Authentication problems can sometimes originate from account state or credential issues rather than resource permissions.

---

## Issue 4 – Domain Unavailable

### Problem

The client temporarily reported that the domain was unavailable.

### Resolution

Domain Controller connectivity and network connectivity were checked, and the authentication attempt was retried after network connectivity stabilized.

### Lesson Learned

Domain authentication depends on reliable communication between the client and domain infrastructure.

---

## Issue 5 – PC01 Network Connectivity

### Problem

PC01 temporarily lost its network connection.

### Resolution

Network connectivity was restored before continuing domain authentication and file-share testing.

### Lesson Learned

Network connectivity is a prerequisite for accessing domain resources and SMB shares.

---

## Issue 6 – Unauthorized User Denied Access

### Problem

Jess Curtis was unable to access the IT file share.

### Resolution

The access denial was verified as expected behavior.

Jess Curtis was not authorized for the IT resource, so the denial demonstrated that the RBAC and NTFS security configuration was functioning correctly.

### Lesson Learned

An **Access Denied** message is not always an error. In an appropriately secured environment, access denial can be the expected security outcome.

---

# Skills Demonstrated

* Windows File Server administration
* SMB network shares
* NTFS permissions
* Share permissions
* Active Directory
* Active Directory security groups
* Role-Based Access Control (RBAC)
* AGDLP
* Group-based authorization
* Principle of Least Privilege
* Authentication vs. authorization
* Access validation
* Authorization troubleshooting
* Windows networking
* File-system security
* Permission inheritance
* Security group administration

---

# Evidence


The following screenshots provide implementation and validation evidence from the Marctech Windows File Server and Role-Based Access Control (RBAC) lab environment.

## 1. File Server & Departmental Folder Structure

[View File Server & Folder Structure Evidence](./Screenshots/01-File-Server-Folder-Structure.png)

This screenshot shows the Windows file server configuration and the departmental folder structure created for Marctech.

The departmental structure provides separate locations for:

* IT
* HR
* Finance
* Sales
* Marketing
* Executive

These folders provide separate resource locations where department-specific access controls can be applied.

---

## 2. RBAC & AGDLP Group Structure

[View RBAC & AGDLP Evidence](./Screenshots/02-RBAC-AGDLP-Groups.png)

This screenshot shows the Active Directory security groups used to implement role-based access to departmental resources.

The configuration demonstrates the relationship between the user's security group and the Domain Local group used to assign resource permissions.

The implementation follows the **AGDLP** model:

```text
Account
   ↓
Global Group
   ↓
Domain Local Group
   ↓
Permission
```

This approach separates identity management from resource authorization and supports scalable access administration.

---

## 3. NTFS Permissions

[View NTFS Permissions Evidence](./Screenshots/03-NTFS-Permissions.png)

This screenshot provides evidence of the NTFS permissions configured on the IT departmental folder.

The `DL_IT_File_RW` group was assigned **Modify** permission while unnecessary broad access was removed.

This demonstrates:

* Group-based authorization
* Least-privilege access
* Controlled departmental resource access
* Centralized permission management

---

## 4. SMB Share Configuration

[View SMB Share Configuration Evidence](./Screenshots/04-SMB-Share-Configuration.png)

This screenshot provides evidence of the IT departmental SMB share configured as:

```text
\\DC01\IT
```

The evidence demonstrates how the departmental folder was published as a network resource for authorized domain users.

The implementation uses SMB for network-based access while NTFS permissions provide the granular file-system authorization.

---

## 5. Authorized Access Validation

[View Authorized Access Evidence](./Screenshots/05-Authorized-Access-Validation.png)

This screenshot demonstrates successful access to the IT network share using the authorized IT user.

The user was able to access:

```text
\\DC01\IT
```

and view the administrator test file.

**Result: PASS**

This validates that the RBAC and NTFS configuration successfully granted the required access to the appropriate role.

---

## 6. Unauthorized Access Validation

[View Unauthorized Access Evidence](./Screenshots/06-Unauthorized-Access-Validation.png)

This screenshot demonstrates an attempted access to the IT network share using an HR user who was not authorized for the IT resource.

The system returned:

```text
Access Denied
```

**Result: PASS**

This validates that the RBAC and NTFS configuration successfully prevented unauthorized access to the IT departmental resource.

An access-denied result was the expected security outcome for the unauthorized user.

---

# Security Consideration

Disabling inheritance on a folder is **not inherently unsafe** and is a normal administrative control when a resource requires permissions that differ from its parent.

In a production environment, however, inheritance should not be disabled arbitrarily. An administrator should first:

* Review the permissions being inherited
* Determine why the child resource requires different access
* Document the intended permission model
* Preserve required administrative and system access
* Apply the Principle of Least Privilege
* Validate the resulting effective permissions
* Test both authorized and unauthorized access

In this lab, inheritance was disabled specifically because the IT departmental resource required a more restrictive access model based on the organization's RBAC design.

The purpose was not simply to remove an inherited permission, but to establish a deliberate security boundary for the IT departmental resource while retaining the permissions required for system and administrative operations.

---

> **Security note:** Screenshots published in this portfolio are limited to the fictional Marctech lab environment. Passwords, credentials, and unnecessary sensitive information are not published.

---

# Key Takeaway

This lab demonstrated how **Windows file-server permissions can be integrated with Active Directory RBAC and the AGDLP model to enforce least-privilege access**.

The implementation followed:

```text
User Account
      ↓
Global Security Group
      ↓
Domain Local Group
      ↓
NTFS Permission
      ↓
Departmental Resource
```

The access-control model was validated using both an authorized IT user and an unauthorized HR user.

The authorized user successfully accessed the IT share, while the unauthorized user received:

```text
Access Denied
```

This demonstrated the complete IAM authorization flow:

```text
Identity
    ↓
Authentication
    ↓
Role Membership
    ↓
Authorization
    ↓
Resource Access
```

The lab reinforced that effective IAM is not simply about creating user accounts.

It also requires designing **who can access what resources, why they can access them, and how those permissions are centrally managed and validated**.
