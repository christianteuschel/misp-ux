# Top 3 Issues to Tackle First

Based on the interview data, prioritised by frequency across interviews, severity of impact, and how foundational each is for everything else.

## 1. The first-run experience drives users away

The highest-impact issue, because it determines whether MISP gets a chance to deliver value at all. Interview 8 is the starkest case: the user abandoned MISP on day one despite acknowledging it covered all the features they wanted. The product won on features and lost the user anyway.

The same pattern recurs across Interviews 3, 5, 6, 7, and 9 — "overwhelmed", "cumbersome", "too much", "felt lost", "took a lot of time to understand". Different people in different roles converging on the same complaint.

**Tackle:** progressive onboarding, in-UI contextual help (Interview 3's explicit wish), and a guided path to a first successful event (Interview 5). AI-UC5 (contextual assistant) has the highest leverage here at the lowest implementation risk.

## 2. The basic IOC ingestion path has too much friction

The highest-volume workflow in the data — Interview 1's analyst runs it 2–3 times per week, with similar patterns in Interviews 4 and 6. Improvements compound across every analyst's workload.

The friction is concentrated in fixable places: unstructured data must be copy-pasted manually; navigation from preview back to edit can lose information; the "Description" field is actually the name, with no real description field; galaxies and tags are hard to find, which is why Interview 1's analyst skips both.

**Tackle:** fix the field naming, make galaxy and tag selection contextual rather than tree-based, and resolve the preview/edit data-loss bug. AI-UC1 (free-text-to-event extraction) directly automates the most painful step.

## 3. Documentation and knowledge are scattered

Almost every interview raises this. Interview 2 calls it out directly ("not centralized and hard to find"), Interview 3 wants contextual help, Interview 5 wants discoverable PyMISP examples, Interview 7 wants an architectural diagram, and Interview 9 spent significant time hunting for the right configuration endpoints.

Third rather than first because it's a multiplier, not a blocker — but it benefits every persona, so small investments yield broad wins.

**Tackle:** a single canonical documentation entry point, an architectural overview diagram (Interview 7), an examples-first PyMISP guide (Interview 5), and a configuration reference mapping settings to UI locations (Interview 9).

---

## Why not these

- *Synchronisation complexity* (Interviews 2, 6) — real but affects a smaller group; downstream of the documentation issue.
- *Strategic analysis and graph readability* (Interview 4) — the best long-term AI opportunity, but it serves mature users; fixing it before onboarding invests in users who already stayed.
- *STIX export reliability* (Interview 7) — a concrete bug worth fixing, but narrow in scope.

The three above are where multiple personas overlap and where one fix benefits many.