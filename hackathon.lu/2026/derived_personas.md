# Personas

Six recurring personas emerge from the interviews. They are not mutually exclusive — some users span more than one — but each captures a distinct relationship with MISP and a distinct set of expectations.

## P1 — The Incident-Response Analyst

A hands-on practitioner who uses MISP several times per week to log, correlate, and share IOCs received from external parties. Comfortable with the core event/attribute model but indifferent to advanced features like tags, galaxies, and workflows. Values speed in the basic creation path and is highly sensitive to UX friction in copy-paste-heavy work. *Represented by Interview 1.*

## P2 — The CTI Team Lead

Manages a small team and is responsible for the broader CTI operation rather than day-to-day analysis. Often a passive consumer of MISP data, focused on its role as a data exchange and filtering layer between organisational units or partners. Values feeds, caching, tagging, and workflow integration. Constrained by organisational processes around new tooling. *Represented by Interview 6.*

## P3 — The Strategic CTI Practitioner

Operates at scale, ingesting data from multiple paid CTI providers and using MISP as the central aggregation point. Prefers the API to the UI, has strong opinions about correlation quality and visualisation, and is most affected by the lack of guardrails. Wants MISP to support higher-level analysis, not just operational IOC handling. *Represented by Interview 4.*

## P4 — The Integrator / API User

A developer or scientist who treats MISP as a programmable platform. Builds tools that read from and write to the MISP API, integrates MISP with other systems (Wazuh, internal analytics, detection-rule tools), and rarely uses the UI. Cares about API stability, documentation, examples, and the correctness of mappings such as STIX export. *Represented by Interviews 2, 5, and 7.*

## P5 — The Operator / Deployment Engineer

A non-analyst who is responsible for installing, configuring, and maintaining MISP instances — often in constrained environments such as air-gapped or container-based deployments. Spends most of their time in admin and settings views. Cares deeply about configuration discoverability, exportability, and operational predictability. *Represented by Interview 9, with elements in Interview 2 (Docker-based deployment).*

## P6 — The Newcomer

A user with limited prior exposure who arrives with a specific small goal — often "learn how to create IOCs" or "import a single rule". Forms an opinion of MISP within minutes and is highly likely to abandon the tool if the path to that first goal is unclear. Values progressive guidance, visual cues, and a friendly first-run experience over breadth of capability. *Represented by Interviews 3, 5, and most starkly Interview 8.*