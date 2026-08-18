# Lab 03 — AI-Assisted Research & Information Synthesis

## Adversary-in-the-Middle (AiTM) Phishing Research Brief

**Organization:** Marctech  
**Role:** Junior Cybersecurity Analyst  
**AI Assistant:** Google Gemini  
**Lab Focus:** AI-assisted cybersecurity research, source discovery, information synthesis, source verification, and analyst judgment

---

# 1. Overview

This lab demonstrates how generative AI can be used to support cybersecurity research while maintaining human oversight and authoritative-source verification.

As a Junior Cybersecurity Analyst supporting the Marctech Security Operations team, I was asked to research **Adversary-in-the-Middle (AiTM) phishing** following a hypothetical phishing-related security alert.

The objective was to use Google Gemini as an approved AI assistant to help:

- Define the research scope.
- Identify relevant research questions.
- Discover potentially useful cybersecurity sources.
- Organize information from multiple sources.
- Synthesize findings into an analyst-oriented security brief.

The AI assistant was not treated as an authoritative security source.

Instead, AI-generated research suggestions and summaries were treated as provisional and were reviewed against authoritative cybersecurity sources before being incorporated into the final research brief.

---

# 2. Real-World Scenario

A Marctech employee reports receiving a suspicious message that may have been part of a credential-phishing campaign.

The Security Operations team wants the junior analyst to perform initial research on **Adversary-in-the-Middle (AiTM) phishing** to better understand:

- How the attack technique works.
- How credentials or authentication sessions may be targeted.
- Why traditional authentication protections may be insufficient in some scenarios.
- What security teams should understand when investigating suspected AiTM activity.
- What defensive considerations are relevant.

The analyst uses **Google Gemini as the organization's approved AI assistant** to accelerate the research process.

The analyst remains responsible for determining whether information is accurate and supported by reliable sources.

---

# 3. Research Question

The primary research question for this exercise is:

> **How does Adversary-in-the-Middle (AiTM) phishing work, what security risks does it create, and what defensive considerations should a security analyst understand when investigating suspected AiTM activity?**

The research is intentionally limited to publicly available cybersecurity information and the fictional Marctech scenario.

---

# 4. Research Scope

The research focuses on:

- AiTM phishing
- Credential theft
- Session/token theft
- Phishing techniques
- Authentication interception
- Security implications
- Detection and investigation considerations
- Defensive recommendations
- Phishing-resistant authentication

The research does not involve:

- Real Marctech incidents
- Real employee information
- Real credentials
- Internal security logs
- Internal network architecture
- Confidential incident information
- Unauthorized testing of external systems

---

# 5. AI Tool & Environment

**AI Assistant:** Google Gemini

**Approved Use in This Lab:**

- Research question development
- Research planning
- Source discovery
- Information organization
- Cross-source synthesis
- Drafting of a security research brief

AI-generated information was treated as **provisional** until reviewed against authoritative sources.

The analyst remained responsible for:

- Source selection
- Source verification
- Accuracy assessment
- Identifying unsupported claims
- Final interpretation
- Final security recommendations

---

# 6. Research Methodology

The research workflow used in this lab was:

```text
Research Question
       |
       v
AI-Assisted Research Planning
       |
       v
Source Discovery
       |
       v
Source Credibility Assessment
       |
       v
Authoritative Source Review
       |
       v
Information Extraction
       |
       v
Cross-Source AI Synthesis
       |
       v
Analyst Verification
       |
       v
Security Research Brief

The key principle is:

AI-generated research is a starting point, not the final source of truth.

7. Hands-On Activities
Activity 1 — Research Question & Scope Development
Objective

Use generative AI to help transform the initial SOC research request into a focused research question and defined research scope.

Prompt Used
Act as a junior cybersecurity analyst supporting the Marctech Security Operations team.


A Marctech employee has reported a suspicious phishing message. The security team wants to conduct initial research into Adversary-in-the-Middle (AiTM) phishing.


Help me define a focused cybersecurity research question and research scope.


Identify:


1. The primary research question.
2. Key questions a SOC analyst should answer.
3. Important technical concepts that should be researched.
4. Security implications that should be considered.
5. Defensive or investigation considerations that should be researched.
6. Topics that should remain outside the scope of this research.


Do not assume that an actual Marctech incident occurred.


Use the fictional scenario only as context.


Do not provide instructions for conducting an attack.


Clearly distinguish general cybersecurity knowledge from information that would require verification from authoritative sources.
Skills Demonstrated
AI-assisted research planning
Research question formulation
Scope definition
Security context development
Responsible AI use
Evidence

View Screenshot — Research Question & Scope

8. Activity 2 — AI-Assisted Source Discovery & Credibility Assessment
Objective

Use AI to identify potentially relevant cybersecurity sources while treating AI-generated source suggestions as leads requiring independent verification.

Prompt Used
Act as a cybersecurity research assistant.


I am researching Adversary-in-the-Middle (AiTM) phishing for a SOC analyst research brief.


Identify potentially useful authoritative sources that I should review.


Prioritize:


- U.S. government cybersecurity agencies
- NIST publications
- Established cybersecurity standards
- Official security advisories
- Primary vendor security documentation where appropriate
- Reputable cybersecurity research organizations


For each suggested source, provide:


1. Organization or publisher
2. Document or resource title
3. Topic covered
4. Why the source may be relevant
5. What information I should verify from the original source


Do not treat your own response as evidence.


Do not invent sources, document titles, URLs, or quotations.


Clearly identify any source that requires independent verification.
Analyst Verification

AI-generated source suggestions were treated as research leads.

Sources were independently reviewed before being used as evidence in the final research brief.

The analyst prioritized authoritative and primary sources where available.

Skills Demonstrated
AI-assisted source discovery
Source credibility assessment
Research methodology
Source verification
Information literacy
Evidence

View Screenshot — Source Discovery & Credibility Assessment

9. Activity 3 — Cross-Source Information Synthesis
Objective

Use AI to organize and synthesize information from multiple verified sources.

The analyst provides relevant information from reviewed sources to Gemini and asks it to organize the findings.

The AI is instructed not to introduce unsupported claims.

Prompt Used
Act as a cybersecurity research analyst.


I am preparing a research brief on Adversary-in-the-Middle (AiTM) phishing.


Below are findings extracted from sources that I independently reviewed.


Use only the information provided below to organize and synthesize the findings.


For each finding:


1. Summarize the key point.
2. Identify the supporting source.
3. Explain the security significance.
4. Identify whether the information is directly stated by the source or represents an interpretation.
5. Identify any areas that require additional verification.


Do not introduce facts that are not supported by the provided source material.


Do not invent citations or source claims.


Source 1:
[Insert verified source finding]


Source 2:
[Insert verified source finding]


Source 3:
[Insert verified source finding]
Analyst Review

The resulting synthesis was compared against the original source material.

Particular attention was given to:

Source attribution
Unsupported claims
Changes in meaning
Overgeneralization
Missing context
AI-generated interpretation presented as fact
Skills Demonstrated
Cross-source synthesis
Source-grounded generation
Information organization
Fact-versus-interpretation analysis
AI output review
Evidence

View Screenshot — Cross-Source Information Synthesis

10. Activity 4 — SOC Research Brief & Analyst Verification
Objective

Use the verified research findings to create a concise security research brief for a SOC audience.

Prompt Used
Using only the verified research findings provided below, create a concise cybersecurity research brief for the Marctech Security Operations team.


Structure the brief as follows:


# Security Research Brief


## Topic


## Executive Summary


## Key Findings


## How the Technique Works


## Security Implications


## Investigation Considerations


## Defensive Considerations


## Areas Requiring Further Verification


## Sources


Requirements:


- Use only the provided verified findings.
- Do not introduce unsupported technical claims.
- Clearly distinguish source-supported facts from analyst interpretation.
- Do not claim that Marctech experienced an actual AiTM attack.
- Do not provide offensive instructions.
- Use concise professional language appropriate for a SOC analyst.
- Preserve source attribution.
- Identify information that cannot be determined from the available sources.


Verified Research Findings:


[Insert verified research findings]
Analyst Verification

The final research brief was reviewed against the original authoritative sources.

The analyst checked:

Accuracy
Source attribution
Completeness
Technical precision
Unsupported claims
Overgeneralization
Separation of fact from interpretation
Appropriate security recommendations
Skills Demonstrated
AI-assisted technical research
Security briefing development
Analyst verification
Technical communication
Source traceability
Critical thinking
Evidence

View Screenshot — SOC Research Brief & Analyst Verification

11. Source Verification Principles

This lab follows several research principles.

AI output is not automatically evidence

Information generated by Gemini must be independently evaluated before being treated as a security finding.

AI-discovered sources are research leads

A source suggested by an AI assistant must be opened and independently reviewed before being cited.

Primary and authoritative sources are preferred

Where available, research should prioritize:

Government cybersecurity agencies
Standards organizations
Official advisories
Original technical documentation
Primary research
Facts and interpretation must be distinguished

A source-supported fact should not be presented as though it were an AI-generated interpretation.

Citations must be traceable

A reader should be able to identify where an important security finding originated.

12. Responsible AI & Security Boundaries

Cybersecurity research can involve sensitive information.

For this lab:

Only public information was used for the research topic.
The Marctech incident scenario is fictional.
No real employee information was provided.
No credentials were provided.
No confidential incident information was provided.
No internal security logs were provided.
No internal network information was provided.
No proprietary security configurations were provided.
Real-World AI Use Requirement

In a real organization, employees should use only AI tools approved by their organization and follow applicable:

AI acceptable-use policies
Data-classification requirements
Privacy requirements
Security requirements
Regulatory requirements
Contractual requirements
Data-retention requirements

Sensitive organizational information should not be submitted to an AI system unless such use is explicitly authorized and appropriate security controls are in place.

Employees should not move sensitive information between different AI services simply because another service produces a preferred response.

13. Evidence

All screenshots are stored in the lab's dedicated Screenshots directory.

Evidence	Description
01 — Research Question & Scope	AI-assisted development of the research question and research boundaries
02 — Source Discovery & Credibility Assessment	AI-assisted source discovery followed by source verification
03 — Cross-Source Information Synthesis	AI-assisted organization and synthesis of verified source findings
04 — SOC Research Brief & Analyst Verification	Final research brief and analyst verification workflow
14. Skills Demonstrated
Artificial Intelligence
Generative AI
AI-assisted research
Prompt engineering
Source-grounded generation
Information synthesis
AI output evaluation
AI-assisted technical writing
Cybersecurity
SOC research
Phishing analysis
Adversary-in-the-Middle awareness
Security research methodology
Source verification
Threat research
Security analysis
Security communication
Professional Skills
Critical thinking
Research methodology
Information validation
Technical communication
Evidence-based analysis
Documentation
Analyst judgment
15. Outcome

This lab demonstrates how generative AI can accelerate cybersecurity research without replacing analyst judgment.

The exercise followed the workflow:

Research Question → AI-Assisted Discovery → Source Verification → Information Synthesis → Analyst Review → Security Brief

The analyst remained responsible for determining whether research findings were accurate, adequately supported, and appropriate for inclusion in the final security brief.

The exercise also demonstrated that AI-generated information should not automatically be treated as authoritative simply because it is presented confidently.

16. Portfolio Takeaway

Applied Google Gemini to an AI-assisted cybersecurity research workflow by defining a focused research question, discovering and evaluating authoritative sources, synthesizing verified findings, and producing a SOC-oriented research brief while maintaining source traceability and human verification.

Disclaimer

This portfolio lab uses a fictional Marctech organization and hypothetical security scenario for educational and demonstration purposes.

No real Marctech security incident occurred as part of this exercise.

No real organizational credentials, confidential information, customer data, internal security configurations, or other sensitive information were submitted to the AI system.

In a real-world environment, AI use should follow the organization's approved AI tools, security policies, data-classification requirements, privacy requirements, and applicable regulatory or contractual obligations.



### One thing before you paste this into GitHub


For **Activity 2**, don't let Gemini invent sources and then screenshot them as though they're verified. We want the evidence to show the actual workflow:


**Gemini suggests → analyst checks original source → verified source is used.**


Likewise, for Activity 3, we'll use the **actual verified source findings** rather than asking Gemini to independently make up the research.


That distinction is what makes this Lab 03 substantially stronger than simply asking an AI, *"Explain AiTM."*
