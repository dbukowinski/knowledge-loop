---
domain: ai
rhythm: monthly
source_freshness: 3 months
hypothesis_dormancy: 8 weeks
independent_situations: different tasks or skills
wiki_area: 4-Knowledge/AI (to confirm)
---

# Domain profile: ai

## Scope
Prompts, skills, agents, automations, LLM tools, working with Claude.

## Observation sources (cost ladder)
1. User corrections (lessons log, skill tags).
2. Skill evaluation results and rhythm reports.
3. Comparisons of prompt/skill versions — only for a specific hypothesis.

`source_id`: `lesson:<date>:<n>`, `eval:<skill>:<date>`, `vault:<path>`, `user:<date>`.

## Guiding methodology
Official model-provider documentation (prompt engineering, tool use) + own evaluations. A fast-moving field: short freshness window.

## Confounders checklist
Different model or version, changed tools/connectors, different context length, different inputs.

## Requires approval (→ `_proposals.md`)
- Any change to a skill or to the behaviour of scheduled tasks.

## Safety
Unattended automations (scheduled tasks, writes to Drive or the training platform) — behaviour changes only after user approval.
