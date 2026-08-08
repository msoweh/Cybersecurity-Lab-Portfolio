# Lab 3 – Role-Based Access Control (RBAC) Design & Access Management

## Real-World Scenario

Following the successful deployment of Active Directory Domain Services in Lab 1 and the implementation of Joiner-Mover-Leaver (JML) identity lifecycle processes in Lab 2, Marctech continued its Identity Modernization Program by implementing a structured Role-Based Access Control (RBAC) model.

As the organization grows, assigning resource permissions directly to individual users or relying only on department-based groups can become difficult to manage, audit, and scale.

The Identity and Access Management team was tasked with designing an access management structure that separates employee identities from resource permissions and supports the Principle of Least Privilege.

To address this requirement, Marctech implemented Microsoft's **AGDLP** methodology:

**Accounts → Global Groups → Domain Local Groups → Permissions**

---

## Business Objective

The objective of this lab was to establish a scalable **Role-Based Access Control (RBAC)** model using Active Directory security groups and Microsoft's AGDLP methodology.

The implementation needed to:

- Separate user identities from resource permissions
- Use Global Security Groups to represent business roles or departments
- Use Domain Local Security Groups as the resource-access layer
- Implement nested group memberships
- Reduce the need for direct user-to-resource permissions
- Support the Principle of Least Privilege
- Simplify future access reviews and auditing
- Prepare the environment for future File Server and NTFS permission implementation


  ## Lab Environment

| Component | Configuration |
|---|---|
| Server | DC01 |
| Operating System | Windows Server 2025 |
| Directory Service | Active Directory Domain Services |
| Domain | `marctech.local` |
| Virtualization | Oracle VirtualBox |
| Management Tools | Active Directory Users and Computers |
| Automation / Validation | Windows PowerShell / Active Directory Module |

---

## Existing Identity Model

The department-based Global Security Groups created during Lab 1 represented Marctech's existing business roles.

| Global Security Group | Department |
|---|---|
| `SG_IT_Users` | IT |
| `SG_Finance_Users` | Finance |
| `SG_Marketing_Users` | Marketing |
| `SG_HR_Users` | HR |
| `SG_Sales_Users` | Sales |

These Global Security Groups remained the identity and business-role layer of the access model.

Rather than assigning resource permissions directly to these groups, the RBAC design introduced a separate Domain Local Security Group layer.

## Implementation

## 1. RBAC Architecture

The RBAC design separated business identities from resource permissions.

The implemented access model follows:

**User Account → Global Security Group → Domain Local Security Group → Resource Permission**

This design allows administrators to manage employee membership independently from the permissions assigned to organizational resources.

---

## 2. Domain Local Security Groups

Domain Local Security Groups were created to represent access to specific organizational resources.

The following three Domain Local Security Groups were implemented for this demonstration:

| Domain Local Security Group | Purpose |
|---|---|
| `DL_IT_AdminTools_RW` | Read/Write access to IT administration resources |
| `DL_Finance_Files_RW` | Read/Write access to Finance resources |
| `DL_Marketing_Files_RW` | Read/Write access to Marketing resources |

### Demonstration Scope

Three Domain Local Security Groups were intentionally implemented for this lab to demonstrate the AGDLP access model.

This was a focused demonstration of the RBAC design rather than a complete implementation for every Marctech department.

Additional resource-specific Domain Local Security Groups can be created as the organization's file shares, applications, and other protected resources expand.

The three groups created in this lab represent the resource-access layer and are intended to receive permissions during the future File Server and NTFS Permissions implementation.

---

## 3. AGDLP Design

Marctech implemented Microsoft's AGDLP methodology.

The access model is:

**Accounts → Global Groups → Domain Local Groups → Permissions**

The model separates the employee's identity and business role from the permissions required to access organizational resources.

For example:

**Employee → SG_IT_Users → DL_IT_AdminTools_RW → IT Administration Resource**

This approach reduces the need to assign permissions directly to individual users.

---

## 4. Nested Group Configuration

The existing Global Security Groups were nested within the appropriate Domain Local Security Groups.

The implemented relationships were:

| Global Security Group | Nested Into |
|---|---|
| `SG_IT_Users` | `DL_IT_AdminTools_RW` |
| `SG_Finance_Users` | `DL_Finance_Files_RW` |
| `SG_Marketing_Users` | `DL_Marketing_Files_RW` |

These relationships establish the following access paths:

| Business Role Group | Resource Access Group |
|---|---|
| `SG_IT_Users` | `DL_IT_AdminTools_RW` |
| `SG_Finance_Users` | `DL_Finance_Files_RW` |
| `SG_Marketing_Users` | `DL_Marketing_Files_RW` |

The nested group structure separates business role membership from resource access permissions.

---

## 5. Resource Permission Model

The Domain Local Security Groups were designed to serve as the groups that receive permissions to organizational resources.

Permissions were not assigned directly to individual users.

The intended architecture is:

**User → Global Group → Domain Local Group → Resource Permission**

The resource-permission layer will be implemented during the future File Server and NTFS Permissions lab.

This design allows changes to employee roles or departments to be managed through group membership rather than by modifying individual resource permissions.

## 6. Example Access Flow

For example, **Marie Joan** is a member of the Global Security Group:

`SG_IT_Users`

That Global Security Group is nested within:

`DL_IT_AdminTools_RW`

The resulting access relationship is:

**Marie Joan → SG_IT_Users → DL_IT_AdminTools_RW → IT Administration Resources**

When resource permissions are assigned to `DL_IT_AdminTools_RW`, members of `SG_IT_Users` can inherit the appropriate access without requiring individual permission assignments.

This demonstrates how the AGDLP model separates identity management from resource authorization.

---

## 7. Validation & Testing

The RBAC implementation was validated using both **Active Directory Users and Computers (ADUC)** and **PowerShell**.

## Active Directory Validation

The Active Directory environment was reviewed to verify:

- Creation of Domain Local Security Groups
- Group scope
- Group category
- Security group configuration
- Nested group membership
- Separation between Global Security Groups and Domain Local Security Groups

---

## 8. PowerShell Validation

PowerShell was used to validate the Domain Local Security Groups and their memberships.

The following command was used to review the groups and their configuration:

```powershell
Get-ADGroup -Filter 'Name -like "DL_*"' |
Select-Object Name, GroupScope, GroupCategory
```

The membership of each Domain Local Security Group was then validated using:

```powershell
Get-ADGroupMember DL_IT_AdminTools_RW
Get-ADGroupMember DL_Finance_Files_RW
Get-ADGroupMember DL_Marketing_Files_RW
```

The validation confirmed that the appropriate Global Security Groups were successfully nested within the corresponding Domain Local Security Groups.


## 9. Security Relevance + Troubleshooting + Lessons Learned

## Security Relevance

Role-Based Access Control (RBAC) is an important cybersecurity and Identity and Access Management (IAM) capability.

Without a structured access model, organizations can accumulate:

- Excessive permissions
- Direct user-to-resource assignments
- Permission sprawl
- Difficult-to-audit access relationships
- Privilege creep
- Increased administrative overhead

The AGDLP model provides a structured way to separate:

**Identity → Business Role → Resource Access → Permission**

This supports the **Principle of Least Privilege** by allowing access to be granted according to business requirements rather than assigning permissions individually to users.

The model also makes employee onboarding, role changes, offboarding, and access reviews easier to manage.

---

## Troubleshooting

## Group Scope and Membership Validation

When implementing nested security groups, it is important to verify that the correct group scope and membership relationships are configured.

A group name alone does not demonstrate that the RBAC model has been implemented correctly.

Validation therefore included:

- Confirming the group exists
- Confirming the group is a Security group
- Confirming the group scope
- Confirming the correct Global Security Group is nested
- Confirming the intended resource-access relationship

## Lesson Learned

RBAC implementation should be validated at the **group relationship level**, not only by checking whether groups were created.

The effectiveness of an AGDLP design depends on the relationships between:

**Accounts → Global Groups → Domain Local Groups → Permissions**

---

## Business Benefits

The RBAC and AGDLP implementation provides Marctech with several operational and security benefits:

- Centralized access management
- Reduced administrative overhead
- Simplified onboarding and offboarding
- Easier access reviews
- Improved scalability
- Support for Least Privilege
- Reduced permission creep
- Separation of identity and resource permissions
- Easier future resource-permission management
- Preparation for File Server and NTFS permissions
- Foundation for future identity governance capabilities

---

## Skills Demonstrated

- Role-Based Access Control (RBAC)
- Identity and Access Management (IAM)
- Active Directory Security Groups
- Global Security Groups
- Domain Local Security Groups
- Microsoft AGDLP methodology
- Group nesting
- Access management
- Principle of Least Privilege
- Active Directory administration
- PowerShell administration
- Security group validation
- Identity architecture
- Access-control design

---

## 10. Evidence

The following screenshots provide implementation and validation evidence from the Marctech RBAC and Access Management lab environment.

All portfolio screenshots are maintained in PNG format.

# 1. Domain Local Security Groups

[View Domain Local Groups Evidence](PASTE-ACTUAL-GITHUB-LINK-HERE)

This screenshot provides evidence of the Domain Local Security Groups created for the RBAC demonstration.

The groups represent the resource-access layer of the AGDLP model.

---

# 2. Group Scope and Type

[View Group Scope and Type Evidence](PASTE-ACTUAL-GITHUB-LINK-HERE)

This screenshot provides evidence that the RBAC groups were configured with the intended Active Directory group scope and security group type.

---

# 3. IT Group Nesting

[View IT Group Nesting Evidence](PASTE-ACTUAL-GITHUB-LINK-HERE)

This screenshot provides evidence that `SG_IT_Users` was nested within `DL_IT_AdminTools_RW` as part of the AGDLP implementation.

---

# 4. Finance Group Nesting

[View Finance Group Nesting Evidence](PASTE-ACTUAL-GITHUB-LINK-HERE)

This screenshot provides evidence that `SG_Finance_Users` was nested within `DL_Finance_Files_RW` as part of the AGDLP implementation.

---

# 5. Marketing Group Nesting

[View RBAC Membership Separation Evidence](PASTE-ACTUAL-GITHUB-LINK-HERE)

This screenshot demonstrates the separation between employee identity, business-role membership, and resource access.

The employee is assigned to the appropriate Global Security Group rather than being directly assigned to the Domain Local resource-access group.

The resulting access model follows:

`User Account → Global Security Group → Domain Local Security Group → Resource Permission`

This separation supports centralized access management, easier access reviews, and the Principle of Least Privilege.


---

# 6. PowerShell Validation

[View PowerShell Validation Evidence](PASTE-ACTUAL-GITHUB-LINK-HERE)

This screenshot provides PowerShell-based validation of the Domain Local Security Groups and their configured memberships.

The validation demonstrates that the RBAC configuration was verified programmatically in addition to being reviewed through Active Directory Users and Computers.

---

> **Security note:** Screenshots published in this portfolio are limited to the fictional Marctech lab environment. Sensitive credentials, passwords, personal information, and unnecessary private network information are not published.

---

## 11. Key Takeaway

This lab established a structured **Role-Based Access Control and AGDLP framework** for the Marctech Active Directory environment.

The implementation separated employee identities and business roles from resource permissions:

**User Account → Global Security Group → Domain Local Security Group → Resource Permission**

By implementing this layered model, Marctech established a scalable foundation for centralized access management, least-privilege enforcement, access reviews, and future resource-permission administration.

The three Domain Local Security Groups created in this demonstration provide the foundation for the subsequent **File Server and NTFS Permissions** implementation, where resource permissions can be assigned to the appropriate access groups.

This architecture also provides a foundation for future IAM capabilities such as access governance, privileged access management, auditing, and cloud identity integration.
