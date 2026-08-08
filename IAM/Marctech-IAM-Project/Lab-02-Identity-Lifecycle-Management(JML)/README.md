# Lab 2 – Identity Lifecycle Management (JML)

## Real-World Scenario

Marctech is a growing organization with approximately 250 employees and needs a structured process for managing employee identities throughout the employment lifecycle.

As employees join the organization, change roles or departments, and eventually leave the organization, IT must ensure that their Active Directory identities and access remain accurate and aligned with their current business responsibilities.

The Systems Administrator is responsible for managing these identity lifecycle events within the Marctech Active Directory environment.

---

## Business Objective

The objective of this lab was to implement a basic **Identity Lifecycle Management** process using Active Directory.

The implementation needed to support:

* Employee identity provisioning
* Employee account administration
* Changes to employee identity information
* Department and role changes
* Security group membership management
* Account disabling during employee offboarding
* Access management based on current business responsibilities
* A repeatable Joiner-Mover-Leaver (JML) process

---

# Lab Environment

| **Component**     | **Configuration**                            |
| ----------------- | -------------------------------------------- |
| Server            | DC01                                         |
| Operating System  | Windows Server 2025                          |
| Directory Service | Active Directory Domain Services             |
| Domain            | `marctech.local`                             |
| Virtualization    | Oracle VirtualBox                            |
| Client            | PC01 – Windows 11                            |
| Management Tools  | Active Directory Users and Computers         |
| PowerShell        | Windows PowerShell / Active Directory Module |

---

# Implementation

## 1. Identity Provisioning – Joiner

The first stage of the identity lifecycle involved provisioning employee identities within Active Directory.

New employee accounts were created and configured within the Marctech domain.

The provisioning process included:

* Creating user accounts
* Configuring employee information
* Assigning usernames
* Assigning initial passwords
* Enabling accounts
* Placing users in the appropriate Organizational Unit
* Assigning appropriate security-group memberships

The process established the employee's digital identity within the `marctech.local` domain.

---

## 2. Employee Identity Administration

After accounts were created, employee identity information could be maintained through Active Directory Users and Computers.

Administrative activities included reviewing and modifying:

* Employee names
* Department information
* Job titles
* Account status
* Group memberships
* Password settings

This demonstrated that identity administration continues after the initial account-creation process.

---

## 3. Role or Department Change – Mover

The mover stage simulated an employee changing responsibilities within Marctech.

When an employee changes departments or job responsibilities, their identity and access must be reviewed.

The process followed:

```text
Employee Role Change
        ↓
Update Identity Information
        ↓
Review Existing Access
        ↓
Remove Unnecessary Access
        ↓
Assign Required Access
        ↓
Validate
```

The purpose of this process is to ensure that employees do not retain access that is no longer required for their current responsibilities.

---

## 4. Security Group Management

Security groups were used to manage access rather than assigning permissions directly to individual users.

Department-based groups provide a scalable foundation for Role-Based Access Control (RBAC).

Examples of departmental security groups used in the Marctech environment included:

```text
SG_IT_Users
SG_HR_Users
SG_Finance_Users
SG_Marketing_Users
SG_Sales_Users
SG_Executive_Users
```

Users could be added to or removed from these groups as their business responsibilities changed.

---

## 5. Account Deprovisioning – Leaver

The leaver stage simulated an employee leaving Marctech.

When an employee leaves the organization, the user's Active Directory account should no longer be permitted to authenticate.

The account was disabled to prevent continued use of the identity.

The basic offboarding process followed:

```text
Employee Leaves
       ↓
Disable Account
       ↓
Review Group Membership
       ↓
Review Access
       ↓
Preserve Required Records
       ↓
Document Offboarding
```

Disabling the account provides an immediate control against unauthorized authentication while preserving the identity object for administrative and record-management purposes.

---

# Validation & Testing

After completing the identity lifecycle activities, the configuration was validated through Active Directory.

### User Account Verification

Active Directory Users and Computers was used to verify:

* User accounts
* Account properties
* Department information
* Job titles
* Account status

### Security Group Verification

Security group membership was reviewed to verify that users were assigned to the appropriate groups.

### Account Status Verification

User accounts were checked to confirm whether they were:

* Enabled
* Disabled

### Authentication Validation

Domain authentication was used to validate that active accounts could authenticate within the Marctech domain environment.

Disabled-account scenarios were also reviewed to confirm that inactive identities could not be used for normal domain authentication.

---

# Security Relevance

Identity Lifecycle Management is a fundamental component of cybersecurity and IAM.

Poor identity lifecycle management can result in:

* Orphaned accounts
* Excessive permissions
* Former employees retaining access
* Privilege accumulation
* Unauthorized authentication
* Increased attack surface

The Joiner-Mover-Leaver process helps ensure that access remains aligned with an employee's current business relationship with the organization.

The lifecycle can be represented as:

```text
Joiner
   ↓
Identity Created
   ↓
Access Assigned
   ↓
Mover
   ↓
Access Reviewed / Modified
   ↓
Leaver
   ↓
Identity Disabled
```

This supports the security principles of:

* Least privilege
* Access review
* Separation of duties
* Account security
* Controlled deprovisioning

---

# Troubleshooting

## Account Administration Issues

During identity lifecycle administration, account changes must be verified carefully to ensure that the correct user object is being modified.

Administrative verification through Active Directory Users and Computers was used to confirm that changes were applied to the intended account.

### Lesson Learned

Before modifying an identity, administrators should verify the user's:

* Name
* Username
* Department
* Role
* Account status

This reduces the risk of making administrative changes to the wrong identity.

---

## Group Membership Validation

When employee responsibilities change, simply adding a user to a new security group may leave the user with unnecessary permissions from their previous role.

### Lesson Learned

A mover process should include both:

**Access Addition**

and

**Access Removal**

rather than only adding new permissions.

This helps maintain least privilege.

---

# Skills Demonstrated

* Identity Lifecycle Management
* Joiner-Mover-Leaver (JML)
* Active Directory administration
* User provisioning
* User account administration
* Account disabling
* Security group management
* Role-Based Access Control
* Least privilege
* Access review
* Identity validation
* Windows Server administration
* Active Directory Users and Computers
* IAM operational procedures

---

# Evidence

The following screenshots provide implementation and validation evidence from the Marctech Identity Lifecycle Management lab environment.

## 1. Employee User Accounts

[View Employee User Evidence](../Lab-01-AD-Infrastructure/Screenshots/04-Employee-Users.png)

This evidence shows employee identity objects within the Marctech Active Directory environment.

---

## 2. User Properties

[View User Properties Evidence](./Screenshots/02-User-Properties.png)

This screenshot should show the selected employee's Active Directory properties, including relevant identity information such as department and job title.

---

## 3. Security Group Membership

[View Security Group Evidence](./Screenshots/03-Security-Group-Membership.png)

This screenshot provides evidence of the user's Active Directory security-group membership.

---

## 4. Account Status

[View Account Status Evidence](./Screenshots/04-Account-Status.png)

This screenshot provides evidence of the account's enabled or disabled state during the lifecycle process.

---

## 5. Lifecycle Validation

[View Lifecycle Validation Evidence](./Screenshots/05-Lifecycle-Validation.png)

This evidence documents the validation of identity lifecycle changes within the Marctech environment.

---

> **Security note:** Screenshots published in this portfolio are limited to the fictional Marctech lab environment. Sensitive credentials, passwords, personal information, and unnecessary private network information are not published.

---

# Key Takeaway

This lab demonstrated that **IAM is a continuous lifecycle rather than a one-time account creation process**.

Employees join the organization, their roles and responsibilities may change, and eventually they leave.

A properly managed identity lifecycle ensures that:

```text
Employee
    ↓
Identity
    ↓
Authentication
    ↓
Access
    ↓
Role Changes
    ↓
Access Review
    ↓
Offboarding
    ↓
Account Disabled
```

The implementation established a practical Joiner-Mover-Leaver process that can serve as the foundation for more advanced IAM capabilities such as automated provisioning, access governance, privileged access management, MFA, conditional access, and identity auditing.
