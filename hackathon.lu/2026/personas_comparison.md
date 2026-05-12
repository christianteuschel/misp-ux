# Persona Comparison: Official CIRCL Personas vs. Interview-Derived Personas

This document compares the personas defined in the official MISP documentation (`MISP/2024/user_personas_offical.md`) with the personas derived from the Hackathon.lu 2026 user interviews (`hackathon.lu/2026/derived_personas.md`).

---

## What the Official CIRCL Personas Add

The official personas (Farrah, Adam, Tina, Henry, Jacob, Jay, Sarah, Malcolm) are descriptive success stories — they show MISP as it is used by experienced, settled users who have already found their way around the platform. Each persona is articulate about their goals and lists a rich inventory of MISP features they rely on.

### Personas with no equivalent in the interviews

- **Tina (Fraud Analyst)** — financial fraud detection, feeding blocking systems with warning lists and sightings, cross-referencing stolen cards before they reach the black market. No interviewee came from this domain.
- **Henry (Law Enforcement / DFIR)** — digital evidence collection, Mactime timelines, forensic use of MISP over time, collaboration with CSIRTs. Absent from the interviews entirely.
- **Sarah (Disinformation Researcher / Journalist)** — AM!TT framework, disinformation communities, Admiralty Scale taxonomy, converting technical data for non-technical audiences. No interview touched this domain.
- **Malcolm (Data Scientist)** — ML model training, predictive modelling, knowledge graphs, NLP. The interviews had API users and integrators, but no one working at this level of data science.

### Depth on the "happy path"

Because the official personas describe experienced users, they give a detailed picture of what MISP can do for each role when it works well. The interviews, by contrast, were mostly captured at pain points. The official personas are therefore useful as a reference for feature completeness and as a benchmark for what the UX should enable, even if they don't reflect the friction new users encounter.

---

## What the Interview-Derived Personas Add

The interview personas (P1–P6) are grounded in observed behaviour and friction, not idealised use.

### Personas with no equivalent in the official set

- **P5 — The Operator / Deployment Engineer** — installs and configures MISP instances, works in air-gapped and container-based environments, spends most of their time in admin views, wants a configuration export function. The official personas assume MISP is already running; this persona is responsible for making that true. It is invisible in the CIRCL documentation.
- **P6 — The Newcomer** — arrives with a small, specific goal, forms a first impression within minutes, and is highly likely to abandon the tool. This is arguably the most strategically important persona for platform growth, and it is completely absent from the official set. The official personas implicitly assume the user has already survived onboarding.

### A more realistic picture of existing personas

Where there are overlaps, the interview versions surface behaviours that the official personas gloss over — things like not using tags despite their importance, copy-pasting as the primary import mechanism, or not knowing that the workflows feature exists.

### Organisational and process friction

The interviews reveal constraints that don't appear anywhere in the official personas: internal approval processes for new tools (Interview 6), the ticketing/media break problem (Interview 1), and small teams of developers figuring out MISP as they go (Interviews 2, 3). These are not feature gaps but context gaps that shape how MISP is actually adopted.

---

## Overlaps

Four of the six interview personas map reasonably well onto official personas, though with meaningful differences in emphasis.

| Interview Persona | Official Persona | Overlap | Key Difference |
|---|---|---|---|
| P1 — Incident-Response Analyst | Adam (The Remediator) | Both do hands-on incident work, create events from incoming IOCs, use correlation, and share with external parties. | Adam is a polished CSIRT professional; P1 is a day-to-day practitioner who copy-pastes IOCs from email and doesn't use tags. P1 reveals the friction Adam presumably solved long ago. |
| P2 — CTI Team Lead | Jacob (The Veteran) | Both manage CTI operations, coordinate sharing between organisations, and care about distribution settings. | P2 is a passive consumer constrained by internal bureaucracy; Jacob is an active consultant integrating MISP into client stacks. P2 reflects a more common and less capable adoption pattern. |
| P3 — Strategic CTI Practitioner | Farrah (The Threat Hunter) | Both ingest from multiple CTI providers, rely on correlation at scale, and use the API heavily. | Farrah is the aspirational version — he has mastered the toolchain. P3 is frustrated by correlation ambiguity, unreadable graphs, and the absence of strategic synthesis. P3 reveals where Farrah's workflow breaks down. |
| P4 — Integrator / API User | Malcolm (The Data Expert) + Jacob (The Veteran) | Both treat MISP as a programmable platform, use PyMISP, and build tooling around the API. | P4 is motivated by integration and developer tooling (Wazuh, detection rules, STIX export); Malcolm is motivated by data science and ML. They use the same surface but for different ends. Jacob overlaps partially on the consulting/integration side. |

---

## Summary

The two sources are complementary rather than redundant.

- The **official personas** answer: *"Who uses MISP and what do they do with it when it works?"*
- The **interview personas** answer: *"Who is actually trying to use MISP today, and where does that experience break down?"*

The official personas were likely constructed from active, engaged community members, which structurally excludes people who gave up or who never got past installation. This explains why P5 (Operator) and P6 (Newcomer) — the two personas most relevant for understanding why adoption stalls — are absent from the official set.

A complete persona set for the `misp-ux` repository should draw on both sources: retain the official personas as role definitions and feature benchmarks, add P5 and P6 from the interviews, and annotate the overlapping personas with the friction and unmet needs the interviews surfaced.