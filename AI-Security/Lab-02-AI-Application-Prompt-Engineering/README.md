# Lab 02 — AI Application & Prompt Engineering

**Project:** AI-Security  
**Organization:** Marctech *(fictional organization)*  
**Role Context:** Cybersecurity / IT Security Analyst  
**AI Tool:** Google Gemini  
**Focus:** AI-assisted security policy analysis, prompt engineering, output validation, and human-in-the-loop review

---

## 1. Lab Overview

### Scenario

Marctech is developing employee security awareness guidance based on its internal security policy.

As a cybersecurity analyst, I was tasked with using generative AI to assist with transforming a controlled security policy into clear employee-facing guidance.

The objective was not simply to generate text with AI, but to evaluate how **prompt design, constraints, source grounding, and human review** affect the quality and security of AI-generated content.

The exercise followed a progressive workflow:

> **Baseline Prompt → Context & Audience → Structured Constraints → Human Review & Refinement**

---

## 2. Objectives

By completing this lab, I demonstrated the ability to:

- Apply generative AI to a practical cybersecurity task.
- Design progressively improved prompts.
- Provide role, audience, context, and output requirements.
- Constrain AI output to an approved source.
- Reduce the risk of unsupported or invented security requirements.
- Review AI-generated security content for accuracy.
- Identify omissions, unsupported statements, and broadened meanings.
- Refine AI-generated content while preserving the original policy intent.
- Apply human-in-the-loop review to AI-assisted security work.
- Recognize security and privacy risks associated with using AI tools.

---

# 3. Controlled Marctech Security Policy

The following fictional policy was used as the controlled source throughout the lab.

### Authentication

- Employees must use MFA when accessing company systems that require it.
- Employees must never approve an unexpected MFA authentication request.
- Suspected MFA compromise must be reported to the IT/Security team.

### Phishing

- Employees must not provide company credentials in response to unsolicited requests.
- Suspicious messages should be reported through the organization's approved reporting process.

### Removable Media

- Employees must not connect unknown or unauthorized removable media to company systems.
- Company-approved removable media must be handled according to organizational security procedures.

### Security Incidents

- Employees must promptly report suspected security incidents.
- Employees should preserve relevant information and avoid attempting unauthorized investigation or remediation.

---

# 4. Activity 1 — Baseline AI Policy Summary

## Objective

Establish a baseline by asking the AI to summarize the Marctech employee security policy without extensive prompt constraints.

## AI Application

Google Gemini was used to generate an initial employee-facing summary of the controlled security policy.

The baseline prompt provided the policy but contained limited instructions regarding role, audience, structure, and output constraints.

## Analyst Observation

The baseline output provided a useful starting point but demonstrated why AI-generated security content requires additional context and review.

A basic prompt can produce a generally reasonable response, but the output may not be optimized for:

- A specific employee audience.
- Organizational context.
- Consistent structure.
- Strict source fidelity.
- Security-specific review requirements.

### Evidence

[View Screenshot — Baseline Policy Summary](./Screenshots/01-Baseline-Policy-Summary.png)

---

# 5. Activity 2 — Role, Audience & Context Prompting

## Objective

Determine whether explicitly defining the AI's role, intended audience, organizational context, and scope improves the usefulness of the generated guidance.

## Prompting Approach

Gemini was instructed to act as a junior cybersecurity analyst supporting Marctech and to produce employee-facing guidance for users with basic technical knowledge.

The prompt also explicitly required the AI to:

- Use plain language.
- Avoid unnecessary cybersecurity jargon.
- Use only the supplied policy.
- Avoid creating new security requirements.

## Analyst Observation

The resulting output was more targeted toward the intended audience.

The response used clearer employee-oriented sections such as:

- System Logins (MFA)
- Phishing & Suspicious Messages
- USBs & Removable Drives
- Handling Security Incidents

The output also became more action-oriented.

However, human review remained necessary.

For example, the AI broadened the phishing requirement by using language such as usernames and passwords, while the controlled policy specifically addressed providing company credentials in response to unsolicited requests.

This demonstrated that **better prompting improves usefulness but does not guarantee exact policy fidelity.**

### Evidence

[View Screenshot — Role, Audience & Context Prompt](./Screenshots/02-Role-Audience-Context-Prompt.png)

---

# 6. Activity 3 — Structured Output & Security Constraints

## Objective

Evaluate whether explicit structure and security constraints can further control AI-generated content.

## Prompting Approach

The AI was instructed to create employee guidance for each policy topic using a defined structure:

1. Security requirement.
2. Plain-language explanation.
3. What the employee should do.
4. What the employee should avoid doing.
5. When the employee should contact IT or Security.

Additional constraints required the AI to:

- Use only the controlled policy.
- Avoid creating new security requirements.
- Avoid changing the meaning of requirements.
- Avoid exaggerating security risks.
- Identify limitations instead of inventing information.
- Use clear employee-friendly language.

## Analyst Observation

This activity demonstrated how structured prompting can make AI output more predictable and easier to review.

The explicit constraints established a stronger boundary around the AI's response and reduced the likelihood of unsupported recommendations being presented as Marctech policy.

The exercise also reinforced an important security principle:

> **Prompt constraints can reduce AI-generated errors, but they do not replace human validation.**

### Evidence

[View Screenshot — Structured Policy Guidance](./Screenshots/03-Structured-Policy-Guidance.png)

---

# 7. Activity 4 — Human Review & Iterative Prompt Refinement

## Objective

Review the previous AI-generated employee guidance against the controlled Marctech security policy and identify potential problems before producing a refined version.

## Review Criteria

The AI was instructed to identify:

- Unsupported statements.
- Omitted policy requirements.
- Statements that changed or broadened the original meaning.
- Newly introduced security requirements.
- Potentially confusing employee instructions.
- Unnecessarily technical terminology.

The AI was then instructed to produce a revised employee guidance document while remaining faithful to the controlled policy.

## AI Review Findings

Gemini identified several issues in the previous response, including:

### Unsupported Addition

The AI identified speculation about an unexpected MFA request potentially indicating that another person was attempting to access the account.

The controlled policy did not make that assertion.

### Broadened Policy Meaning

Gemini identified that previous language regarding sharing usernames or passwords could broaden the original phishing requirement.

The controlled policy specifically addressed providing company credentials in response to unsolicited requests.

### Potential Ambiguity

Gemini identified that specifying examples such as files, messages, or notes could unintentionally narrow the broader requirement to preserve relevant information.

### Technical Terminology

Gemini identified the use of the term "remediation" as potentially unnecessary for employees with basic technical knowledge.

---

## Human Analyst Validation

The AI-generated review was not automatically accepted as authoritative.

The revised AI guidance itself required additional human review.

For example, the controlled policy states:

> Employees must promptly report suspected security incidents.

The revised AI guidance changed this to:

> Report any suspected security problem immediately.

### Analyst Finding

"Immediately" is stronger than the source policy's "promptly."

The wording should therefore be reviewed and aligned with the original policy rather than automatically accepted.

This demonstrated that **AI can assist with reviewing AI-generated content, but the AI's review also requires human validation.**

### Evidence

[View Screenshot — Human Review & Prompt Refinement](./Screenshots/04-Human-Review-Prompt-Refinement.png)

---

# 8. Prompt Engineering Progression

The four activities demonstrated a progressive improvement in prompt design.

| Activity | Prompting Technique | Primary Purpose |
|---|---|---|
| Activity 1 | Baseline prompt | Establish baseline AI output |
| Activity 2 | Role + audience + context | Improve relevance and usability |
| Activity 3 | Structure + constraints | Improve consistency and source fidelity |
| Activity 4 | Review + refinement | Identify and correct AI-generated issues |

### Key Observation

Increasing prompt specificity improved the usefulness and structure of the AI-generated responses.

However:

> **More detailed prompting did not eliminate the need for human review.**

This is particularly important when AI is used for cybersecurity policies, procedures, employee instructions, or other security-sensitive content.

---

# 9. Security & Privacy Considerations

Generative AI should not automatically be treated as an approved destination for organizational information.

This lab used a **fictional Marctech security policy** specifically to avoid exposing real organizational information.

No real:

- Passwords
- Credentials
- Personally identifiable information
- Confidential business information
- Security keys
- Authentication tokens
- Production security configurations
- Sensitive incident information

were used in the exercise.

### Real-World Security Consideration

Before using an AI service for organizational work, employees should follow applicable:

- Organizational AI-use policies.
- Data classification requirements.
- Acceptable-use policies.
- Privacy requirements.
- Security procedures.
- Approved AI-tool requirements.

Employees should verify with their employer or organization's security and compliance policies before submitting organizational information to an AI system.

Only information approved for the specific AI service should be provided.

---

# 10. Key Skills Demonstrated

### AI & Prompt Engineering

- Generative AI fundamentals.
- Prompt construction.
- Role prompting.
- Audience targeting.
- Context injection.
- Structured prompting.
- Constraint-based prompting.
- Iterative prompt refinement.

### Cybersecurity

- Security policy interpretation.
- Security awareness communication.
- Policy-to-guidance translation.
- Security requirement validation.
- Identification of unsupported security claims.
- Identification of policy drift.
- Human-in-the-loop security review.

### AI Security Awareness

- AI output validation.
- Source grounding.
- Recognition of hallucination/unsupported claims.
- Data exposure awareness.
- Organizational AI-use considerations.
- Security-sensitive AI usage.

---

# 11. Analyst Takeaways

This lab demonstrated that effective cybersecurity use of generative AI requires more than knowing how to write prompts.

The most important lessons were:

1. **Prompt quality affects AI output quality.**
2. **Context and audience improve the usefulness of generated content.**
3. **Explicit constraints can reduce unsupported or invented requirements.**
4. **AI-generated security content should be reviewed before use.**
5. **AI can assist with reviewing AI-generated content, but that review also requires human validation.**
6. **Security policies should remain the authoritative source rather than the AI model.**
7. **Sensitive organizational information should not be entered into an AI tool without authorization.**

### Final Principle

> **Use AI as an assistant—not as the authority.**

For security-sensitive work, the authoritative policy, organizational requirements, and qualified human review remain the final controls over what is approved for use.
