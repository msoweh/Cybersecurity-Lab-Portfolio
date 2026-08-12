# Lab 02 - AI Application and Prompt Engineering

## Security Policy Summarization & Employee Guidance

**Organization:** MarcTech
**Role:** Junior Cybersecurity Analyst
**AI Assistant:** Google Gemini
**Lab Focus:** Generative AI Application, Prompt Engineering, Human Oversight, Source Fidelity, and Responsible AI Use

---

# Overview

This lab demonstrates the practical application of generative AI to a realistic cybersecurity workplace task.

As a Junior Cybersecurity Analyst at MarcTech, I was tasked with using the organization's approved generative AI assistant, Google Gemini, to assist with transforming a sanitized security policy excerpt into clear, employee-facing security guidance.

The objective was not to allow AI to create, modify, or approve security policy.

Instead, AI was used as an assistance and drafting tool while the analyst remained responsible for reviewing the generated content for accuracy, completeness, security implications, and alignment with the source policy.

The exercise also demonstrates how prompt engineering can improve AI output by progressively introducing relevant context, audience requirements, output constraints, and review instructions.

---

# Real-World Scenario

MarcTech maintains security policies that define expected employee behavior when using company systems and handling security-related situations.

Although these policies are important security controls, employees may have difficulty understanding technical or policy-oriented language.

The cybersecurity team therefore asked a Junior Cybersecurity Analyst to create employee-friendly security guidance from a fictional and sanitized policy excerpt.

The analyst uses Google Gemini as the approved AI assistant for this exercise.

The workflow must ensure that:

* Only fictional and sanitized information is provided to the AI.
* AI does not establish or modify organizational policy.
* Generated content remains faithful to the source policy.
* AI-generated recommendations are reviewed by a human.
* Unsupported or invented requirements are identified.
* Final guidance is reviewed before being considered suitable for employee communication.

---

# Security Policy Source

A fictional MarcTech security policy excerpt was used as the controlled source for this exercise.

## Authentication

* Employees must use MFA when accessing company systems that require it.
* Employees must never approve an unexpected MFA authentication request.
* Suspected MFA compromise must be reported to the IT/Security team.

## Phishing

* Employees must not provide company credentials in response to unsolicited requests.
* Suspicious messages should be reported through the organization's approved reporting process.

## Removable Media

* Employees must not connect unknown or unauthorized removable media to company systems.
* Company-approved removable media must be handled according to organizational security procedures.

## Security Incidents

* Employees must promptly report suspected security incidents.
* Employees should preserve relevant information and avoid attempting unauthorized investigation or remediation.

This fictional policy serves as the source of truth for evaluating AI-generated employee guidance.

---

# Objectives

By completing this lab, I demonstrated the ability to:

1. Apply generative AI to a realistic cybersecurity workplace task.
2. Use role, context, audience, and task-specific prompting.
3. Define output structure and constraints.
4. Iteratively refine prompts based on AI output.
5. Evaluate AI-generated content against a defined source.
6. Identify unsupported, ambiguous, or overly broad statements.
7. Prevent AI from introducing requirements not present in the source policy.
8. Maintain human oversight over AI-generated security content.
9. Apply responsible AI and data-protection considerations.
10. Document AI-assisted work in a reproducible manner.

---

# AI Tool & Environment

**AI Assistant:** Google Gemini

**Purpose:**

* Policy summarization
* Employee guidance creation
* Prompt engineering
* Output refinement
* Human review and validation

AI-generated content was treated as a draft and analytical aid rather than an authoritative source.

The analyst remained responsible for reviewing all generated content and ensuring alignment with the source policy.

---

# Responsible AI & Security Controls

Cybersecurity work may involve sensitive organizational information. AI use must therefore be controlled.

For this lab:

* Only fictional and sanitized information was used.
* No real credentials were provided.
* No personally identifiable information (PII) was provided.
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

# Hands-On Activities

## Activity 1 - Baseline Policy Summarization

### Objective

Establish a baseline AI response before introducing detailed prompting instructions.

A simple prompt was used to determine how the AI initially interpreted and summarized the provided security policy.

### Prompt

```text
Summarize the following MarcTech security policy for employees.

[Insert the fictional MarcTech security policy provided in this lab.]
```

### Skills Demonstrated

* Generative AI application
* Basic prompting
* Baseline output evaluation

### Evidence

[View Screenshot - Baseline Policy Summary](./Screenshots/01-Baseline-Policy-Summary.png)

---

## Activity 2 - Role, Audience & Context Prompting

### Objective

Improve the AI response by explicitly defining the analyst's role, organizational context, target audience, and purpose.

### Prompt

```text
Act as a junior cybersecurity analyst supporting MarcTech.

Using only the fictional security policy provided below, create an employee-facing summary for employees with basic technical knowledge.

The goal is to help employees understand what the policy requires and what actions they should take.

Use plain language and avoid unnecessary cybersecurity jargon.

Do not create new security requirements that are not present in the source policy.

[Insert the fictional MarcTech security policy.]
```

### Skills Demonstrated

* Role prompting
* Context prompting
* Audience specification
* Task definition
* Scope control

### Evidence

[View Screenshot - Role, Audience & Context Prompt](./Screenshots/02-Role-Audience-Context-Prompt.png)

---

## Activity 3 - Structured Output & Security Constraints

### Objective

Use a structured prompt to control the format, scope, tone, and security requirements of the AI-generated employee guidance.

### Prompt

```text
Act as a cybersecurity awareness specialist supporting MarcTech.

Using only the fictional security policy provided below, create an employee-facing security guidance document.

For each policy topic:

1. Identify the security requirement.
2. Explain what it means to an employee in plain language.
3. State what the employee should do.
4. State what the employee should avoid doing.
5. Explain when the employee should contact IT or Security.

Cover the following topics:

- Authentication and MFA
- Phishing
- Removable Media
- Security Incident Reporting

Requirements:

- Use clear headings.
- Use concise bullet points.
- Write for employees with basic technical knowledge.
- Avoid unnecessary technical terminology.
- Do not exaggerate security risks.
- Do not create new security requirements.
- Do not remove or change the meaning of requirements in the source policy.
- If the source policy does not provide enough information to answer something, clearly identify that limitation rather than inventing an answer.

Use only the information contained in the provided policy.

[Insert the fictional MarcTech security policy.]
```

### Skills Demonstrated

* Structured prompting
* Output constraints
* Scope control
* Source fidelity
* Security-aware prompting
* Instruction design

### Evidence

[View Screenshot - Structured Policy Guidance](./Screenshots/03-Structured-Policy-Guidance.png)

---

## Activity 4 - Human Review & Iterative Prompt Refinement

### Objective

Review the AI-generated guidance against the original security policy and identify potential issues before producing a final version.

The analyst evaluated the AI output for:

* Unsupported claims
* Missing policy requirements
* Overly broad statements
* Changed or distorted meaning
* Invented security requirements
* Ambiguous employee instructions
* Excessive technical terminology

### Prompt

```text
Review the previous employee security guidance against the original MarcTech security policy.

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
- Do not claim information has been verified unless it was actually verified.

Original Policy:

[Insert the fictional MarcTech security policy.]
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

[View Screenshot - Human Review & Prompt Refinement](./Screenshots/04-Human-Review-Prompt-Refinement.png)

---

# AI-Assisted Security Workflow

```text
Fictional Security Policy
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

The AI assisted with drafting and information transformation.

The analyst remained responsible for reviewing and validating all generated content.

---

# Prompt Engineering Techniques Demonstrated

| Technique              | Application                                           |
| ---------------------- | ----------------------------------------------------- |
| Role Prompting         | Defined the cybersecurity role the AI should simulate |
| Context Setting        | Provided organizational and business context          |
| Audience Specification | Defined the target audience                           |
| Task Definition        | Explained the desired output                          |
| Output Constraints     | Controlled structure and formatting                   |
| Scope Control          | Prevented expansion beyond source material            |
| Source Grounding       | Kept output aligned with policy requirements          |
| Iterative Refinement   | Improved output through prompt adjustments            |
| Negative Instructions  | Explicitly identified actions the AI must avoid       |
| Human Review           | Analyst reviewed output before acceptance             |

---

# Security Considerations

## AI Is Not the Source of Truth

The fictional MarcTech security policy remained the authoritative source for this exercise.

AI-generated content did not override policy requirements.

## Human Review Is Required

AI-generated cybersecurity content should be reviewed before operational use or employee distribution.

## Prevent Policy Drift

The AI was instructed not to introduce security requirements that were not supported by the source material.

## Protect Sensitive Information

Real credentials, confidential information, customer data, PII, internal security configurations, and other restricted information should not be submitted to an AI system unless explicitly authorized by organizational policy and protected by appropriate controls.

## Use Approved AI Tools

Employees should use only AI services approved by their organization for the intended business purpose.

Organizations should determine which information may be entered into approved AI environments based on security, privacy, compliance, and governance requirements.

---

# Evidence

All screenshots are stored within this lab's dedicated `Screenshots` directory.

| Evidence                                                                                     | Description                                                        |
| -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| [01 - Baseline Policy Summary](./Screenshots/01-Baseline-Policy-Summary.png)                 | Baseline AI response using a simple summarization prompt           |
| [02 - Role, Audience & Context](./Screenshots/02-Role-Audience-Context-Prompt.png)           | AI response after adding role, context, audience, and scope        |
| [03 - Structured Policy Guidance](./Screenshots/03-Structured-Policy-Guidance.png)           | AI response using structured requirements and security constraints |
| [04 - Human Review & Prompt Refinement](./Screenshots/04-Human-Review-Prompt-Refinement.png) | AI-assisted review and refinement of generated content             |

---

# Skills Demonstrated

## Artificial Intelligence

* Generative AI
* Prompt Engineering
* Context Engineering
* AI-Assisted Content Generation
* Iterative Prompting
* AI Output Evaluation

## Cybersecurity

* Security Policy Awareness
* Security Awareness Communication
* Source Validation
* Security Control Interpretation
* Security Risk Awareness
* Data Protection Awareness
* Human-in-the-Loop Security Workflows

## Professional Skills

* Technical Communication
* Requirements Interpretation
* Critical Thinking
* Quality Assurance
* Documentation
* Responsible Technology Use

---

# Outcome

This lab demonstrated how generative AI can be incorporated into a cybersecurity workflow as a productivity and drafting assistant while maintaining appropriate security boundaries and human oversight.

The exercise demonstrated that effective AI use involves more than obtaining an answer from an AI system.

The workflow followed:

**Context → Prompt Design → AI Output → Human Review → Refinement → Validation**

The analyst remained accountable for the accuracy, security, and appropriateness of the resulting employee guidance.

---

# Portfolio Takeaway

> Applied Google Gemini to a controlled cybersecurity documentation workflow using structured prompt engineering, source-constrained generation, iterative refinement, and human review to transform a sanitized security policy into employee-facing guidance without allowing AI to establish or modify security requirements.

---

# Disclaimer

This portfolio lab uses a fictional MarcTech organization and sanitized information for educational and demonstration purposes.

No real organizational credentials, confidential information, customer data, security configurations, or other sensitive information were submitted to the AI system.

In a real-world environment, AI use should follow the organization's approved AI tools, security policies, data-classification requirements, privacy requirements, and applicable regulatory or contractual obligations.
