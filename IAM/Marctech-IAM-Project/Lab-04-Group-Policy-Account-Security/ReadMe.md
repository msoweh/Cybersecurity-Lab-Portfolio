# Lab 4 – Group Policy & Account Security

## Real-World Scenario

Marctech is a growing organization with approximately 250 employees and needs centralized security policies to protect employee accounts and Windows workstations.

As the organization grows, manually configuring password requirements, account lockout settings, and workstation security controls becomes difficult to manage consistently.

The Systems Administrator is responsible for implementing centralized security policies through **Group Policy** so that security requirements can be applied consistently throughout the Marctech Active Directory environment.

---

## Business Objective

The objective of this lab was to implement centralized Windows security controls using **Group Policy**.

The implementation needed to provide:

* Centralized password policy enforcement
* Protection against password reuse
* Strong password requirements
* Account lockout protection
* Consistent workstation security settings
* Centralized policy administration
* A foundation for future security and compliance controls

---

# Lab Environment

| **Component**     | **Configuration**                |
| ----------------- | -------------------------------- |
| Server            | DC01                             |
| Operating System  | Windows Server 2025              |
| Directory Service | Active Directory Domain Services |
| Domain            | `marctech.local`                 |
| Client            | PC01 – Windows 11                |
| Virtualization    | Oracle VirtualBox                |
| Management Tools  | Group Policy Management          |
| Validation Tools  | `gpupdate`, `gpresult`           |

---

# Implementation

## 1. Group Policy Management

The **Group Policy Management** console was used to centrally configure security settings for the Marctech Active Directory environment.

Group Policy allows administrators to define and enforce configuration and security settings across domain users and computers.

This provides a centralized approach rather than manually configuring each workstation individually.

---

## 2. Password Policy

The **Default Domain Policy** was configured to establish centralized password security requirements for the Marctech domain.

The password policy included:

| Setting                                     |           Configuration |
| ------------------------------------------- | ----------------------: |
| Enforce password history                    | 24 passwords remembered |
| Minimum password age                        |                   1 day |
| Maximum password age                        |                 90 days |
| Minimum password length                     |           14 characters |
| Password complexity requirements            |                 Enabled |
| Store passwords using reversible encryption |                Disabled |

These settings were designed to reduce the risk associated with weak passwords and repeated password reuse.

### Password History

The domain was configured to remember the previous **24 passwords**.

This helps prevent users from repeatedly changing their password and then returning to a previously used password.

### Minimum Password Age

The minimum password age was configured to **1 day**.

This helps prevent users from rapidly changing their password multiple times in an attempt to bypass the password-history requirement.

### Maximum Password Age

The maximum password age was configured to **90 days**.

This establishes a centralized password-expiration requirement for the domain.

### Minimum Password Length

The minimum password length was configured to **14 characters**.

Longer passwords generally provide stronger resistance against password-guessing attacks.

### Password Complexity

Password complexity requirements were enabled to require stronger password construction.

### Reversible Encryption

Reversible encryption was disabled.

Passwords should not be stored using reversible encryption unless a specific legacy requirement exists.

---

## 3. Account Lockout Policy

Account lockout settings were configured as part of the domain security policy.

The configuration included:

| Setting                             |      Configuration |
| ----------------------------------- | -----------------: |
| Account lockout threshold           | 5 invalid attempts |
| Account lockout duration            |         30 minutes |
| Reset account lockout counter after |         30 minutes |

These settings provide protection against repeated unsuccessful authentication attempts.

### Account Lockout Threshold

The account was configured to lock after **5 invalid login attempts**.

This helps reduce the effectiveness of repeated password-guessing attempts.

### Account Lockout Duration

A locked account remains locked for **30 minutes**.

### Reset Lockout Counter

The failed-attempt counter resets after **30 minutes** without additional failed attempts.

---

## 4. Workstation Security Policy

A separate **WorkStation Security Policy** Group Policy Object was configured to provide an additional workstation security control.

The policy included:

* Screen saver enabled
* Screen saver password protection enabled
* Screen saver timeout configured to 600 seconds

The policy was linked to the `marctech.local` domain.

This configuration helps reduce the risk of unauthorized access when a user leaves a workstation unattended.

---

## 5. Group Policy Application

After configuring the policies, the client environment was updated so that the domain policies could be applied.

The Group Policy update process was initiated using:

```text
gpupdate /force
```

This forces the computer and user Group Policy settings to refresh.

---

# Validation & Testing

After configuring the Group Policy settings, the policies were validated from the Windows client environment.

## Group Policy Update

The following command was used:

```text
gpupdate /force
```

The command forces the workstation to retrieve and apply available Group Policy settings.

---

## Group Policy Result Verification

The resulting policy configuration was reviewed using:

```text
gpresult /r
```

The output was used to verify that the expected policies were being applied.

The validation confirmed the presence of:

```text
Default Domain Policy
WorkStation Security Policy
```

This demonstrated that the client was receiving the expected domain-level security policies.

---

## Password Policy Validation

The password policy settings were reviewed to verify that the configured requirements were being enforced centrally.

The validation focused on:

* Password history
* Password age
* Password length
* Complexity requirements
* Account lockout settings

---

## Workstation Security Validation

The workstation security configuration was reviewed to verify that:

* Screen saver functionality was enabled.
* Password protection was enabled.
* The configured timeout was 600 seconds.

---

# Security Relevance

Group Policy is an important security control in Windows enterprise environments.

Instead of configuring every workstation independently, security administrators can establish centralized policies that are applied throughout the domain.

This provides:

**Centralized Policy → Consistent Configuration → Reduced Security Risk**

The password and account lockout policies implemented in this lab help protect against:

* Weak passwords
* Password reuse
* Password guessing
* Repeated authentication attempts
* Unauthorized access

The workstation policy adds another layer of protection by requiring password protection after a period of inactivity.

Group Policy therefore provides an important connection between **Active Directory administration and cybersecurity controls**.

---

# Troubleshooting

## Password Policy Compatibility

During password-policy configuration, attention was given to the interaction between password length requirements and existing domain security settings.

Changing password-policy requirements can affect user provisioning and password-reset operations because newly supplied passwords must satisfy the domain's configured requirements.

### Lesson Learned

Password policies should be tested carefully after modification.

When troubleshooting account-creation or password-reset issues, administrators should verify:

* Minimum password length
* Complexity requirements
* Password history
* Minimum password age
* Account lockout status

---

## Group Policy Application

After making Group Policy changes, the policy does not necessarily appear immediately on the client.

The following command was used to force a policy refresh:

```text
gpupdate /force
```

The resulting configuration was then verified using:

```text
gpresult /r
```

### Lesson Learned

When troubleshooting Group Policy, administrators should distinguish between:

**Policy Configuration**

and

**Policy Application**

A policy can be correctly configured in Group Policy Management but still require a refresh and validation on the client.

---

# Skills Demonstrated

* Group Policy Management
* Active Directory security administration
* Password policy configuration
* Password history enforcement
* Password complexity
* Account lockout policy
* Workstation security
* Screen saver security
* Domain policy administration
* Group Policy troubleshooting
* `gpupdate`
* `gpresult`
* Windows security configuration
* IAM security controls
* Least-privilege and account-security concepts

---

# Evidence

The following screenshots provide implementation and validation evidence from the Marctech Group Policy and Account Security lab environment.

## 1. Group Policy Management

[View Group Policy Management Evidence](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/blob/main/IAM/Marctech-IAM-Project/Lab-04-Group-Policy-Account-Security/Screenshots/01-Group-Policy-Management.png)

This screenshot shows the Group Policy Management environment used to administer centralized security policies for the Marctech domain.

---

## 2. Password Policy

[View Password Policy Evidence](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/blob/main/IAM/Marctech-IAM-Project/Lab-04-Group-Policy-Account-Security/Screenshots/02-Password-Policy.png)

This screenshot provides evidence of the centralized password security requirements configured for the Marctech domain.

---

## 3. Account Lockout Policy

[View Account Lockout Evidence](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/blob/main/IAM/Marctech-IAM-Project/Lab-04-Group-Policy-Account-Security/Screenshots/03-Account-Lockout-Policy.png))

This screenshot provides evidence of the account lockout controls configured to protect against repeated unsuccessful authentication attempts.

---

## 4. Workstation Security Policy

[View Workstation Security Evidence](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/blob/main/IAM/Marctech-IAM-Project/Lab-04-Group-Policy-Account-Security/Screenshots/04-Workstation-Security-Policy.png)

This screenshot provides evidence of the workstation security policy, including screen saver and password-protection settings.

---

## 5. Group Policy Update

[View Group Policy Update Evidence](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/blob/main/IAM/Marctech-IAM-Project/Lab-04-Group-Policy-Account-Security/Screenshots/05-GPUpdate-Application.png)

This screenshot shows the execution of:

```text
gpupdate /force
```

demonstrating that the client was instructed to refresh its Group Policy configuration.

---

## 6. Applied Group Policy Results

[View Group Policy Results Evidence](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/blob/main/IAM/Marctech-IAM-Project/Lab-04-Group-Policy-Account-Security/Screenshots/06-GPResult-Validation.png)

This screenshot shows the output of:

```text
gpresult /r
```

and provides validation that the expected policies were applied to the client.

Evidence note: This screenshot was captured during a subsequent validation pass of the completed lab environment. It supplements the original implementation evidence by demonstrating client-side Group Policy verification.

---

> **Security note:** Screenshots published in this portfolio are limited to the fictional Marctech lab environment. Sensitive credentials, passwords, personal information, and unnecessary private network information are not published.

---

# Key Takeaway

This lab demonstrated how **Group Policy can be used to centrally enforce Windows security requirements across an Active Directory environment**.

The implementation established centralized controls for:

```text
Password Security
       ↓
Account Lockout
       ↓
Workstation Security
       ↓
Centralized Policy Enforcement
       ↓
Validation & Monitoring
```

The lab also demonstrated an important cybersecurity administration principle:

> **Security policies are only effective when they are both configured correctly and validated on the systems to which they apply.**

The Marctech environment can now use Group Policy as a foundation for additional security controls, including more advanced workstation policies, administrative controls, auditing, and enterprise security management.
