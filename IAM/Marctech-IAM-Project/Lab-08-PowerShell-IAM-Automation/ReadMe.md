# Lab 8 – PowerShell Automation for Identity Lifecycle Management

## Real-World Scenario

Marctech hired five new interns who were scheduled to begin work on Monday.

Before their first day, the IT and IAM teams needed to:

* Provision their Active Directory accounts
* Assign department-based access
* Configure initial account settings
* Verify security group membership
* Provide HR with documentation confirming the onboarding process

Instead of manually creating each account through Active Directory Users and Computers (ADUC), the Systems Administrator automated the onboarding process using **PowerShell and CSV-based employee data**.

This approach demonstrates how identity administration can be scaled through automation while maintaining consistent provisioning and validation procedures.

---

## Business Objective

The objective of this lab was to automate key portions of the **Joiner process** within Marctech's Identity and Access Management environment.

The implementation was designed to:

* Create Active Directory user accounts from an HR spreadsheet
* Assign department-based security group membership
* Configure initial account settings
* Generate onboarding reports
* Reduce repetitive manual administration
* Improve provisioning consistency and accuracy
* Provide validation after automated changes

The lab demonstrates how PowerShell can be used to automate repetitive IAM administration while retaining centralized Active Directory controls.

---

# Lab Environment

| Component            | Configuration                               |
| -------------------- | ------------------------------------------- |
| Domain Controller    | DC01                                        |
| Operating System     | Windows Server 2025 Evaluation              |
| Directory Service    | Active Directory Domain Services            |
| Domain               | `marctech.local`                            |
| Management Tool      | PowerShell                                  |
| PowerShell Module    | Active Directory                            |
| Directory Management | Active Directory Users and Computers (ADUC) |
| Input Format         | CSV                                         |
| Employee OU          | `Employees`                                 |

---

# Implementation

## Phase 1 – PowerShell Fundamentals

The lab began by verifying the PowerShell environment and the Active Directory PowerShell module.

Basic Active Directory commands were executed to retrieve directory information and inspect user accounts.

PowerShell filtering and object-selection techniques were also practiced.

The following concepts were reinforced:

* `-Filter`
* `-eq`
* PowerShell Pipeline (`|`)
* Active Directory cmdlets
* Object properties
* Selecting and filtering directory data

These concepts formed the foundation for the automation tasks completed later in the lab.

---

## Phase 2 – Active Directory Discovery

PowerShell was used to query Active Directory and retrieve user information.

The lab demonstrated how administrators can use PowerShell to:

* Query users
* Retrieve user properties
* Filter directory objects
* Select specific properties
* Generate administrative information

This provides a more scalable approach to directory administration than manually reviewing accounts through the ADUC graphical interface.

For example, PowerShell can retrieve directory objects and pass them through a pipeline for further processing:

```text
Active Directory
      ↓
PowerShell Query
      ↓
Filter / Select
      ↓
Administrative Output
```

---

## Phase 3 – Identity Administration

PowerShell was used to perform common IAM and Help Desk administrative tasks.

The following operations were completed:

* Reset user password
* Unlock user account
* Disable user account
* Enable user account
* Force password change at next logon
* Add a user to an existing security group

Changes were subsequently verified through **Active Directory Users and Computers (ADUC)**.

This demonstrated how routine identity administration can be performed through PowerShell while still using ADUC for visual verification.

---

# Phase 4 – Identity Provisioning Automation

A PowerShell provisioning script was created:

```text
Create-MarctechInterns.ps1
```

The script used an HR CSV file as the source of employee information.

The automation performed the following actions:

* Imported employee information from CSV
* Created five Active Directory accounts
* Assigned temporary passwords
* Enabled the accounts
* Required password changes at first logon
* Placed users in the `Employees` Organizational Unit

The provisioning workflow was:

```text
HR CSV
   ↓
PowerShell
   ↓
New-ADUser
   ↓
Active Directory
   ↓
Employee Accounts
```

---

## New Interns Provisioned

| Name          | Department | Role             |
| ------------- | ---------- | ---------------- |
| Emily Stunie  | Marketing  | Marketing Intern |
| Merci Reed    | Marketing  | Marketing Intern |
| Joan Grant    | Sales      | Sales Intern     |
| Ethel Ross    | Sales      | Sales Intern     |
| Rosiel Brooks | IT         | IT Intern        |

The five accounts were successfully created and validated in Active Directory.

---

# Phase 5 – Department Access Provisioning

A separate PowerShell script was created:

```text
Assign-DepartmentAccess.ps1
```

The script automated department-based security group assignment.

The script:

* Read the onboarding CSV
* Determined each employee's department
* Assigned users to the appropriate department security group

The security groups used were:

```text
SG_Marketing_Users
SG_Sales_Users
SG_IT_Users
```

The access-provisioning workflow was:

```text
Employee
   ↓
Department
   ↓
Department Security Group
   ↓
Department-Based Access
```

This demonstrates a practical implementation of **Role-Based Access Control (RBAC)** using Active Directory security groups.

---

## Access Validation

Group membership was validated using:

```powershell
Get-ADGroupMember
```

The results were also verified through **Active Directory Users and Computers (ADUC)**.

This provided two levels of validation:

```text
PowerShell Verification
        +
ADUC Verification
        ↓
Confirmed Group Membership
```

---

# Phase 6 – Administrative Reporting

A third PowerShell script was created:

```text
Generate-Intern-Report.ps1
```

The script automated the generation of an onboarding report for HR and management.

The script:

* Retrieved intern accounts
* Sorted employee information
* Exported the results
* Generated a CSV report

The resulting report was:

```text
InternUsers.csv
```

This demonstrates how PowerShell can be used not only for provisioning but also for **IAM reporting and administrative documentation**.

---

# Automation Workflow

The three primary automation scripts created during the lab form a simple IAM onboarding workflow:

```text
                    HR CSV
                      │
                      ▼
          Create-MarctechInterns.ps1
                      │
                      ▼
             Active Directory
                      │
                      ▼
             User Accounts
                      │
                      ▼
          Assign-DepartmentAccess.ps1
                      │
                      ▼
          Department Security Groups
                      │
                      ▼
             Access Provisioned
                      │
                      ▼
           Generate-Intern-Report.ps1
                      │
                      ▼
              InternUsers.csv
                      │
                      ▼
                  HR Report
```

This represents a simplified automated **Joiner process**.

---

# Validation & Testing

Validation was performed after the automation tasks to ensure that the scripts produced the expected results.

The following were verified:

### User Account Validation

New intern accounts were verified in ADUC.

### Security Group Validation

Department-based group membership was verified using:

```powershell
Get-ADGroupMember
```

and through ADUC.

### Account Status Validation

The account state and provisioning settings were reviewed to confirm that the accounts were enabled and configured as intended.

### Password Settings Validation

The configured initial password behavior and password-change requirement were verified.

### Reporting Validation

The generated:

```text
InternUsers.csv
```

report was reviewed to confirm that the expected intern information was exported successfully.

### Script Execution Validation

Each automation script was executed successfully and the resulting Active Directory changes were validated.

---

# Security Relevance

PowerShell automation is highly relevant to enterprise IAM because identity environments can contain hundreds or thousands of users.

Manually provisioning every account increases the possibility of:

* Incorrect usernames
* Incorrect group membership
* Inconsistent account settings
* Missed onboarding steps
* Administrative errors

Automation can reduce repetitive manual work by applying the same provisioning logic consistently.

The lab demonstrates the relationship between:

```text
Identity Data
     ↓
Automated Provisioning
     ↓
Account Configuration
     ↓
Access Assignment
     ↓
Validation
     ↓
Reporting
```

This supports several important IAM principles:

* Centralized identity management
* RBAC
* Least-privilege access
* Standardized provisioning
* Auditability
* Consistency
* Reduced administrative error

---

# Security Considerations

Automation improves consistency, but automation scripts must themselves be managed securely.

In a production environment, administrators should consider:

* Protecting scripts from unauthorized modification
* Restricting who can execute provisioning scripts
* Protecting temporary credentials
* Avoiding hard-coded production passwords
* Validating input data before provisioning accounts
* Logging provisioning actions
* Reviewing group assignments
* Using appropriate administrative privileges
* Testing scripts before production deployment

The lab used a controlled training environment to demonstrate the provisioning workflow.

Production implementations should use organizational credential-management and privileged-access controls appropriate to the environment.

---

# Troubleshooting

## Issue 1 – Incorrect Organizational Unit Path

### Problem

The initial provisioning script attempted to place users into an OU path that did not match the actual Active Directory structure.

### Resolution

The available Organizational Units were verified using:

```powershell
Get-ADOrganizationalUnit -Filter *
```

The correct `Employees` OU distinguished name was then used in the provisioning script.

### Lesson Learned

Automation scripts should be validated against the actual directory structure before execution.

A small difference in an OU distinguished name can cause automated provisioning to fail.

---

## Issue 2 – Department Group Assignment

### Problem

Department-based access needed to be assigned after the user accounts were created.

### Resolution

A separate access-provisioning script was created:

```text
Assign-DepartmentAccess.ps1
```

The script read each employee's department from the CSV file and assigned the appropriate security group.

### Lesson Learned

Separating **identity provisioning** from **access provisioning** makes automation easier to understand, troubleshoot, and maintain.

---

## Issue 3 – PowerShell Command Parameter Error

### Problem

During identity administration, an attempted command used an unsupported parameter for the cmdlet being executed.

### Resolution

The command syntax was corrected and the appropriate Active Directory PowerShell operation was used.

### Lesson Learned

PowerShell cmdlets have specific parameter sets. Administrators should verify cmdlet syntax rather than assuming that similar Active Directory commands support identical parameters.

---

# IAM Concepts Reinforced

This lab reinforced several important IAM concepts:

### Joiner Process

Automated creation and configuration of accounts for new employees.

### Identity Provisioning

Creating and configuring an identity within Active Directory.

### Access Provisioning

Assigning users to security groups based on their department and role.

### RBAC

Using security groups to associate users with role- or department-based access.

### Lifecycle Management

Demonstrating the provisioning portion of the broader identity lifecycle.

### Administrative Reporting

Generating structured reports from directory data.

### Automation

Replacing repetitive manual administrative tasks with repeatable PowerShell workflows.

---

# PowerShell Scripts Created

The following scripts were created during the lab:

### 1. Create-MarctechInterns.ps1

Responsible for automated Active Directory account creation from the HR CSV.

### 2. Assign-DepartmentAccess.ps1

Responsible for department-based security group assignment.

### 3. Generate-Intern-Report.ps1

Responsible for generating the intern onboarding report.

The three scripts collectively demonstrate:

```text
Provision
   ↓
Assign Access
   ↓
Report
```

---

# Skills Demonstrated

* PowerShell automation
* Active Directory administration
* Identity provisioning
* Access provisioning
* RBAC
* Security group management
* Bulk user creation
* CSV import automation
* Active Directory querying
* PowerShell filtering
* PowerShell pipelines
* Administrative reporting
* Identity lifecycle management
* Active Directory validation
* IAM Joiner process

---

# Evidence

The following screenshots provide implementation and validation evidence from the Marctech PowerShell Automation for Identity Lifecycle Management lab environment.

## 1. PowerShell Active Directory Discovery

[View PowerShell Active Directory Discovery Evidence](./Screenshots/01-PowerShell-AD-Discovery.png)

This screenshot shows PowerShell querying Active Directory and retrieving user information using Active Directory cmdlets, filtering, and pipeline techniques.

The evidence demonstrates the use of PowerShell for directory discovery and administrative data retrieval.

---

## 2. Automated Identity Provisioning

[View Automated Identity Provisioning Evidence](./Screenshots/02-Automated-Identity-Provisioning.png)

This screenshot shows the successful execution of `Create-MarctechInterns.ps1` and the resulting provisioning of the five Marctech intern accounts.

The evidence demonstrates automated account creation from the HR CSV data.

**Result: PASS**

---

## 3. Provisioned Intern Accounts

[View Provisioned Intern Accounts Evidence](./Screenshots/03-Provisioned-Intern-Accounts.png)

This screenshot shows the five newly created intern accounts in Active Directory Users and Computers (ADUC).

The accounts include:

* Emily Stunie
* Merci Reed
* Joan Grant
* Ethel Ross
* Rosiel Brooks

This validates that the automated provisioning process successfully created the expected identities in Active Directory.

---

## 4. Department-Based Access Assignment

[View Department-Based Access Evidence](./Screenshots/04-Department-Group-Membership.png)

This screenshot shows the department security group memberships assigned by `Assign-DepartmentAccess.ps1`.

The relevant groups include:

```text
SG_Marketing_Users
SG_Sales_Users
SG_IT_Users
```

The evidence demonstrates department-based access provisioning using Active Directory security groups and supports the Marctech RBAC model.

**Result: PASS**

---

## 5. Automated IAM Reporting

[View Automated Reporting Evidence](./Screenshots/05-Intern-Report-Generation.png)

This screenshot shows the successful execution of `Generate-Intern-Report.ps1` and the generation of the onboarding report.

The evidence demonstrates that the automation process can retrieve and organize intern identity information for administrative reporting.

---

## 6. Generated Intern Report

[View InternUsers.csv Report Evidence](./Screenshots/06-InternUsers-Report.png)

This screenshot shows the generated `InternUsers.csv` report containing the provisioned intern information.

The report provides documented evidence of the onboarding process and can be used by HR or management for administrative verification.

**Result: PASS**

---

# Evidence Summary

The six screenshots demonstrate the complete automated IAM onboarding workflow:

```text
PowerShell AD Discovery
        ↓
Automated Identity Provisioning
        ↓
Active Directory User Accounts
        ↓
Department-Based Access Assignment
        ↓
Automated Reporting
        ↓
InternUsers.csv
```

The evidence demonstrates that PowerShell was used to automate identity provisioning, department-based access assignment, validation, and administrative reporting within the Marctech Active Directory environment.

> **Security note:** Screenshots published in this portfolio are limited to the fictional Marctech lab environment. Passwords, temporary credentials, and unnecessary sensitive information should not be published.

---

# Key Takeaway

This lab demonstrated how PowerShell can automate important portions of the **Identity and Access Management lifecycle**, particularly the Joiner process.

Instead of manually creating each account and assigning access individually, the Marctech environment used structured employee data and PowerShell automation:

```text
HR Employee Data
       ↓
Identity Provisioning
       ↓
Active Directory Account
       ↓
Department Access
       ↓
Security Group Membership
       ↓
Validation
       ↓
Administrative Reporting
```

The lab demonstrated that IAM automation is not simply about creating accounts faster.

Effective automation should provide:

* Consistency
* Repeatability
* Controlled access assignment
* Validation
* Reporting
* Reduced administrative error

The three PowerShell scripts created during this lab provide a foundation for extending the Marctech IAM environment toward more scalable identity lifecycle automation.
