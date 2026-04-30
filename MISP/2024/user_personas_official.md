# MISP User Personas

Source: https://www.circl.lu/doc/misp/user-personas/ (last modified: 2024-10-02)

These personas are fictitious but are concrete representations of the people using MISP. They are derived from OSINT on current MISP users (Gitter chats, GitHub issues, LinkedIn) and other sources of information about cybersecurity.

---

## Primary Personas

Farrah and Adam represent the users that are the most important.

### Farrah — The Threat Hunter

**Role:** Lead Threat Intelligence Analyst

Farrah works as a threat intelligence analyst for a security service provider that offers a range of cybersecurity solutions. He leads a threat intelligence team made up of experienced analysts who are former military/government employees and contractors.

Farrah uses MISP to analyse malware, gather information about specific adversary groups, and discover emerging threats. He also uses MISP for data normalisation (consolidating data across different source formats), de-duplication (removal of duplicate information), and enrichment (removal of false positives, scoring of indicators, and the addition of context).

*"In order to effectively address threats, you must maintain a team focused on monitoring, generating and triaging alerts."*

**Primary goals:**
- Hunt down threats, analyse malware, manage vulnerabilities, and prevent attacks against ICT infrastructures, organisations, or people.
- Improve security posture through the aggregation, correlation, and analysis of threat data from multiple sources.
- Investigate and understand adversarial capabilities, infrastructure, and TTPs.
- Turn threat data from various sources into actionable threat intelligence.

**He uses MISP to:**
- Dispatch notifications containing IoCs to various parties via mail_to_misp.
- Monitor feeds for indicators and correlate attributes; analyse malware (check ransom notes, look for indicators, check origin, etc.).
- Store attack info in a structured format and allow for automated use of the database via the API.
- Prioritise indicators using sighting reports and purge false positives using warning lists.
- Classify and contextualise data using taxonomies and galaxies; track the advancement of analyses using tags.
- View and visualise events and activities using MISP-dashboard or Maltego.
- Automatically import, aggregate, compare, contextualise, query, and cross-reference data using PyMISP.
- Import, export, and enrich data using MISP modules.
- Aggregate, curate, and validate indicators from various feeds, then feed the data into detection and analysis tools like NIDS, IDS, and SIEMs.
- Query vulnerability scan results in MISP, automatically create/classify events on matching results, then create blocklists by excluding attributes that exist on warning lists.
- Collaborate with others in a sharing community using Proposals, Extended Events, and Event Reports.
- Share and receive reports of specific threats, false positives, or post-mortem analyses of incidents from sharing groups.

**Objectives:**
- Join relevant sharing communities, produce and publish indicators, and share information across sectors to avoid hybrid threats.
- Use IoCs from feeds to identify vulnerabilities, compromised assets, and data leaks, and to verify malware scan results.
- Triage threat intel, prioritise vulnerabilities, and customise risk feeds to ignore or downgrade irrelevant alerts to avoid alert fatigue.
- Generate and share alerts to provide critical information to internal teams and external peers.
- Research the evolution of high-risk malware families; validate malware signatures and domain reputations.
- Use indicators to query security logs/systems and databases, identify compromised systems, and add/modify signatures used by firewalls and intrusion detection systems.
- Correlate shared indicators from feeds with those captured by other security and network tools to produce intelligence in the context of wider threat landscapes.
- Integrate with existing security solutions to centralise security in one place (AIL 2, McAfee OpenDXL, ATT&CK, MVISION EDR, Cytomic Orion, Carbon Black).

---

### Adam — The Remediator

**Role:** Incident Response

Adam is part of the Computer Security Incident Response Team (CSIRT) at a cybersecurity consulting firm. His responsibilities involve incident response, incident coordination, threat intelligence, and vulnerability management. He monitors potential threats, investigates attacks, and works with other security personnel to reduce the impact and severity of an attack.

Adam uses MISP to monitor incidents, provide early warnings and alerts, respond to incidents, and provide incident analysis and situational awareness.

*"A breach alone is not a disaster, but mishandling it is. The goal is to handle the situation in a way that limits damage and reduces recovery time and costs."*

**Primary goals:**
- Uncover the effects of attacks, determine how to clean up their impact, and inform a response to an existing incident to mitigate its extent or impacts.
- Develop and maintain strong processes for the most common incidents and threats, and create actionable results and remediation plans for internal stakeholders.
- Accelerate incident investigations, management, and prioritisation by looking for information on the who/what/why/when/how of an incident.
- Determine the scope of incidents and limit the potential damage.

**He uses MISP to:**
- Store incidents as a database of events, describe incidents through event classification (using taxonomies and galaxies), and use the API to deduce the current operational status, risk posture, and threats to the cyber environment.
- Join sharing groups and communities to share incident information and discuss associated risks via forums, event comments, and direct contact.
- Analyse observables and malware collected during an incident, determining whether they are IoCs or false positives using the correlation graph and expansion modules.
- Alert and send emails when events are created or major changes occur, serving as part of an early warning system.
- Pull events via the API or export IoCs in formats for easy ingestion into other tools (SIEMs, IDS) and carry out investigations by launching lookups against databases.
- Collaborate with and get feedback from team members and affected parties during incident response using Proposals.
- Dismiss false positives (using warning lists) and enable alert prioritisation.
- Aggregate and compare information from internal and external feeds to identify genuine threats.
- Perform large-scale data/traffic analysis and correlation through lookups against SightingDB.
- Share, receive, store, and forward incidents and information identified during an investigation, enabling MISP to act as a forensic tool over time.
- Correlate and reference network forensic flows from different tools or network equipment.
- Speed up incident response via integration with TheHive.

**Objectives:**
- Share information and get critical alerts and relevant actionable information in the event of a crisis situation.
- Support forensic analysts and collaborate with law enforcement.
- Improve incident response functionality and increase coverage and detection through integrations with tools like SIEMs.
- Use threat data to validate alarms/events and decide which to escalate to the incident response team for remediation.
- Aggregate information from various sources and correlate it to understand how data fits together in the broader threat landscape.
- Get insights (e.g. from data feeds) into attacks, helping incident response teams understand the nature, intent, and timing of specific attacks.
- Prioritise incidents based on risk and impact to the organisation, and filter out false alerts.

---

## Secondary Personas

Tina, Henry, Jacob, and Jay represent other users that are also important.

### Tina — The Fraud Catcher

**Role:** Fraud Analyst

Tina works as a fraud analyst at a national bank. She is responsible for investigating forgery and theft within customers' accounts and transactions.

Tina uses MISP to find and share financial indicators in order to detect financial fraud.

*"Fighting fraud with threat intelligence is all about alerting."*

**Primary goals:**
- Identify and trace fraudulent activity.
- Create models for analysing and determining financial fraud in order to protect consumers and stakeholders.
- Assess and analyse the attack surface, conduct threat modelling, and deliver actionable intelligence with a focus on current and emerging cyber-attacks against financial sector assets.

**She uses MISP to:**
- Map legacy and internal systems/models using MISP objects.
- Find IoCs, malware, vulnerabilities, financial threat information, and fraud data, and share it between banks and financial institutions using sharing groups.
- Create, modify, and visualise the timeline of events; use MISP Dashboard to provide real-time information on current threats and activity.
- Minimise false positives during the fraud vetting process using warning lists and sightings.
- Detect fraud using threat intel such as real-time notifications for stolen credit cards and phishing URLs from MISP feeds.
- Prevent fraud by integrating MISP with a network of crawlers, honeypots, and other techniques that cross-reference indicators against feeds.
- Monitor feeds for specific indicators (e.g. email header content, attachments, embedded URLs) related to phishing and fraud attacks.
- Block wire transfers to money mule accounts by integrating MISP warning lists and sightings with blocking systems.
- Aggregate sightings of attributes/objects to detect particular security events or threats.

**Objectives:**
- Investigate financial indicators and handle false positives in order to detect and alert for potentially invalid data points.
- Aggregate, correlate, and analyse financial indicators from multiple feeds to discover fraudulent activity.
- Blend threat intel from MISP with anti-fraud tools to identify and prevent fraud in real-time.
- Use threat intel to produce awareness reports informing the institution of threats in the financial sector, and develop proactive defence strategies.
- Engage with sharing communities that allow individual enterprises to receive and share data so they can protect themselves before they are compromised.

---

### Henry — The Enforcer

**Role:** Law Enforcement Officer

Henry works with a Digital Forensics and Incident Response (DFIR) team. He is responsible for investigating digital security incidents, identifying digital assets targeted during attacks, and documenting all findings.

He uses MISP to support or bootstrap his DFIR cases.

*"I worry about what I don't know, not what I know."*

**Primary goals:**
- Find, gather, and analyse digital evidence for criminal investigations.
- Carry out data breach and malware investigations.

**He uses MISP to:**
- Propose changes to existing analyses or reports.
- Correlate (1-to-1 value matches, fuzzy hashing, CIDR block matching) evidence against external/local attributes.
- Correlate and reference network forensic flows from different tools or network equipment using the community-id feature.
- Export data in various formats to feed into and look up in other security tools.
- Join sharing groups and collaborate with other investigators.
- Receive, gather, analyse, and share intelligence on digital crimes.
- Report digital evidence (in STIX) in a structured way for forensic use.
- Collect evidence for forensic analysis from feeds, using shared indicators to carry out cybercriminal behaviour investigations, attribution, and identification of links to organised crime.
- Exchange, store, and forward incidents and information identified during an incident investigation, enabling MISP to act as a forensic tool over time.

**Objectives:**
- Share indicators, analyses, and reports of forensic evidence among law enforcement officers within and outside his team.
- Collaborate with CSIRTs/CERTs and security researchers in the investigation of cyberattacks.
- Correlate data identified in a recent incident with data from previous investigations or external feeds.
- Bridge their use cases with MISP's information-sharing mechanism.

---

### Jacob — The Veteran

**Role:** Cybersecurity Consultant

Jacob is a cybersecurity consultant who has founded a cybersecurity agency providing threat intel and security consulting services to small and medium-sized businesses. He typically wants to integrate MISP into existing client solutions.

Jacob uses MISP to investigate threats and find IoCs.

*"There's a difference between threat data and threat intelligence."*

**Primary goals:**
- Produce intelligence that will be embedded into organisational workflows and serve decision-makers.
- Scope and implement custom security solutions across a variety of client software, architectures, and tools.
- Detect, contain, and remediate cybersecurity incidents, manually or programmatically.

**He uses MISP to:**
- Create, collaborate, automate, and share threat intel using flexible sharing groups, automatic correlation, the free-text import helper, event distribution, and proposals.
- Allow users to notify a MISP instance about activities related to an indicator using sightings (sourced from SIEMs, NIDS, honeypot devices, etc.).
- Monitor feeds delivered through a REST API and correlate IoCs with firewall and other logs to identify potential threats.
- Push/pull events between local and client MISP instances to exchange intel internally and externally.
- Import, export, and enrich data using modules; automate such tasks using PyMISP.
- Create sub-communities and MISP object templates to allow rapid sharing of information using specific data models with existing communities.
- Validate data and flag false positives using warning lists and sightings.
- View live data and statistics and process information in real-time through integration with ZMQ and MISP-dashboard.
- Pseudo-anonymously publish data using the MISP delegation system.
- Contextualise shared information using taxonomies and tags; attach more complex structures to data using MITRE ATT&CK and other galaxies.

**Objectives:**
- Run a Cyber Threat Intel platform using MISP integrated with existing client solutions (e.g. Active Directory, Splunk ES, ThreatConnect, Recorded Future, CrowdStrike).
- Gather unstructured data from various sources and connect the dots to provide context on IoCs and TTPs of threat actors.
- Identify incoming threats, triage, and prioritise alerts as they emerge.
- Feed SIEMs from MISP and feed MISP from other sources (including SIEMs).
- Share incidents and IoCs for detection, blocking, and intelligence gathering purposes.

---

### Jay — The Inquisitor

**Role:** Risk Analyst

Jay is a risk analyst for a large technology company. He is responsible for identifying and predicting risks, as well as forecasting the cost of certain attacks to the organisation.

Jay uses MISP data to learn about the broad threat landscape and analyse the likelihood of certain risks in order to gain situational awareness.

*"The more certain you can be about the probability of a specific exploit impacting your environment, the easier it is to manage risk."*

**Primary goals:**
- Improve the organisation's security posture, situational awareness, and resilience.
- Forecast evolving threats before they materialise, provide detailed insights into which vulnerabilities pose the greatest risk, and plan accordingly.
- Assess business and technical risks, identify the right strategies and technologies to mitigate them, communicate the nature of the risks to top management, and justify investments in defensive measures.

**He uses MISP to:**
- Monitor trends and adversary TTPs within the company's sector/geographical region; share and track information emerging on a particular topic from the MISP dashboard to gain situational awareness.
- Monitor IoCs from various technical feeds and add additional context to internal data sources using the automatic correlation engine.
- Access risk scores using correlation and sightings.
- Present data using different export formats, event reports, and the MISP dashboard timeline.

**Objectives:**
- Use shared indicators to perform risk assessments, identify key information/assets, and illustrate the intent/capability of actors to target these assets through impact assessments.
- Score threats according to the organisation's specific needs and prepare processes in advance based on threat data gathered from feeds.
- Present data to stakeholders in various formats — articles, timelines, graphs, raw data — depending on their technical knowledge.
- Gain shared situational awareness through information sharing and collaboration with other experts in the same sector.

---

### Sarah — The Fact Checker

**Role:** Disinformation Researcher and Journalist

Sarah is a disinformation researcher and journalist working for a large newspaper. She works with security researchers around the world to investigate cybercrimes and report disinformation. She has written about national security and geopolitics, and is used to making decisions on what should or shouldn't be published or shared.

Sarah uses MISP to collaborate with security researchers and investigate disinformation as it happens.

*"Decisions as to what is or isn't published or shared go far beyond what is technically interesting."*

**Primary goals:**
- Conduct research and write intelligence reports about up-and-coming emerging threats and recent breaches.
- Investigate and report disinformation as it happens.
- Convert technical data into articles and reports that non-technical people can understand.

**She uses MISP to:**
- Write and read event reports; create misinformation events using relevant techniques found in a report or sighting.
- Join sharing groups and communities (e.g. CogSec Collab) that connect misinformation researchers and responders; share incident data with organisations focusing on response and counter-campaigns.
- Integrate with the AM!TT Framework (as a galaxy) to describe misinformation tactics/techniques, break an incident into techniques that can be analysed/countered, and check for disinformation through mapping.
- Monitor feeds, investigate disinformation using shared indicators in feeds, generate structured intelligence using the automated correlation engine, and decide if there are any falsehoods in data.
- Enrich threat data by adding object types, new relationship types, and taxonomies to cover things like types of threat actors.
- Classify events, indicators, and threats using taxonomies such as the Admiralty Scale, which ranks the reliability of a source and the credibility of the information.

**Objectives:**
- Distil essential information from large pieces of data, making it clear to the reader what really matters.
- Integrate MISP with TheHive for enhanced disinformation investigation and reporting.
- Verify that an article, image, or video doesn't contain disinformation, and verify that a source (publisher, domain, etc.) doesn't distribute disinformation.
- Extend MISP for disinformation by adding object types for incidents and narratives, and using AMITT for attack patterns.

---

## Other Personas

Malcolm represents users that matter but are lower priority.

### Malcolm — The Data Expert

**Role:** Data Scientist

Malcolm is a data scientist for a telecom operator. He assists the Security Operations Center with tasks related to anomaly detection, exploratory data analysis, data visualisation, modelling, and optimisation of security solutions.

Malcolm uses data from MISP alongside natural language processing, predictive modelling, and other data science techniques to assess, prioritise, and even predict risk.

*"It is a mistake to theorise before one has data. Insensibly, one begins to twist facts to suit theories, instead of theories to suit facts."*

**Primary goals:**
- Develop tools to help businesses detect threats so they can develop solid plans of action and better protect themselves.
- Make predictions, perform data analysis, and detect patterns in data.
- Support the threat analysis team with new and innovative ways of extracting insight from large sets of structured and unstructured data.
- Translate complex data into relevant insights and visualise information.

**He uses MISP to:**
- Collect IoCs and sift through data from feeds to derive useful insights and connect dots between actors from various sources.
- Join sharing groups to collaborate with threat analysts and reduce analysts' workloads by taking on tasks related to data collection and correlation.
- Automatically aggregate, parse, de-duplicate, and manage indicators using the API.
- Visualise events in real-time by setting up MISP-dashboard.
- Export large threat data sets that can be used to train ML models.

**Objectives:**
- Combine data from MISP and other security sources to find patterns/relationships, develop models, and assess, prioritise, and predict risk using data science and AI techniques.
- Produce informative visualisations and knowledge graphs based on large data sets.
- Eliminate manual tasks by writing scripts that automatically aggregate, parse, de-duplicate, and manage indicators in MISP.
- Classify risks in order to save analysts time sorting through false positives and deciding what to prioritise.