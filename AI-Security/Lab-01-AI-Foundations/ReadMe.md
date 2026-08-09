# Lab 01 - AI Foundations: Applying Generative AI to MFA Security Analysis

## Overview

This lab demonstrates the practical application of **generative AI in a cybersecurity workflow** involving Multi-Factor Authentication (MFA).

A realistic security scenario was used to explore how an analyst can use AI to explain security concepts, adapt technical information to different audiences, perform initial security analysis, and assist with technical documentation.

The lab also demonstrates an important responsible-AI practice: **AI-generated cybersecurity information was not treated as authoritative without verification.** Selected claims were evaluated against authoritative guidance from the **Cybersecurity and Infrastructure Security Agency (CISA)** and the **National Institute of Standards and Technology (NIST)**.

---

## Real-World Scenario

**Organization:** MarcTech
**Role:** Security Analyst / IAM Analyst
**Security Domain:** Identity & Access Management
**Security Topic:** Multi-Factor Authentication (MFA)

MarcTech is strengthening its identity security controls by requiring MFA for workforce access.

As part of the security team's work, an analyst may need to:

* Explain MFA to nontechnical employees.
* Support employees experiencing MFA-related issues.
* Analyze the security benefits and limitations of MFA.
* Identify common techniques that can weaken or bypass MFA.
* Use generative AI to accelerate research and documentation.
* Validate AI-generated security information before using it professionally.

---

## Objectives

By completing this lab, I demonstrated the ability to:

* Apply generative AI to a cybersecurity use case.
* Use prompts to obtain and refine security-related information.
* Provide role, organizational, and technical context to AI.
* Adapt AI-generated content for different audiences.
* Use AI to assist with cybersecurity analysis.
* Identify limitations and potentially inaccurate AI-generated claims.
* Validate AI-generated claims against authoritative sources.
* Refine AI-generated statements for technical accuracy.
* Distinguish supported information from claims requiring additional verification.
* Apply responsible AI practices when using AI for cybersecurity work.

---

## Skills Demonstrated

| Skill                   | Application                                                        |
| ----------------------- | ------------------------------------------------------------------ |
| Generative AI           | Generated cybersecurity explanations and analysis                  |
| Prompt Engineering      | Provided structured security and role-based context                |
| Contextual Prompting    | Adapted AI responses for employees and IT/security personnel       |
| Iterative Refinement    | Progressively increased the depth of the AI analysis               |
| Critical Evaluation     | Identified overly broad or absolute AI-generated claims            |
| Source Validation       | Compared AI output against CISA and NIST guidance                  |
| Responsible AI          | Treated AI output as assistance rather than authoritative evidence |
| Technical Documentation | Documented security findings and validation results                |

---

# Hands-On Activities

## Activity 1 — AI-Assisted MFA Explanation

### Objective

Use generative AI to explain a cybersecurity concept clearly to a nontechnical audience.

### Scenario

MarcTech is introducing mandatory MFA to protect employee accounts and company information. Employees need a simple explanation of what MFA is, why it is required, and what they can expect during authentication.

### AI Application

The AI was used to explain:

* What MFA is.
* The three major authentication factor categories.
* Why MarcTech requires MFA.
* How MFA affects employees during normal authentication.

### Result

The AI produced a business-friendly explanation using familiar examples while introducing the fundamental concepts behind MFA.

### Evidence

[View Screenshot - MFA Basic Prompt](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/tree/main/AI-Security/Lab-01-AI-Foundations/01-AI-Foundations-Basic-Prompt.png)

---

## Activity 2 — Contextual AI Application for IT Support

### Objective

Evaluate how additional role and organizational context affects the usefulness of AI-generated output.

### Scenario

The analyst was placed in the role of an entry-level IT support technician assisting MarcTech employees with MFA-related access problems.

### AI Application

The AI was asked to provide:

* MFA fundamentals.
* Authentication factors.
* Common MFA methods.
* Common MFA helpdesk scenarios.
* Troubleshooting considerations.
* Security precautions for MFA resets.

### Security Scenarios Identified

The AI identified several realistic support and security situations, including:

* New phone or lost MFA registration.
* Invalid TOTP codes.
* MFA fatigue / push-bombing.
* Travel-related authentication challenges.
* Identity verification before MFA resets.

### Result

Providing the organizational and job-role context produced a more operationally relevant response than the general MFA explanation.

### Evidence

[View Screenshot - Contextual MFA Exercise](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/tree/main/AI-Security/Lab-01-AI-Foundations/02-AI-Foundations-MFA-Context-Experiment.png)

---

# Activity 3 — AI-Assisted MFA Security Assessment

### Objective

Use generative AI to analyze both the security benefits and limitations of MFA without assuming that MFA completely secures an account.

### AI Application

The AI was instructed to act as a senior cybersecurity analyst reviewing MarcTech's MFA security posture.

The assessment considered:

* Security benefits of MFA.
* MFA limitations.
* Adversary-in-the-Middle (AiTM) attacks.
* MFA fatigue / push bombing.
* SIM swapping.
* Session and token theft.
* OAuth consent attacks.
* Phishing-resistant MFA.
* Conditional Access.
* Legacy authentication.
* Session management.

### Key Observation

The AI correctly presented MFA as an important layer of defense rather than a standalone security solution.

The exercise also demonstrated the need for human review because some AI-generated statements used language that was broader or stronger than the authoritative evidence supported.

### Evidence

[View Screenshot - MFA Security Assessment](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/tree/main/AI-Security/Lab-01-AI-Foundations/03-AI-Foundations-Security-Assessment.png)

---

# Activity 4 — AI Output Validation

## Objective

Validate selected AI-generated cybersecurity claims against authoritative security guidance.

The validation workflow was:

**AI-generated claim → authoritative source → analyst assessment → refined statement**

Two claims were selected from the MFA security assessment for verification.

### Evidence

[View Screenshot - AI Output Validation](https://github.com/msoweh/Cybersecurity-Lab-Portfolio/tree/main/AI-Security/Lab-01-AI-Foundations/04-AI-Foundations-MFA-Output-Validation.png)

---

## Claim 1 — MFA and Password-Based Attacks

### AI-Generated Claim

> "MFA neutralizes credential stuffing, brute-force dictionary attacks, and password spraying."

### Authoritative Source

**CISA — Multi-Factor Authentication (MFA) guidance**

CISA states that MFA **mitigates common attacks against passwords such as brute-force guessing and credential stuffing** by requiring another factor in addition to the password.

CISA also explains that, unless an attacker can defeat the MFA authentication mechanism, knowing the password alone does not enable impersonation of the user.

### Assessment

⚠️ **PARTIALLY SUPPORTED — LANGUAGE TOO ABSOLUTE**

### Analyst Finding

The underlying security concept is supported by CISA.

However, the term **"neutralizes"** is too absolute. CISA describes MFA as **mitigating** common password attacks rather than eliminating them.

The specific CISA passage reviewed also does not explicitly identify password spraying. Therefore, that portion of the AI-generated claim requires separate verification rather than being treated as validated by this source.

### Refined Statement

> MFA can mitigate common password-based attacks such as brute-force guessing and credential stuffing by requiring an additional authentication factor. MFA reduces the risk associated with compromised passwords but does not eliminate password-based attacks.

### Validation Result

**The underlying security concept was supported, but the AI-generated wording was qualified for accuracy and technical precision.**

---

## Claim 2 — Phishing-Resistant MFA

### AI-Generated Claim

> "FIDO2 / WebAuthn hardware keys and Passkeys are the gold standard for phishing-resistant authentication."

### Authoritative Source

**NIST SP 800-63B-4 — Authentication and Authenticator Management**

NIST identifies **WebAuthn**, which is used by authenticators implementing **FIDO2 specifications**, as an example of a standard that provides phishing resistance through **verifier name binding**.

### Assessment

✅ **SUPPORTED WITH QUALIFICATION**

### Analyst Finding

NIST directly supports the core technical concept that WebAuthn/FIDO2 can provide phishing-resistant authentication.

However, the phrase **"gold standard"** is not precise technical terminology established by the cited NIST guidance.

The statement was therefore refined to use terminology directly supported by the authoritative source.

### Refined Statement

> WebAuthn, used by authenticators implementing FIDO2 specifications, provides phishing-resistant authentication through verifier name binding.

### Validation Result

**The underlying technical claim was supported, while the AI-generated terminology was refined for technical precision.**

---

# Validation Methodology

The validation process followed these steps:

1. Identify a specific security claim generated by AI.
2. Locate an authoritative cybersecurity source.
3. Compare the source evidence against the AI-generated claim.
4. Determine whether the claim was supported, partially supported, or required qualification.
5. Identify overly broad or unsupported language.
6. Produce a technically refined statement.
7. Document the source and reasoning used for validation.

This demonstrates that AI output was treated as **assistance rather than authority**.

---
# Security & Responsible AI Considerations

When using generative AI in a professional cybersecurity environment,
security and organizational data-handling requirements must remain a
priority.

### Sensitive Information

Do not enter confidential, sensitive, proprietary, regulated, or
otherwise restricted organizational information into a public or
unapproved AI service.

Examples of information that should not be entered without explicit
authorization include:

- Passwords, API keys, access tokens, or authentication secrets.
- Personally identifiable information (PII).
- Customer or employee records.
- Confidential business information.
- Security incident details.
- Internal network configurations or sensitive architecture diagrams.
- Proprietary source code or intellectual property.
- Regulated or contractually restricted information.

### Organizational Policy

Before using generative AI for work-related activities, the analyst
should verify the organization's:

- Acceptable Use Policy.
- AI/Generative AI Policy.
- Data Classification Policy.
- Data Loss Prevention (DLP) requirements.
- Privacy and regulatory requirements.
- Approved AI tools and services.
- Third-party data-sharing requirements.

**AI tools should only be used with organizational information when
the organization has explicitly authorized the tool and the intended
use case.**

When authorization or policy requirements are unclear, the analyst
should consult the appropriate security, privacy, legal, compliance,
or management team before submitting organizational information to
an AI service.

### Lab Practice

For this lab, AI interactions were limited to **non-sensitive,
simulated MarcTech information and cybersecurity concepts**.

No real organizational credentials, secrets, PII, confidential
business information, or production security data were used.

### Responsible AI Principle

> **Never assume that information is safe to provide to an AI system
> simply because the information appears useful for the task. Verify
> the organization's policies, data-handling requirements, and approved
> AI services before using AI with organizational information.**

# Evidence

The following evidence files document the hands-on AI workflow:

| Evidence                                                                                                           | Description                                                                   |
| ------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------- |
| [01 — MFA Basic Prompt](../Screenshots/Lab-01-AI-Foundations/01-AI-Foundations-MFA-Basic-Prompt.png)               | AI-generated explanation of MFA for a nontechnical audience                   |
| [02 — Context Experiment](../Screenshots/Lab-01-AI-Foundations/02-AI-Foundations-MFA-Context-Experiment.png)       | AI applied to an IT support/security scenario                                 |
| [03 — MFA Security Assessment](../Screenshots/Lab-01-AI-Foundations/03-AI-Foundations-MFA-Security-Assessment.png) | AI-assisted analysis of MFA benefits, limitations, and attack techniques      |
| [04 — AI Output Validation](../Screenshots/Lab-01-AI-Foundations/04-AI-Foundations-MFA-Output-Validation.png)      | Human validation of AI-generated security claims using CISA and NIST guidance |

---

# Authoritative References

* [CISA — Multi-Factor Authentication (MFA)](https://www.nsa.gov/Press-Room/Press-Releases-Statements/Press-Release-View/Article/3336001/esf-partners-nsa-and-cisa-release-identity-and-access-management-recommended-be/)
* [NIST SP 800-63B-4 — Authentication and Authenticator Management](https://pages.nist.gov/800-63-4/sp800-63b/authenticators/)

---

# Key Takeaways

This lab demonstrated how generative AI can be incorporated into a cybersecurity workflow to assist with:

* Security education.
* Technical analysis.
* Research and information synthesis.
* Security documentation.
* Initial identification of security risks.

The validation exercise demonstrated an equally important principle:

> **AI-generated cybersecurity information should be critically evaluated and validated before being treated as authoritative.**

The primary outcome of this lab was not simply generating AI responses. It was demonstrating the ability to combine:

**Generative AI + cybersecurity knowledge + authoritative sources + human judgment**

to produce more accurate and defensible security analysis.
