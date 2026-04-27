# Use Cases

The interviews surface several recurring use cases. Each is described below in terms of context, workflow, and observed challenges.

## UC1 — Incident-Driven IOC Ingestion and Correlation

Analysts receive IOCs from external parties — most often by email and in unstructured form — and need to convert this raw input into structured, correlatable threat intelligence. The typical pattern is to open a new MISP event tied to a ticket number, paste the IOCs through the batch import tool to produce one attribute per line, and apply a TLP tag to define sharing constraints. The IDS flag then controls whether attributes are pushed to detection equipment.

The value of MISP in this workflow comes from automatic correlation: once attributes are ingested, the analyst immediately sees whether the new indicators relate to past events, which directly informs the response sent back to the reporting party. This is one of the most frequently performed workflows and is heavily affected by friction in the basic event-creation path.

Pain points cluster around the creation step itself: data arrives unstructured, copy-paste is manual, navigation between preview and edit views can lose information, and field naming (notably "Description" being used for the name) creates confusion for analysts who want to enrich events properly.

## UC2 — Multi-Instance Synchronisation and Filtered Sharing

Several organisations operate more than one MISP instance and use synchronisation to move intelligence between them. A common pattern is to dedicate one instance to broad feed collection and a second instance to high-confidence intelligence used by an operational team — for example, an Incident Response Team in a different country or business unit. A filtering mechanism (often based on MISP's matching feature) forwards only true positives between instances.

The workflow also includes a reverse path: the operational instance produces hash lists of locally observed indicators, which are returned to the collection instance to check whether the same artefacts have been seen by other parties. The end goal is mutual enrichment.

The friction in this use case lies in the setup and operation of synchronisation: it is reported as complex, and documentation on it is scattered. Once running, however, it becomes a backbone for the organisation's CTI flow.

## UC3 — Programmatic CTI Aggregation via API

A distinct class of users barely interacts with the MISP UI. They aggregate intelligence from multiple paid CTI providers, ingest it into MISP through APIs (often PyMISP), and then build downstream pipelines for prioritisation, reporting, and integration with tools such as Wazuh. MISP serves as the central ingestion sink and a queryable backend for analytical applications.

These users value MISP's extensibility and its position as a de-facto integration hub. Their daily work involves writing custom code, mapping data into MISP objects, and serving it back out through semantic or structured queries to other systems.

The challenges they face are different from UI users: STIX mapping reliability, the readability of the relationship graph at scale, the absence of strong guardrails (which makes correlation across providers harder, particularly around inconsistent threat-actor naming), and the lack of accessible API examples to onboard new team members.

## UC4 — Phishing Investigation

A frequent and well-defined scenario is investigating phishing attempts reported by employees or partners. The analyst creates a MISP event containing a structured object representing the email itself and a second object representing the phishing site, then enriches both with related attributes. Correlation reveals whether the campaign has been observed before and whether infrastructure overlaps with prior incidents.

This use case is small enough to be handled rapidly but common enough that even small UX improvements compound significantly across an analyst's workload. It is also a reporting trigger: incidents involving personal data may require notifying the national data protection authority, which adds a compliance dimension to the workflow.

The main inefficiency is the manual nature of object construction: the analyst still has to identify the relevant fields and structure the data themselves, even though phishing emails follow highly recognisable patterns.

## UC5 — Detection-Rule Authoring and Import

A specialised but important use case is the authoring of detection rules (regex, Wazuh, and other formats) and their integration into MISP as objects, optionally embedded in events. Tools external to MISP — such as the rule-authoring tool described in Interview 5 — translate rule definitions into MISP objects via the API, and rely on MISP for distribution and correlation with related intelligence.

This use case caters to a smaller user base, but it sits at an important intersection: detection rules are operational artefacts that must remain tightly coupled to the intelligence that justifies them. Storing both in the same system enables traceability.

The dominant pain point reported here is onboarding: new users of this workflow find MISP overloaded and struggle to perform basic actions like creating their first event. Better example-driven documentation for PyMISP is the most concrete request.

## UC6 — Deployment, Configuration, and Operations

A non-analyst use case is the deployment and configuration of MISP itself — including air-gapped deployments, container-based installations (Docker, LXC), and instance-level operational tasks. These users live primarily in the admin and settings areas of the UI.

Their experience is shaped less by analytical capabilities and more by the discoverability of configuration. Even when the relevant feature exists, finding it can take hours, and there is no straightforward way to export the configuration of an instance for backup, audit, or replication purposes.

Improving this use case is foundational: every other use case depends on a correctly configured instance, and operators are often the first contact a new organisation has with MISP.

## UC7 — Strategic-Level Threat Analysis

Beyond operational IOC handling, more mature CTI teams want to move "up the stack" toward strategic analysis: connecting actors, campaigns, sectors, and infrastructure into a higher-level picture. Today, this requires increasingly complex queries and manual harmonisation of inconsistent data — for example, reconciling the many names a single threat actor receives across different feeds.

The relationship graph is the natural vehicle for this use case but becomes unreadable as references multiply. Users interested in strategic analysis perceive MISP as data-rich but lacking the synthesis layer that would let them surface high-signal patterns without writing custom analytics.

This is the use case most likely to benefit from new capabilities, including AI-supported approaches discussed below.

---

## AI-Supported Use Cases

Several friction points across the interviews map naturally onto capabilities that LLMs and related AI techniques are well-suited to provide. The use cases below are derived from the pain points raised by interviewees and are framed as concrete, scoped opportunities rather than open-ended automation.

### AI-UC1 — Unstructured-to-Structured IOC Extraction

Multiple analysts described the same starting point: an email containing IOCs in free-form text. The current workflow involves manually copy-pasting and using the batch import tool to produce one attribute per line. An LLM-based extractor could ingest raw email content (or any free-form report) and propose a fully populated draft MISP event — including IP addresses, domains, hashes, suggested object types (email, URL, file), TLP tag, and IDS flag defaults — for the analyst to validate and publish.

Because analysts already validate every event before publication, the human-in-the-loop pattern is a natural fit, and the UX gain is substantial. This single capability addresses the most frequently described workflow in the interviews (UC1 and UC4).

### AI-UC2 — Galaxy and Taxonomy Suggestion

Interview 1 directly raised the difficulty of finding the right galaxy: a search field would help, but contextual suggestions would help more. An LLM can read the content of an event (object types, attribute values, free-text descriptions) and propose the most relevant galaxies, taxonomies, and tags, ranked by confidence. The analyst sees a short list of suggestions in context rather than navigating a tree.

This is also a soft solution to the under-tagging problem observed in Interview 1, where the analyst simply does not use tags. Lowering the activation energy makes well-tagged events the default rather than an extra effort.

### AI-UC3 — Threat-Actor Name Harmonisation

Interview 4 described the challenge of working across multiple paid CTI providers, each with its own naming for the same threat actor. This is a classic entity-resolution problem and a good fit for LLM-based reasoning combined with structured aliases. An AI-assisted reconciliation layer could propose merges, flag likely duplicates, and surface the canonical name in views and exports — making correlation across feeds materially more reliable.

This directly enables UC3 (programmatic aggregation) and UC7 (strategic analysis), where naming inconsistency is the most visible obstacle.

### AI-UC4 — Strategic Synthesis and "Connecting the Dots"

The most ambitious AI opportunity is in strategic-level analysis. Today, surfacing high-level patterns requires writing complex queries by hand. An AI assistant grounded in the user's own MISP instance could answer questions such as "which actors target our sector this quarter", "what infrastructure overlaps between these two campaigns", or "what has changed about this actor in the last month", returning narrative summaries with citations back to the underlying events and attributes.

Crucially, the value depends on grounding: answers must be traceable to specific events and attributes, not generated from general knowledge. This both addresses the UC7 gap and turns the unreadable-graph problem (Interview 4) into a tractable one — the AI traverses the graph; the user reads the synthesis.

### AI-UC5 — Contextual Help and Onboarding

Several interviews (3, 5, 7, 8) converged on the same observation: MISP is powerful but overwhelming, and the UI does not guide users toward the next sensible action. An LLM-based contextual assistant — aware of the current view, the current event, and recent actions — could answer questions like "how do I publish this event?", "what should I tag here?", or "why is this attribute not being exported?" without sending the user to external documentation.

This is the lowest-risk AI capability and probably has the highest impact on first-time-user retention. Interview 8, where the user abandoned MISP within a single day, is the clearest evidence of the cost of the current learning curve.

### AI-UC6 — Automated Object Construction for Common Patterns

Phishing investigations (UC4) follow a highly repeatable structure: an email object plus a phishing-site object, plus a small set of related attributes. An AI-driven "create from template" function could parse a forwarded phishing email and generate the full set of objects and relationships in one step, leaving only validation to the analyst. The same pattern generalises to other recurring incident shapes (malware delivery, credential leak, fraudulent domain).

### AI-UC7 — Translating between API and Natural Language

For users who lean on the API (Interviews 4, 5, 7), an AI capability that translates natural-language requests into PyMISP code (and vice versa) addresses both the lack of accessible examples and the steep onboarding curve for new team members. It complements rather than replaces documentation, by producing examples on demand from the user's actual instance schema.