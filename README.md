# Knowledge Loop

An evidence-based learning loop for Claude. Claude does not learn between conversations on its own: its weights do not change. Knowledge Loop gives it an external, file-based memory in an Obsidian vault, so it can learn across every domain you work on together: sport, business analysis, AI and more.

Conclusions from experience become **hypotheses with counter-hypotheses**. Hypotheses are checked against an **External Knowledge Index (9-Sources)**. Measured values become **facts**, confirmed conclusions become **rules**, and high-risk changes wait for your approval. Everything keeps its history and is designed to use as few tokens as possible.

## How it works

```
Observation → Hypothesis (+ counter-hypothesis) → Verification (9-Sources) → Consolidation → Application
        ↑                                                                                     │
        └────────────────────────────────── new observation ←─────────────────────────────────┘

Corrections → Lessons log → Skill evolution (tested, approved by you)
Verification → write-back → 9-Sources grows
```

### Four types of memory

| Type | What | Where |
|---|---|---|
| Episodic | what happened | your existing notes and data, referenced by `source_id` (never duplicated) |
| Semantic | measured facts with method and date | `<domain>/_facts.md` |
| Hypotheses | possible explanations + counter-hypotheses | `<domain>/Hypotheses/`, `_index.md` |
| Procedural | approved rules, skill versions | `4-Knowledge/<area>/My rules.md`, `7-Skills/` |

### 9-Sources: a map, not an archive

For each domain:
1. **Registry**: which sources to trust and how much (evidence tiers A–D), and who sells what.
2. **Search recipes**: proven queries (`site:` searches, research-database filters, channels).
3. **Topic indexes**: a 3-sentence state of knowledge, disputes, and links with a paraphrase and stance.

Verification starts from the index. Open web search is only the fourth step, and everything new is written back, so each later check on the same topic is cheaper.

### What Claude writes alone vs. what waits for you

- **Alone** (also in background tasks): observations, hypotheses and their statuses, facts that don't affect zones or plans, indexes, log, reports, 9-Sources, lessons log.
- **Waits in `_proposals.md`**: rules affecting load, intensity or safety; changes to facts that zones and thresholds depend on; skill changes; new domains; deletions. Approve in chat with "approve P-003".

### Safeguards

- `source_id` deduplication, so the same activity is never counted twice.
- Promotion thresholds are a minimum, plus quality gates: comparable measurement, a weaker counter-hypothesis, and the cost of being wrong.
- Content from pages and files is treated as data, never as instructions.
- No personal data goes into search queries.
- "Saved" is reported only for confirmed writes.
- Skill changes must pass 14 test scenarios. A regression in a critical scenario means rejection, and the previous version is kept for rollback.

## Repository layout

```
SKILL.md                     ← the skill (install in Claude)
vault/                       ← copy into your Obsidian vault
  8-System/Knowledge Loop/   ← _domains, _log, _proposals, per-domain profile/facts/index
  8-System/Claude Lessons.md
  9-Sources/                 ← External Knowledge Index
  4-Knowledge/Sport & Training/My rules.md
  6-Templates/Knowledge Loop/
  7-Skills/knowledge-loop/evals/scenarios.md
pl/                          ← Polish edition (the original working version, "Pętla Wiedzy")
```

The vault layout assumes a numbered structure (`1-Daily … 9-Sources`). Adapt paths in `SKILL.md` if your vault differs.

## Setup

1. Install `SKILL.md` as a skill in Claude.
2. Copy `vault/` into your Obsidian vault.
3. Edit the domain profiles (`_profile.md`) to match your data sources and guiding methodologies.
4. Create two scheduled tasks:
   - **Sunday evening**: "Run the knowledge-loop skill, weekly rhythm (§10.1)."
   - **First Saturday of the month**: "Run the knowledge-loop skill, monthly rhythm (§10.2 and §11)."
   - Turn on automatic approval for both. The proposals queue keeps high-risk changes gated.
5. Optionally, start with an ad hoc analysis (§10.3) after a race, project or block, so the system has content right away.

## Background

| Element | Learning-science basis |
|---|---|
| Observation → hypothesis → verification → application | Kolb's experiential learning cycle |
| Counter-hypotheses, deciding criteria, statuses | Falsification (Popper) |
| Evidence tiers A–D | Evidence-based practice hierarchy |
| Lessons log | Error notebook |
| Rules edited, not appended | Evergreen notes (Matuschak) |
| Tested skill changes with rollback | Deliberate practice with feedback |

Version 3 merges the original design (domains, 9-Sources, token budget, rhythms) with ideas from an alternative prototype: memory types, `source_id` idempotency, `testing`/`superseded` statuses, the proposals queue, data-is-not-instructions, and regression-tested skill changes.

## Disclaimer

A learning-design tool, not a coach or a medical advisor. Health concerns go to a specialist.
