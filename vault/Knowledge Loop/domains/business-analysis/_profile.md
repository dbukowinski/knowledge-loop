---
domain: business-analysis
rhythm: monthly
source_freshness: 12 months
hypothesis_dormancy: 12 weeks
independent_situations: different documents or projects
notes_area: <your BA notes/wiki folder>
---

# Domain profile: business-analysis

> Example profile — adapt the sources, methodology and approval rules to your team.

## Scope
Business and systems analysis, requirements, documentation, stakeholder work, integrations.

## Observation sources (cost ladder)
1. The user's corrections to my analyses (lessons log, tag `business-analysis`).
2. Stakeholder and team feedback relayed by the user.
3. Issues and comments in the issue tracker (follow-up questions, corrections) — only when a hypothesis needs it.
4. Full analysis documents — only for a specific hypothesis.

`source_id`: `issue:<id>`, `vault:<path>`, `lesson:<date>:<n>`, `user:<date>`.

## Guiding methodology
BABOK (IIBA) as the reference + team/organisation standards (to fill in).

## Confounders checklist
Deadline pressure, unclear client requirements, new stakeholder, new business domain, scope change mid-way.

## Requires approval (→ `_proposals.md`)
- Rules changing the structure or scope of analyses delivered to stakeholders.
- Changes to facts about team standards.

## Safety
Production, legal or customer-data risk beats any rule.

## Important dates (no experiments before them)
- Analysis deadlines, releases — list here.
