# Lab 03 - AI-Assisted Research & Information Synthesis

## Adversary-in-the-Middle (AiTM) Phishing Research Brief

**Organization:** Marctech  
**Role:** Junior Cybersecurity Analyst  
**AI Assistant:** Google Gemini  
**Lab Focus:** AI-assisted cybersecurity research, source discovery, information synthesis, source verification, and analyst judgment

---

## 1. Overview

This lab demonstrates how generative AI can support cybersecurity research while maintaining human oversight and authoritative-source verification.

As a Junior Cybersecurity Analyst supporting the Marctech Security Operations team, I was asked to research **Adversary-in-the-Middle (AiTM) phishing** following a hypothetical phishing-related security alert.

Google Gemini was used as an approved AI assistant to support research planning, source discovery, information organization, and synthesis.

AI-generated information was treated as provisional and was not considered authoritative without independent verification.

---

## 2. Real-World Scenario

A Marctech employee reports receiving a suspicious message that directed them to a login page.

During initial triage, the Security Operations team identifies two notable indicators:

1. The message directs the employee to a suspicious login page that closely resembles the organization's legitimate sign-in page.

2. Initial analysis indicates that the suspicious site may be acting as an intermediary between the user and the legitimate authentication service.

These indicators raise the possibility of an **Adversary-in-the-Middle (AiTM)** phishing technique.

However, the activity has **not been confirmed as AiTM**.

The Security Operations team asks the Junior Cybersecurity Analyst to conduct initial research into AiTM phishing to help determine:

- How the technique works.
- How authentication information or sessions may be targeted.
- What additional evidence should be examined.
- What security implications may exist.
- What defensive considerations should be evaluated.

The analyst uses **Google Gemini as the organization's approved AI assistant** to support the research process.

The analyst does not treat the initial indicators as proof of an AiTM attack. The research is used to develop an informed hypothesis and identify information that requires further verification.

> **SOC principle: An indicator can justify investigation, but it does not by itself establish a confirmed finding.**

---

## 3. Research Objective

The primary research question was:

> How does Adversary-in-the-Middle (AiTM) phishing work, what security risks does it create, and what defensive considerations should a security analyst understand when investigating suspected AiTM activity?

The objective was to demonstrate an AI-assisted research workflow rather than simply asking an AI system to explain a cybersecurity topic.

---

## 4. Research Methodology

The workflow used in this lab was:

**Research Question → AI-Assisted Research Planning → Source Discovery → Source Verification → Information Synthesis → Analyst Review → Security Brief**

The core principle was:

> **AI-generated research is a starting point, not the final source of truth.**

AI-generated claims and source suggestions were independently evaluated before being incorporated into the final research brief.

---

# 5. Hands-On Activities

## Activity 1 - Research Question & Scope Development

### Objective

Used Google Gemini to transform the initial SOC research request into a focused research question and defined research scope.

### Skills Demonstrated

- AI-assisted research planning
- Research question formulation
- Scope definition
- Security context development
- Responsible AI use

### Evidence

[**View Screenshot - Research Question & Scope**](./Screenshots/01-Research-Question-and-Scope.png)

---

## Activity 2 - AI-Assisted Source Discovery & Credibility Assessment

### Objective

Used Google Gemini to identify potentially relevant cybersecurity sources.

AI-generated source suggestions were treated as **research leads rather than evidence**.

Sources were independently reviewed before being used in the research brief.

### Skills Demonstrated

- AI-assisted source discovery
- Source credibility assessment
- Research methodology
- Source verification
- Information literacy

### Evidence

[**View Screenshot - Source Discovery & Credibility Assessment**](./Screenshots/02-Source-Discovery-and-Credibility.png)

---

## Activity 3 - Cross-Source Information Synthesis

### Objective

Used Google Gemini to organize and synthesize findings from multiple independently verified sources.

The AI was instructed to use only the verified findings provided by the analyst and not introduce unsupported claims.

The resulting synthesis was compared against the original source material.

### Analyst Review Focus

- Source attribution
- Unsupported claims
- Changes in meaning
- Overgeneralization
- Missing context
- AI-generated interpretation presented as fact

### Skills Demonstrated

- Cross-source synthesis
- Source-grounded generation
- Information organization
- Fact-versus-interpretation analysis
- AI output review

### Evidence

[**View Screenshot - Cross-Source Information Synthesis**](./Screenshots/03-Cross-Source-Information-Synthesis.png)

---

## Activity 4 - SOC Research Brief & Analyst Verification

### Objective

Used the verified research findings to produce a concise security research brief for a SOC audience.

The final output was reviewed against the original authoritative sources.

### Analyst Verification

The analyst reviewed the final brief for:

- Accuracy
- Source attribution
- Completeness
- Technical precision
- Unsupported claims
- Overgeneralization
- Separation of fact from interpretation
- Appropriate security recommendations

### Skills Demonstrated

- AI-assisted technical research
- Security briefing development
- Analyst verification
- Technical communication
- Source traceability
- Critical thinking

### Evidence

[**View Screenshot - SOC Research Brief & Analyst Verification**](./Screenshots/04-SOC-Research-Brief-Verification.png)

---

# 6. Source Verification Principles

### AI Output Is Not Automatically Evidence

Information generated by Gemini was treated as provisional and independently evaluated before being used as a security finding.

### AI-Discovered Sources Are Research Leads

A source suggested by an AI assistant was independently reviewed before being cited.

### Authoritative Sources Are Preferred

Where available, the research prioritized:

- Government cybersecurity agencies
- Standards organizations
- Official advisories
- Original technical documentation
- Primary research

### Facts and Interpretation Are Distinguished

Source-supported facts were separated from analyst interpretation and AI-generated summaries.

### Citations Are Traceable

Important findings were linked to the source from which the information originated.

---

# 7. Responsible AI & Security Boundaries

Only public and non-sensitive information was used in this exercise.

The following were not provided to the AI system:

- Real credentials
- Personally identifiable information
- Customer information
- Confidential incident information
- Internal security logs
- Internal network information
- Proprietary security configurations
- Sensitive organizational data

### Real-World AI Use Requirement

In a real organization, employees should use only AI tools approved by their organization and follow applicable:

- AI acceptable-use policies
- Data-classification requirements
- Privacy requirements
- Security requirements
- Regulatory requirements
- Contractual requirements
- Data-retention requirements

Employees should not move sensitive organizational information between different AI services simply because another service produces a preferred response.

AI tool selection and permitted use should be determined by organizational policy and security governance.

---

# 8. Evidence Summary

| Evidence | Demonstrated Skill |
|---|---|
| [01 - Research Question & Scope](./Screenshots/01-Research-Question-and-Scope.png) | AI-assisted research planning |
| [02 - Source Discovery & Credibility](./Screenshots/02-Source-Discovery-and-Credibility.png) | AI-assisted source discovery and verification |
| [03 - Cross-Source Synthesis](./Screenshots/03-Cross-Source-Information-Synthesis.png) | AI-assisted information synthesis |
| [04 - Research Brief & Verification](./Screenshots/04-SOC-Research-Brief-Verification.png) | AI-assisted technical documentation and analyst review |

---

# 9. Skills Demonstrated

### Artificial Intelligence

- Generative AI
- AI-assisted research
- Prompt engineering
- Source-grounded generation
- Information synthesis
- AI output evaluation
- AI-assisted technical writing

### Cybersecurity

- SOC research
- Phishing analysis
- Adversary-in-the-Middle awareness
- Threat research
- Security research methodology
- Source verification
- Security analysis
- Security communication

### Professional Skills

- Critical thinking
- Research methodology
- Information validation
- Technical communication
- Evidence-based analysis
- Documentation
- Analyst judgment

---

# 10. Outcome

This lab demonstrated how generative AI can accelerate cybersecurity research without replacing analyst judgment.

The completed workflow combined:

**AI Assistance + Authoritative Sources + Human Verification**

The analyst remained responsible for determining whether research findings were accurate, adequately supported, technically appropriate, and suitable for inclusion in the final security brief.

---

# 11. Portfolio Takeaway

> **Applied Google Gemini to an AI-assisted cybersecurity research workflow by defining a focused research question, discovering and evaluating authoritative sources, synthesizing verified findings, and producing a SOC-oriented research brief while maintaining source traceability and human verification.**

---

## Disclaimer

This portfolio lab uses a fictional Marctech organization and hypothetical security scenario for educational and demonstration purposes.

No real Marctech security incident occurred as part of this exercise.

No real organizational credentials, confidential information, customer data, internal security configurations, or other sensitive information were submitted to the AI system.

In a real-world environment, AI use should follow the organization's approved AI tools, security policies, data-classification requirements, privacy requirements, and applicable regulatory or contractual obligations.
