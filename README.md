# Knowledge Loop

An evidence-based learning loop for Claude. Claude does not learn between conversations on its own: its weights do not change. Knowledge Loop gives it an external, file-based memory in a notes vault (e.g. Obsidian), so it can keep learning in any domain you work on together: sport, work, AI tooling or anything else.

Conclusions from experience become **hypotheses with counter-hypotheses**. Hypotheses are checked against an **External Knowledge Index** (`sources/`). Measured values become **facts**, confirmed conclusions become **rules**, and high-risk changes wait for your approval. Everything keeps its history and is designed to use as few tokens as possible.

The whole loop lives in **one self-contained folder**, `Knowledge Loop/`. You can drop it into any vault (a numbered "second brain", PARA, Zettelkasten or a plain notes folder) without renaming anything you already have.

## How it works

```
Observation → Hypothesis (+ counter-hypothesis) → Verification (Sources index) → Consolidation → Application
        ↑                                                                                          │
        └──────────────────────────────────── new observation ←────────────────────────────────────┘

Corrections → Lessons log → Skill evolution (tested, approved by you)
Verification → write-back → the Sources index grows
```

### Four types of memory

| Type | What | Where (inside `Knowledge Loop/`) |
|---|---|---|
| Episodic | what happened | your existing notes and data, referenced by `source_id` (never duplicated or moved) |
| Semantic | measured facts with method and date | `domains/<domain>/_facts.md` |
| Hypotheses | possible explanations + counter-hypotheses | `domains/<domain>/Hypotheses/`, `_index.md` |
| Procedural | approved rules, skill versions | `domains/<domain>/rules.md`, `skills/` |

### Domains

Each area of learning is a domain with its own profile: where observations come from, the guiding methodology, confounders, how long external knowledge stays fresh, and what needs your approval. Claude loads only the profile of the domain at hand. The repository ships three **example** domains (`sport`, `business-analysis`, `ai`). Add, remove or rename them to fit your life and work.

### The Sources index: a map, not an archive

For each domain:
1. **Registry**: which sources to trust and how much (evidence tiers A–D), and who sells what.
2. **Search recipes**: proven queries (`site:` searches, research-database filters, channels).
3. **Topic indexes**: a 3-sentence state of knowledge, disputes, and links with a paraphrase and stance.

Verification starts from the index. Open web search is only the fourth step, and everything new is written back, so each later check on the same topic is cheaper.

### What Claude writes alone vs. what waits for you

- **Alone** (also in background tasks): observations, hypotheses and their statuses, facts that don't affect high-risk decisions, indexes, log, reports, the Sources index, the lessons log.
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
SKILL.md                          ← the skill (install in Claude)
vault/Knowledge Loop/             ← copy this folder into your vault
  _domains.md, _log.md, _proposals.md, lessons.md
  domains/<domain>/               ← _profile, _facts, _index, rules (+ Hypotheses/, Reports/)
  sources/                        ← External Knowledge Index (_guide + per-domain registries)
  templates/                      ← hypothesis, source topic, domain profile, report, lesson, skill version
  skills/knowledge-loop/evals/    ← 14 test scenarios
pl/                               ← Polish translation of the skill and README ("Pętla Wiedzy")
LICENSE
```

## Setup

1. Install `SKILL.md` as a skill in Claude.
2. Copy `vault/Knowledge Loop/` anywhere in your vault.
3. Edit `_domains.md` and the domain profiles: your data sources, `source_id` formats, guiding methodology, confounders, approval rules, and the `notes_area` where your own notes for that domain live.
4. Replace the example registries in `sources/` with sources you trust (or let the first verifications fill them).
5. Create two scheduled tasks:
   - **Weekly** (e.g. Sunday evening): "Run the knowledge-loop skill, weekly rhythm (§10.1)."
   - **Monthly** (e.g. first Saturday): "Run the knowledge-loop skill, monthly rhythm (§10.2 and §11)."
   - Automatic approval for these tasks is fine: the proposals queue keeps high-risk changes gated.
6. Optionally, start with an ad hoc analysis (§10.3) after a recent project, race or block, so the system has content right away.

## Inspiration and compatibility

Knowledge Loop grew out of a vault built on the **LLM knowledge base** idea popularised by Andrej Karpathy: raw material goes into the vault and an LLM compiles and maintains a linked wiki from it. The concrete vault it was first used with follows the numbered layout of **[Super Brain](https://github.com/superhero-tech/super-brain)** ("Product Builder Second Brain", by Superhero.tech / AI Product Heroes). Knowledge Loop adds a learning layer on top: hypotheses, evidence, rules and an external knowledge index. It is a separate, independent project, not affiliated with or endorsed by Superhero.tech or Andrej Karpathy.

Knowledge Loop deliberately uses **no numbered folders**, so it never collides with an existing layout, including Super Brain's `9-Outputs`. If you prefer to spread its pieces across a numbered vault, this mapping works well. Update the paths in `SKILL.md` to match.

| Knowledge Loop (default) | Numbered vault (e.g. Super Brain) |
|---|---|
| `Knowledge Loop/` (router, log, proposals, lessons, domains) | `8-System/Knowledge Loop/` |
| `domains/<domain>/rules.md` | `4-Knowledge/<area>/Rules.md` |
| `sources/` | `4-Knowledge/_Sources/` |
| `templates/` | `6-Templates/Knowledge Loop/` |
| `skills/<skill>/` | `7-Skills/<skill>/` |
| `local:` pointers | summaries in `4-Knowledge/`, raw files in `5-Raw/` |

Other foundations:

| Element | Learning-science basis |
|---|---|
| Observation → hypothesis → verification → application | Kolb's experiential learning cycle |
| Counter-hypotheses, deciding criteria, statuses | Falsification (Popper) |
| Evidence tiers A–D | Evidence-based practice hierarchy |
| Lessons log | Error notebook |
| Rules edited, not appended | Evergreen notes (Matuschak) |
| Tested skill changes with rollback | Deliberate practice with feedback |

## Disclaimer

A learning-design tool, not a coach, medical or professional advisor. Health concerns belong with a specialist. Third-party sources named in the example registries are listed for illustration only.

## License

[MIT](LICENSE)
