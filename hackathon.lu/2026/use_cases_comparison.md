# Use Case Comparison: Official MISP User Stories vs. Interview-Derived Use Cases

This document compares the user stories defined in the official MISP documentation (`MISP/2024/user_stories_official.md`) with the use cases derived from the Hackathon.lu 2026 user interviews (`hackathon.lu/2026/derived_use_cases.md`).

---

## What the Official User Stories Add

The official user stories are written from the perspective of experienced, role-identified users — threat analysts, SOC teams, incident responders, fraud analysts, law enforcement, data scientists, and others. They describe MISP as a capable, feature-complete platform and are structured around what a user *wants to accomplish*, with concrete workflow steps attached.

### Domains entirely absent from the interviews

Several official user story clusters have no equivalent in the interview data at all:

- **Malware analysis and reverse engineering** — attaching and downloading malware samples, submitting to VirusTotal/VMRay, performing dynamic malware analysis correlations. None of the interviewees described this workflow.
- **CVE and vulnerability management** — importing CVEs from MetaSploit, contextualising vulnerabilities, converting CVE data into feeds. Not mentioned in any interview.
- **Fraud detection** — sharing financial indicators between banks, feeding anti-fraud blocking systems, cross-referencing stolen cards. No interviewee worked in the financial sector.
- **Law enforcement and DFIR** — collecting digital evidence, importing Mactime timelines, bootstrapping DFIR cases, collaborating with CSIRTs. Absent from the interviews.
- **Customs and border control** — sharing passenger name records and biometric data, offline border control checks. A highly specialised domain not represented at the hackathon.
- **Disinformation research** — AM!TT framework, DFRLab taxonomies, CogSec Collab community, campaign mapping. No interviewee worked in this space.
- **Risk analysis and stakeholder reporting** — presenting threat data in non-technical formats, generating timelines and graphs for management. Not raised by any interviewee.
- **Anonymous/pseudo-anonymous publishing** — Event Delegation for protecting source identity. Not mentioned.

### Breadth of the SOC and CSIRT workflows

The official stories cover the full SOC lifecycle in detail: ingesting CVEs, customising risk feeds to reduce alert fatigue, sharing real-time case information between analysts, ruling out false positives, and coordinating cross-organisation incident response. The interviews touched some of this (Interview 1, Interview 6) but only at the surface level of basic event creation and feed consumption.

### Feature-level completeness

The official stories reference a much wider set of MISP features than the interviews surfaced: ZMQ pub-sub, Event Reports, Extended Events, the delegation system, the Geolocalisation Dashboard, SightingsDB, the ATT&CK navigator, Cortex analysers, and RPZ zone generation. These appear in workflows because experienced users have discovered and integrated them; the interviewees mostly hadn't reached that point.

---

## What the Interview-Derived Use Cases Add

The interview use cases are grounded in the actual workflows observed or described during the sessions, including the friction that accompanies them. They add things the official stories do not address.

### Use cases entirely absent from the official stories

- **UC2 — Multi-Instance Synchronisation and Filtered Sharing** — The official stories mention syncing events between instances, but the interviews describe a specific and common architecture: one instance for broad feed collection, a second for high-confidence operational intelligence, with a filtering layer in between and a reverse hash-list path for mutual enrichment. The *operational complexity* of setting this up and the fragility of the documentation around it are invisible in the official stories.
- **UC5 — Detection-Rule Authoring and Import** — Storing detection rules (regex, Wazuh, Sigma, etc.) as MISP objects, tightly coupled to the intelligence that justifies them, and distributing them through the same sharing infrastructure. The official stories don't cover this integration pattern at all.
- **UC6 — Deployment, Configuration, and Operations** — Installing MISP in Docker or LXC containers, navigating admin views to configure settings, and the absence of a configuration export function. The official stories assume a running, configured instance; they are entirely silent on the operational burden of getting there.
- **AI-supported use cases (UC AI-1 through AI-7)** — The entire AI/LLM-assisted layer is absent from the official stories. This includes: free-text-to-event extraction, contextual galaxy/taxonomy suggestion, threat-actor name harmonisation, strategic synthesis ("connecting the dots"), contextual onboarding assistance, automated object construction for common patterns, and natural-language-to-PyMISP translation. These are not gaps in MISP today — they are opportunities identified from the interviews that do not yet exist.

### Friction as a first-class concern

The official user stories describe intended outcomes ("so that I can…") and working workflows. They contain no friction, no workarounds, and no failure modes. The interview use cases systematically document where workflows break down: unstructured input arriving by email with no automation, manual copy-paste as the primary ingestion mechanism, data loss when navigating between preview and edit, graph unreadability at scale, and documentation too scattered to follow. This friction data is essential for UX prioritisation and is entirely absent from the official set.

### Compliance and data protection obligations

UC4 (Phishing Investigation) surfaces a dimension not present in the official stories: incidents involving personal data may trigger a mandatory notification to the national data protection authority. This compliance dimension affects how events are classified and shared, and it has no representation in the official user story set.

---

## Overlaps

Five of the seven interview use cases have a reasonable counterpart in the official user stories, though the framing and emphasis differ substantially.

| Interview Use Case | Official User Story Counterpart | Overlap | Key Difference |
|---|---|---|---|
| UC1 — Incident-Driven IOC Ingestion and Correlation | "As a threat analyst, I want to have a structured database of threat data…" / "As a threat analyst, I want to investigate threats…" | Both cover creating events from incoming indicators, applying the batch import tool, using the IDS flag, and relying on automatic correlation. | The official story describes the happy path. UC1 documents the friction: unstructured email input, manual copy-paste, data loss on preview/edit navigation, and the field-naming confusion around "Description". |
| UC3 — Programmatic CTI Aggregation via API | "As a data scientist, I want to automate tasks…" / "As a security analyst, I want to automate repetitive tasks…" | Both cover using PyMISP, aggregating from multiple sources, building downstream pipelines, and integrating with SIEMs and other tools. | The official story frames this as smooth automation. UC3 foregrounds the scaling problems: STIX mapping failures, graph unreadability, naming inconsistency across providers, and the absence of accessible API examples for onboarding. |
| UC4 — Phishing Investigation | "As a security analyst, I want to unravel the inner workings of a malicious file, phishing email or domain…" / "As a fraud analyst, I want to investigate financial threats…" | Both cover creating structured events around phishing artefacts, correlating with prior incidents, and integrating with TheHive or similar tools. | UC4 is grounded in the specific MISP object structure (email object + phishing-site object) and adds the compliance trigger (data protection reporting obligation) not present in the official stories. |
| UC7 — Strategic-Level Threat Analysis | "As a threat analyst, I want to aggregate and compare indicators from various sources so that I can connect the dots…" / "As a risk analyst, I want to identify and predict risks…" | Both address correlating indicators across campaigns and actors, linking events using galaxies, and surfacing patterns across feeds. | The official stories treat this as achievable with existing features (correlation graph, galaxies, ATT&CK). UC7 documents that in practice these tools break down at scale — the graph becomes unreadable, actor naming is inconsistent, and the synthesis layer needed for strategic conclusions does not exist. |
| UC2 — Multi-Instance Synchronisation | "As a threat analyst, I want to exchange threat information with third parties…" / "As a CSIRT, we want to coordinate with team members and other organisations…" | Both address syncing data between instances and using distribution controls to manage what is shared. | The official stories describe the feature as it is designed to work. UC2 describes the operational reality: setup is complex, documentation is scattered, and the filtering architecture (two-instance model with true-positive forwarding) is something users have had to build themselves without guidance. |

The two interview use cases with **no official counterpart** — UC5 (Detection-Rule Import) and UC6 (Deployment and Operations) — represent the largest gaps. UC6 in particular is foundational: the official stories are written for people who are already past the deployment step, which means the hardest barrier to adoption is simply not documented.

---

## Summary

| | Official User Stories | Interview Use Cases |
|---|---|---|
| **Perspective** | Experienced users describing desired outcomes | Observed workflows, including friction and failure |
| **Tone** | Aspirational ("so that I can…") | Descriptive and diagnostic |
| **Domains covered** | Broad: malware, fraud, law enforcement, disinformation, border control, risk analysis | Narrow: incident response, synchronisation, API integration, phishing, detection rules, deployment |
| **Friction documented** | None | Systematic |
| **AI opportunities** | Not addressed | Seven concrete use cases identified |
| **Deployment / operations** | Not covered | UC6 dedicated to it |
| **Detection-rule integration** | Not covered | UC5 dedicated to it |
| **Compliance obligations** | Not covered | Raised in UC4 |

The official user stories answer: *"What should MISP enable for each role?"* The interview use cases answer: *"What are people actually doing, and where does it break?"* A complete picture for the MISP UX perspective requires both: the official stories as the feature and role reference, the interview use cases as the prioritisation and improvement agenda, and the AI-suported use cases as the forward-looking innovation layer.