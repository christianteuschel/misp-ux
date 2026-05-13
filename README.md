# MISP UX Research

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](LICENSE)

[MISP](https://www.misp-project.org/) (Malware Information Sharing Platform) is an open-source threat intelligence platform developed by [CIRCL](https://www.circl.lu) for sharing and correlating indicators of compromise (IOCs), malware samples, and threat data across organisations.

This repository collects UX research artifacts for MISP, combining official CIRCL documentation with empirical user research conducted at [Hackathon.lu 2026](https://hackathon.lu). It is intended for UX designers, product contributors, and researchers working to improve the MISP user experience.

---

## Repository Structure

```
misp-ux/
├── misp/2024/                        Official CIRCL documentation (October 2024)
│   ├── user_personas_official.md         9 official user personas
│   └── user_stories_official.md          55 structured user stories
│
└── hackathon.lu/2026/                Empirical research, Hackathon.lu (April 2026)
    ├── interview_guide.md                Interview methodology and question framework
    ├── derived_interviews.md             9 anonymised, structured interview summaries
    ├── derived_personas.md               6 personas derived from observed behaviour
    ├── derived_use_cases.md              7 operational use cases + 7 AI opportunities
    ├── personas_comparison.md            Official vs. derived persona analysis
    ├── use_cases_comparison.md           Official user stories vs. derived use cases
    └── derived_top_issues.md             Prioritised action items
```

---

## Research Tracks

### Track 1 — Official Documentation (`misp/2024/`)

Sourced from the [MISP user personas page](https://www.circl.lu/doc/misp/user-personas/), this track describes nine idealised personas representing experienced, settled MISP users across roles — threat hunters, incident responders, fraud analysts, law enforcement officers, consultants, risk analysts, disinformation researchers, and data scientists. Fifty-five structured user stories accompany these personas, covering workflows across threat analysis, malware triage, DFIR, fraud detection, and more.

These artifacts reflect MISP at its best: users who have already navigated onboarding and developed fluency with the platform.

### Track 2 — Empirical Research (`hackathon.lu/2026/`)

Nine structured user interviews were conducted at Hackathon.lu on 14–15 April 2026. Participants ranged from incident-response analysts and CTI team leads to deployment engineers and developers building tools on top of the MISP API. The research surfaces friction, workarounds, and unmet needs that do not appear in the official documentation.

Derived artifacts include six grounded personas, seven operational use cases, a gap analysis against the official documentation, and seven concrete AI-assisted opportunities for reducing user friction.

---

## Key Findings

1. **First-run experience drives users away.** Six of nine interviewees described being overwhelmed on first use. One user abandoned MISP entirely on day one despite it meeting all their feature requirements. The biggest lever here is progressive onboarding and in-context help.

2. **The basic IOC ingestion path has too much friction.** The most frequent MISP workflow — taking unstructured data (e.g., a phishing email) and creating a structured event — requires manual copy-paste, loses data between preview and edit views, and uses confusing field names (`Description` is actually the event name). This affects daily users most directly.

3. **Documentation is scattered and hard to navigate.** Nearly every interviewee mentioned this. There is no single entry point for new users, no architectural overview, and no examples-first PyMISP guide. Configuration endpoints can take hours to locate.

---

## Notable Gaps vs. Official Documentation

| Gap | Detail |
|---|---|
| **Operator / Deployment Engineer (P5)** | Completely absent from the official persona set. Covers installation, Docker/LXC configuration, admin views, and air-gapped deployments. |
| **Newcomer (P6)** | Also absent. Represents users who arrive with a small, concrete goal and form a lasting first impression within minutes — a strategically critical persona for adoption. |
| **Deployment & operations (UC6)** | No official user stories address the operational lifecycle of running a MISP instance. |
| **Detection-rule integration (UC5)** | Using MISP to author, store, and link detection rules (Wazuh, Sigma, etc.) has no coverage in the official story set. |

---

## License

This work is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE). You are free to share and adapt the material for any purpose, provided appropriate credit is given.
