# Captured Interviews — Structured Notes

This document consolidates findings from nine user interviews conducted at Hackathon.lu 2026. Each interview has been cleaned up, structured, and anonymized. Aggregated insights are presented as use cases (including AI-supported variants) and personas - see derived_use_cases.md and derived_personas.md.

---

## Interview Summaries

### Interview 1 — Incident Response Analyst

- **Role:** Incident Response analyst, working in the field for many years.
- **MISP usage frequency:** 2–3 times per week.
- **Typical workflow:**
  - Receives a high volume of IOCs by email from companies, mostly as unstructured data.
  - Creates a MISP event linked to a ticket number.
  - Copy-pastes IP addresses and applies a TLP tag to indicate sharing constraints.
  - Uses the batch import tool to convert pasted data into one attribute per line.
  - Uses the IDS flag to control whether attributes are exported to detection equipment.
  - Relies on automatic correlation between attributes.
  - Publishes the event to share it, then replies to the original email indicating whether the IOCs correlate with prior intelligence.
- **Frustrations / friction:**
  - Proxy-related issue: when creating an event and going back from the preview to edit, initial information is lost.
  - Reducing the view to "own events" surfaces ordering issues, e.g. in descriptions.
  - The field labelled "Description" actually represents the name; a separate description field is missing.
  - Galaxies are difficult to find — would benefit from a search field and ideally automatic suggestions based on context.
- **Notable behaviours:**
  - Does not use tags.
  - Most functionality is unused.
  - Common scenario: phishing investigation, where one event contains an object for the email and another for the phishing site.
  - Reporting of personal data must be escalated to the national data protection authority.
- **Cross-cutting comments:**
  - Ticketing creates a media break in the workflow.
  - End users sometimes call in with unusual or impractical ideas.

---

### Interview 2 — R&D Software Developer (Privacy Tech)

- **Role:** R&D software developer in ICT, working on privacy-enhancing technologies.
- **Team size:** Three engineers plus a project manager.
- **Tool selection rationale:** Evaluated alternatives, but chose MISP because of its European origin and adoption by law-enforcement agencies.
- **Typical workflow:**
  - Daily activities involve exploration and searching for documentation.
  - Runs MISP via Docker.
  - Uses MISP synchronisation to share between multiple instances.
  - Custom workflow: events contain private information, so only the intersection with external data is shared.
- **Frustrations / friction:**
  - Documentation is decentralised and hard to navigate (a known issue).
  - Setting up synchronisation is complex.
- **Notable comments:**
  - Questions whether the "workflows" feature is widely known.
  - Observes that, since MISP is engineer-driven, new features are often motivated by curiosity or technical possibility rather than user need.

---

### Interview 3 — R&D Software Developer / Cryptographer

- **Role:** R&D software developer and cryptographer.
- **Team size:** Three engineers plus a project manager.
- **Background:** Recommended MISP via a colleague; began using it about two months ago.
- **Typical workflow:**
  - Tests open-source software and evaluates protocols.
  - Some light programming.
- **First impression vs. current view:**
  - Initially perceived MISP as highly capable, with many possible use cases.
  - Now feels strongly that users need guidance to be productive.
- **Likes:** Wide range of options; many integrable tools.
- **Dislikes:** Overwhelming surface area; non-intuitive controls (e.g. enabling a workflow requires pressing a "Play" button).
- **Wish list:** Contextual help within the UI.

---

### Interview 4 — Cybersecurity Unit Lead (CTI Aggregation)

- **Role:** Member of a cybersecurity unit focused on threat intelligence aggregation for a large institutional environment.
- **MISP role in workflow:** Main tool and primary ingestion sink for most data.
- **Typical workflow:**
  - Ingests data from five to six paid CTI providers.
  - Acts as an "orchestrator", prioritising events and producing reports based on MISP data.
  - Tracks APTs.
  - Roughly 30% of time spent on internal tooling: improving ingestion, visualisation, etc.
  - Used MISP during the ShinyHunters incidents to track threat actors (data itself came from a separate detection team).
- **Sharing:** Limited — primarily with one trusted partner CERT; otherwise outbound contact is rare.
- **Interface preference:** Mainly accesses MISP through the API.
- **Adoption path:** First encountered MISP at university.
- **Strengths:** Visualisation of intelligence is what initially attracted them to MISP.
- **Frustrations / friction:**
  - MISP's flexibility creates correlation challenges (less guardrails → more ambiguity), e.g. inconsistent threat-actor naming.
  - Graph visualisations become unreadable when references multiply.
  - Lack of strategic-level analysis: "connecting the dots on a higher level" requires increasingly complex searches.
- **Suggestions:**
  - Consider splitting MISP into two distinct applications by use case.
  - Address the long-term challenge of growing data volume.

---

### Interview 5 — Detection-Rule Tool Developer

- **Role:** Developer of a detection-rule tool ("Rulezet"); rules are mostly regex but also other formats such as Wazuh.
- **Integration with MISP:** Tool can import a rule as a MISP object, optionally inside an event.
- **Audience:** Likely to be used by a small subset of MISP users.
- **First experience:** Initial goal was to import a rule as an object, but starting point was unclear; the application felt overloaded for a beginner.
- **Suggestion:** Implement a first-connection / onboarding guide.
- **Reliance:** Depends primarily on the import functionality.
- **Likes:** Translating JSON content directly into a MISP object.
- **Dislikes:** Difficulty performing basic actions such as creating an event.
- **API usage:** Uses PyMISP heavily; would value accessible command examples to ease onboarding.

---

### Interview 6 — CTI Team Lead

- **Role:** Lead of a newly formed CTI team (under one year old, five people), supporting an Incident Response Team of around fifteen people based abroad.
- **Adoption blocker:** Cannot use MISP as much as desired due to internal "new business application" review process.
- **Function of the team:** Supports the IRT but does not perform incident response itself.
- **Typical workflow:**
  - Acts as a passive consumer, collecting information from MISP.
  - Uses MISP as the data exchange layer with the company's IRT.
  - Architecture: one MISP instance aggregates external feeds; a filtering process forwards only true positives to a second instance used by the IRT.
  - Filters via MISP's matching feature.
  - Produces hash lists from the IRT-side instance and shares them with the aggregating instance to check for prior sightings.
  - Goal: enrich the IRT-side instance with externally observed intelligence.
- **Heavy use of:** Feeds.
- **Strong views on tagging:** Considers it one of MISP's most important features because tags can drive workflows.
- **First impression:** Cumbersome and overwhelming.
- **Adoption path:** First encountered MISP through a CIRCL training.
- **Likes:** Feeds and caching.

---

### Interview 7 — R&D Scientist (Tool Integration)

- **Role:** R&D scientist, evaluating MISP for integration with internal tooling.
- **Goal:** Use MISP as a CTI analysis platform supporting semantic queries.
- **Interface preference:** Primarily uses the API rather than the UI.
- **Related project:** Developing an analytics tool ("Decipher x Radar", built into Wazuh) where Radar sends IOCs to Decipher; Decipher then queries the MISP API for events and sightings.
- **Terminology concern:** Questions whether "Sightings" is a clear name for users outside the CTI community (the term means feedback).
- **First impression:** Overwhelmed by the interface.
- **UI impression:** Unclear which actions are possible from a given view.
- **Wish list:**
  - STIX mapping / output currently does not work — should be fixed.
  - An architectural diagram would help newcomers understand the system.
- **Likes:** Broad integration surface; well-maintained codebase.

---

### Interview 8 — Aspiring IOC Author

- **Role:** New user looking for a tool to learn how to create IOCs.
- **Adoption path:** Discovered another tool first, then MISP, and decided to try MISP.
- **Outcome:** Gave up on the same day due to a non-user-friendly interface and feature overload.
- **Experience:** Felt lost; would have liked progressive guidance.
- **Actual usage:** Only added a single IOC; encountered features they did not need (tags, galaxies).
- **Interface preference:** UI user, not interested in the API.
- **Wishes:** More colour and visual diagrams, similar to OpenCTI.
- **Likes:** The application already covers all the features they were hoping for.
- **Dislikes:** The interface is off-putting.
- **Overall rating:** 6–7 out of 10, with deductions attributed entirely to the interface.

---

### Interview 9 — Deployment Engineer

- **Role:** Currently not actively using MISP, but previously involved with deployment.
- **First exposure:** October 2023; used the system for several months.
- **First impression:** Not intuitive; took significant time to understand.
- **Primary usage:** Admin views and configuration sections.
- **Goal:** Deploy MISP inside LXC containers; produced a public repository for this purpose (`misp-airgap`).
- **Deployment experience:** No issue running the application; the difficulty lay in navigating the UI to configure settings and locate the right endpoints.
- **Likes:** Found every needed feature within the application.
- **Dislikes:** Too many menus, sometimes within the same view.
- **Wish list:** A function to export the current configuration of an instance (mentioned twice — clearly a priority).






