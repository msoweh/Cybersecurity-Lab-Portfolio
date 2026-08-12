
# Lab 02 - AI Application and Prompt Engineering

## Security Policy Summarization & Employee Guidance

**Organization:** MarcTech
**Role:** Junior Cybersecurity Analyst
**AI Assistant:** Google Gemini
**Lab Focus:** Generative AI application, prompt engineering, source grounding, human oversight, and responsible AI use

---

# 1. Overview

This lab demonstrates the practical application of generative AI to a realistic cybersecurity workplace task.

As a Junior Cybersecurity Analyst at MarcTech, I was asked to use the organization's approved generative AI assistant, Google Gemini, to assist with transforming a sanitized security policy into clear, employee-facing security guidance.

The objective was not to allow AI to create, modify, or approve security policy.

Instead, AI was used as an assistance and drafting tool while the analyst remained responsible for reviewing the generated content for accuracy, completeness, security implications, and alignment with the source policy.

The exercise also demonstrates how prompt engineering can improve AI output by progressively introducing relevant context, audience requirements, output constraints, and review instructions.

---

# 2. Real-World Scenario

MarcTech maintains security policies that define expected employee behavior when using company systems and handling security-related situations.

Although these policies are important security controls, employees may have difficulty understanding technical or policy-oriented language.

The cybersecurity team therefore asked a Junior Cybersecurity Analyst to create employee-friendly security guidance from a fictional and sanitized policy excerpt.

The analyst uses **Google Gemini as the approved AI assistant** for this exercise.

The workflow must ensure that:

* Only fictional and sanitized information is provided to the AI.
* AI does not establish or modify organizational policy.
* Generated content remains faithful to the source policy.
* AI-generated content is reviewed by a human.
* Unsupported or invented requirements are identified.
* Final guidance is reviewed before being considered suitable for employee communication.

---

# 3. Controlled Security Policy Source

The following fictional MarcTech security policy is the **controlled source for all activities in this lab**.

AI-generated outputs will be evaluated against this source to determine whether requirements were:

* Preserved
* Omitted
* Changed
* Misrepresented
* Newly introduced by the AI

Using a consistent source allows the analyst to evaluate whether prompt changes improve the quality and reliability of AI-generated output.

---

## MarcTech Security Policy - Employee Security Practices

### Authentication

* Employees must use MFA when accessing company systems that require it.
* Employees must never approve an unexpected MFA authentication request.
* Suspected MFA compromise must be reported to the IT/Security team.

### Phishing

* Employees must not provide company credentials in response to unsolicited requests.
* Suspicious messages should be reported through the organization's approved reporting process.

### Removable Media

* Employees must not connect unknown or unauthorized removable media to company systems.
* Company-approved removable media must be handled according to organizational security procedures.

### Security Incidents

* Employees must promptly report suspected security incidents.
* Employees should preserve relevant information and avoid attempting unauthorized investigation or remediation.

---

## Source Control

For consistency, the same policy source is used throughout the four activities.

No real MarcTech information is used.

This fictional policy exists solely for educational and portfolio demonstration purposes.

---

# 4. AI Tool & Environment

**AI Assistant:** Google Gemini

**Primary Use:**

* Policy summarization
* Employee guidance drafting
* Prompt experimentation
* Output refinement
* AI-assisted review

Google Gemini was used as the AI assistant for this exercise.

AI-generated content was treated as a draft and analytical aid rather than an authoritative source.

The analyst remained responsible for reviewing the output and determining whether it accurately represented the source policy.

---

# 5. Responsible AI & Security Boundaries

Cybersecurity work may involve sensitive organizational information. AI use must therefore be controlled.

For this lab:

* Only fictional and sanitized information was used.
* No real credentials were provided.
* No personally identifiable information was provided.
* No customer information was provided.
* No confidential organizational information was provided.
* No real security logs were provided.
* No internal network information was provided.
* No proprietary source code was provided.

## Real-World AI Use Requirement

In a real organization, employees should use only AI tools approved by their organization and follow applicable:

* AI acceptable-use policies
* Data-classification requirements
* Privacy requirements
* Security requirements
* Regulatory requirements
* Contractual requirements
* Data-retention requirements

Employees should not independently move sensitive organizational information between different AI services simply because another service produces a preferred response.

AI tool selection and permitted use should be determined by organizational policy and security governance.

---

# 6. Objectives

By completing this lab, I will demonstrate the ability to:

1. Apply generative AI to a realistic cybersecurity workplace task.
2. Use role, context, audience, and task-specific prompting.
3. Define output structure and constraints.
4. Iteratively refine prompts based on AI output.
5. Evaluate AI-generated content against a defined source.
6. Identify unsupported, ambiguous, or overly broad statements.
7. Detect when AI introduces requirements not present in the source policy.
8. Maintain human oversight over AI-generated security content.
9. Apply responsible AI and data-protection considerations.
10. Document AI-assisted work in a reproducible manner.

---

# 7. Hands-On Activities

## Activity 1 - Baseline Policy Summarization

### Objective

Establish a baseline AI response before introducing detailed prompting instructions.

A simple prompt is used to determine how Gemini initially interprets and summarizes the controlled MarcTech security policy.

### Prompt Used

```text
Summarize the following MarcTech security policy for employees.

MarcTech Security Policy - Employee Security Practices

Authentication:
- Employees must use MFA when accessing company systems that require it.
- Employees must never approve an unexpected MFA authentication request.
- Suspected MFA compromise must be reported to the IT/Security team.

Phishing:
- Employees must not provide company credentials in response to unsolicited requests.
- Suspicious messages should be reported through the organization's approved reporting process.

Removable Media:
- Employees must not connect unknown or unauthorized removable media to company systems.
- Company-approved removable media must be handled according to organizational security procedures.

Security Incidents:
- Employees must promptly report suspected security incidents.
- Employees should preserve relevant information and avoid attempting unauthorized investigation or remediation.
```

### Skills Demonstrated

* Generative AI application
* Basic prompting
* Baseline output evaluation
* Source-grounded summarization

### Evidence

[**View Screenshot - Baseline Policy Summary**](./Screenshots/01-Baseline-Policy-Summary.png)

---

## Activity 2 - Role, Audience & Context Prompting

### Objective

Improve the AI response by explicitly defining the analyst's role, organizational context, target audience, and purpose.

The same controlled MarcTech security policy will be provided to Gemini.

### Prompt Used

```text
Act as a junior cybersecurity analyst supporting MarcTech.

Using only the fictional security policy provided below, create an employee-facing summary for employees with basic technical knowledge.

The goal is to help employees understand what the policy requires and what actions they should take.

Use plain language and avoid unnecessary cybersecurity jargon.

Do not create new security requirements that are not present in the source policy.

Use only the following controlled MarcTech security policy:

MarcTech Security Policy - Employee Security Practices

Authentication:
- Employees must use MFA when accessing company systems that require it.
- Employees must never approve an unexpected MFA authentication request.
- Suspected MFA compromise must be reported to the IT/Security team.

Phishing:
- Employees must not provide company credentials in response to unsolicited requests.
- Suspicious messages should be reported through the organization's approved reporting process.

Removable Media:
- Employees must not connect unknown or unauthorized removable media to company systems.
- Company-approved removable media must be handled according to organizational security procedures.

Security Incidents:
- Employees must promptly report suspected security incidents.
- Employees should preserve relevant information and avoid attempting unauthorized investigation or remediation.
```

### Skills Demonstrated

* Role prompting
* Context prompting
* Audience specification
* Task definition
* Scope control
* Source grounding

### Evidence

[**View Screenshot - Role, Audience & Context Prompt**](./Screenshots/02-Role-Audience-Context-Prompt.png)

---

## Activity 3 - Structured Output & Security Constraints

### Objective

Use a structured prompt to control the format, scope, tone, and security requirements of the AI-generated employee guidance.

The controlled MarcTech policy remains the source of truth.

### Prompt Used

```text
Act as a cybersecurity awareness specialist supporting MarcTech.

Using only the controlled MarcTech security policy provided below, create an employee-facing security guidance document.

For each policy topic:

1. Identify the security requirement.
2. Explain what it means to an employee in plain language.
3. State what the employee should do.
4. State what the employee should avoid doing.
5. Explain when the employee should contact IT or Security.

Cover the following topics:

- Authentication and MFA
- Phishing
- Removable media
- Security incident reporting

Requirements:

- Use clear headings.
- Use concise bullet points.
- Write for employees with basic technical knowledge.
- Avoid unnecessary technical terminology.
- Do not exaggerate security risks.
- Do not create new security requirements.
- Do not remove or change the meaning of requirements in the source policy.
- If the source policy does not provide enough information to answer something, clearly identify that limitation rather than inventing an answer.
- Use only the information contained in the controlled policy.

Controlled MarcTech Security Policy:

Authentication:
- Employees must use MFA when accessing company systems that require it.
- Employees must never approve an unexpected MFA authentication request.
- Suspected MFA compromise must be reported to the IT/Security team.

Phishing:
- Employees must not provide company credentials in response to unsolicited requests.
- Suspicious messages should be reported through the organization's approved reporting process.

Removable Media:
- Employees must not connect unknown or unauthorized removable media to company systems.
- Company-approved removable media must be handled according to organizational security procedures.

Security Incidents:
- Employees must promptly report suspected security incidents.
- Employees should preserve relevant information and avoid attempting unauthorized investigation or remediation.
```

### Skills Demonstrated

* Structured prompting
* Output constraints
* Scope control
* Source fidelity
* Source grounding
* Security-aware prompting
* Instruction design

### Evidence

[**View Screenshot - Structured Policy Guidance**](./Screenshots/03-Structured-Policy-Guidance.png)

---

## Activity 4 - Human Review & Iterative Prompt Refinement

### Objective

Review the AI-generated guidance against the controlled MarcTech security policy and identify potential problems before producing the final version.

The analyst evaluates the AI output for:

* Unsupported claims
* Missing policy requirements
* Overly broad statements
* Changed or distorted meaning
* Invented security requirements
* Ambiguous employee instructions
* Excessive technical terminology

### Prompt Used

```text
Review the previous employee security guidance against the controlled MarcTech security policy.

Identify:

1. Any statements that are unsupported by the source policy.
2. Any policy requirements that were omitted.
3. Any statements that changed or broadened the original meaning.
4. Any newly introduced security requirements.
5. Any instructions that could be misunderstood by employees.
6. Any terminology that is unnecessarily technical.

For each issue, explain why it should be corrected.

Then produce a revised employee guidance document.

Requirements for the revised version:

- Remain faithful to the original policy.
- Do not introduce new security requirements.
- Do not remove required security actions.
- Use clear employee-friendly language.
- Clearly identify information that cannot be determined from the source policy.
- Do not claim that information has been verified unless it was actually verified.

Controlled MarcTech Security Policy:

Authentication:
- Employees must use MFA when accessing company systems that require it.
- Employees must never approve an unexpected MFA authentication request.
- Suspected MFA compromise must be reported to the IT/Security team.

Phishing:
- Employees must not provide company credentials in response to unsolicited requests.
- Suspicious messages should be reported through the organization's approved reporting process.

Removable Media:
- Employees must not connect unknown or unauthorized removable media to company systems.
- Company-approved removable media must be handled according to organizational security procedures.

Security Incidents:
- Employees must promptly report suspected security incidents.
- Employees should preserve relevant information and avoid attempting unauthorized investigation or remediation.
```

### Skills Demonstrated

* Iterative prompt engineering
* Human-in-the-loop review
* AI output evaluation
* Unsupported-claim detection
* Source validation
* Security content review
* Prompt refinement

### Evidence

[**View Screenshot - Human Review & Prompt Refinement**](./Screenshots/04-Human-Review-Prompt-Refinement.png)

---

# 8. AI-Assisted Security Workflow

```text
Controlled MarcTech Security Policy
              |
              v
      Approved AI Assistant
          Google Gemini
              |
              v
       Baseline Prompt
              |
              v
       AI-Generated Draft
              |
              v
    Role + Context + Audience
              |
              v
    Structured Requirements
              |
              v
      AI-Generated Guidance
              |
              v
         Human Review
              |
              v
       Prompt Refinement
              |
              v
    Policy-to-Output Verification
              |
              v
    Reviewed Employee Guidance
```

The AI assists with drafting and transformation of information.

The controlled security policy remains the source of truth.

The analyst remains responsible for reviewing the output.

---

# 9. Prompt Engineering Techniques Demonstrated

| Technique              | Application                                                      |
| ---------------------- | ---------------------------------------------------------------- |
| Role prompting         | Defines the cybersecurity role the AI should simulate            |
| Context setting        | Provides the organizational and business context                 |
| Audience specification | Defines who will consume the final output                        |
| Task definition        | Clearly explains what the AI must produce                        |
| Output constraints     | Controls structure, length, and formatting                       |
| Scope control          | Prevents the AI from expanding beyond the source                 |
| Source grounding       | Requires the output to remain aligned with the controlled policy |
| Iterative refinement   | Uses review findings to improve the next prompt                  |
| Negative instructions  | Explicitly identifies actions the AI must avoid                  |
| Human review           | Analyst evaluates AI output before acceptance                    |

---

# 10. Security Considerations

## AI Is Not the Source of Truth

The controlled MarcTech security policy remains the authoritative source for this exercise.

AI-generated content must not override the source policy.

## Human Review Is Required

AI-generated cybersecurity content should be reviewed before being used operationally or distributed to employees.

## Prevent Policy Drift

The AI must not introduce new security requirements that are not supported by the source material.

## Protect Sensitive Information

Real credentials, confidential information, PII, customer data, internal security configurations, or other restricted information should not be submitted to an AI system unless explicitly authorized by organizational policy and appropriate security controls.

## Use Approved AI Tools

Employees should use only AI services approved by their organization for the specific business use case.

The organization should determine which information may be entered into the approved AI environment based on its security, privacy, and data-governance requirements.

---

# 11. Evidence

All screenshots are stored in the lab's dedicated `Screenshots` directory.

| Evidence                                                                                     | Description                                                                           |
| -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| [01 - Baseline Policy Summary](./Screenshots/01-Baseline-Policy-Summary.png)                 | Baseline Gemini response using the controlled policy and a basic summarization prompt |
| [02 - Role, Audience & Context](./Screenshots/02-Role-Audience-Context-Prompt.png)           | Gemini response after adding role, context, audience, and scope                       |
| [03 - Structured Policy Guidance](./Screenshots/03-Structured-Policy-Guidance.png)           | Gemini response using structured output requirements and security constraints         |
| [04 - Human Review & Prompt Refinement](./Screenshots/04-Human-Review-Prompt-Refinement.png) | AI-assisted review and iterative prompt refinement                                    |

---

# 12. Skills Demonstrated

## Artificial Intelligence

* Generative AI
* Prompt engineering
* Context engineering
* Source grounding
* AI-assisted content generation
* Iterative prompting
* AI output evaluation

## Cybersecurity

* Security policy awareness
* Security awareness communication
* Source validation
* Security control interpretation
* Security risk awareness
* Data protection awareness
* Human-in-the-loop security workflows

## Professional Skills

* Technical communication
* Requirements interpretation
* Critical thinking
* Quality assurance
* Documentation
* Responsible technology use

---

# 13. Outcome

This lab demonstrates how generative AI can be incorporated into a cybersecurity workflow as a productivity and drafting assistant while maintaining appropriate security boundaries and human oversight.

The exercise demonstrates that effective AI use involves more than obtaining an answer from an AI system.

The workflow is:

**Controlled Source → Context → Prompt Design → AI Output → Human Review → Refinement → Validation**

The analyst remains accountable for the accuracy, security, and appropriateness of the resulting employee guidance.

---

# 14. Portfolio Takeaway

> **Applied Google Gemini to a controlled cybersecurity documentation workflow using source grounding, structured prompt engineering, iterative refinement, and human review to transform a fictional security policy into employee-facing guidance without allowing AI to establish or modify security requirements.**

---

## Disclaimer

This portfolio lab uses a fictional MarcTech organization and sanitized information for educational and demonstration purposes.

No real organizational credentials, confidential information, customer data, security configurations, or other sensitive information were submitted to the AI system.

In a real-world environment, AI use should follow the organization's approved AI tools, security policies, data-classification requirements, privacy requirements, and applicable regulatory or contractual obligations.

