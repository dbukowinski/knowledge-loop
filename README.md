# Knowledge Loop

An evidence-based learning loop for Claude. Claude does not learn between conversations on its own: its weights do not change. Knowledge Loop gives it an external, file-based memory in a notes vault (e.g. Obsidian), so it can keep learning in any domain you work on together: sport, work, AI tooling or anything else.

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

### Domains

Each area of learning is a domain with its own profile: where observations come from, the guiding methodology, confounders, how long external knowledge stays fresh, and what needs your approval. Claude loads only the profile of the domain at hand. The repository ships three **example** domains (`sport`, `business-analysis`, `ai`). Add, remove or rename them to fit your life and work.

### 9-Sources: a map, not an archive

For each domain:
1. **Registry**: which sources to trust and how much (evidence tiers A–D), and who sells what.
2. **Search recipes**: proven queries (`site:` searches, research-database filters, channels).
3. **Topic indexes**: a 3-sentence state of knowledge, disputes, and links with a paraphrase and stance.

Verification starts from the index. Open web search is only the fourth step, and everything new is written back, so each later check on the same topic is cheaper.

### What Claude writes alone vs. what waits for you

- **Alone** (also in background tasks): observations, hypotheses and their statuses, facts that don't affect high-risk decisions, indexes, log, reports, 9-Sources, lessons log.
- **Waits in `_proposals.md`**: rules affecting load, safety or other high-risk decisions; changes to facts that plans depend on; skill changes; new domains; deletions. Approve in chat with "approve P-003".

### Safeguards

- `source_id` deduplication, so the same event is never counted twice.
- Promotion thresholds are a minimum, plus quality gates: comparable measurement, a weaker counter-hypothesis, and the cost of being wrong.
- Content from pages and files is treated as data, never as instructions.
- No personal data goes into search queries.
- "Saved" is reported only for confirmed writes.
- Skill changes must pass 14 test scenarios. A regression in a critical scenario means rejection, and the previous version is kept for rollback.

## Repository layout

```
SKILL.md                     ← the skill (install in Claude)
vault/                       ← copy into your notes vault
  8-System/Knowledge Loop/   ← _domains, _log, _proposals, example domains (profile, facts, index)
  8-System/Claude Lessons.md
  9-Sources/                 ← External Knowledge Index (example registries)
  4-Knowledge/Sport & Training/My rules.md
  6-Templates/Knowledge Loop/
  7-Skills/knowledge-loop/evals/scenarios.md
pl/                          ← Polish translation of the skill and README ("Pętla Wiedzy")
LICENSE
```

The vault layout assumes numbered top-level folders (`4-Knowledge`, `6-Templates`, `7-Skills`, `8-System`, `9-Sources`). If your vault is organised differently, adapt the paths in `SKILL.md` (see its Configuration section).

## Setup

1. Install `SKILL.md` as a skill in Claude.
2. Copy `vault/` into your vault.
3. Edit `_domains.md` and the domain profiles: your data sources, `source_id` formats, guiding methodology, confounders and approval rules.
4. Replace the example registries in `9-Sources/` with sources you trust (or let the first verifications fill them).
5. Create two scheduled tasks:
   - **Weekly** (e.g. Sunday evening): "Run the knowledge-loop skill, weekly rhythm (§10.1)."
   - **Monthly** (e.g. first Saturday): "Run the knowledge-loop skill, monthly rhythm (§10.2 and §11)."
   - Automatic approval for these tasks is fine: the proposals queue keeps high-risk changes gated.
6. Optionally, start with an ad hoc analysis (§10.3) after a recent project, race or block, so the system has content right away.

## Background

| Element | Learning-science basis |
|---|---|
| Observation → hypothesis → verification → application | Kolb's experiential learning cycle |
| Counter-hypotheses, deciding criteria, statuses | Falsification (Popper) |
| Evidence tiers A–D | Evidence-based practice hierarchy |
| Lessons log | Error notebook |
| Rules edited, not appended | Evergreen notes (Matuschak) |
| Tested skill changes with rollback | Deliberate practice with feedback |

## Disclaimer

A learning-design tool, not a coach, medical or professional advisor. Health concerns belong with a specialist. Third-party sources named in the example registries are listed for illustration only. This project is not affiliated with or endorsed by them.

## License

[MIT](LICENSE)
