# Docforge Sync

[![Available on MyClaude](https://myclaude.sh/badge/available.svg)](https://myclaude.sh/p/docforge-sync)

Documentation drift detection + verification — computes DDS-1 (6-component Doc Drift Score), runs doctest dispatch (pytest-markdown-docs / cargo test --doc / mdbook test / Go testable examples), Vale prose lint with custom rules (hedge soup, anonymous best-practice, redaction), lychee link check, frontmatter schema validation, schema-derive (Pydantic / OpenAPI / Protobuf / GraphQL → reference docs).

| | |
|---|---|
| **Category** | skills |
| **Version** | 0.1.0 |
| **Author** | [@l0z4n0](https://myclaude.sh/u/l0z4n0) |
| **License** | Proprietary |
| **Price** | Free |
| **Downloads** | 3 |

## Installation

### Via MyClaude CLI
```bash
myclaude install docforge-sync
```

### Via Vercel Skills
```bash
npx skills add myclaude-sh/docforge-sync
```

### Via Claude Code Plugin System
```
/plugin marketplace add myclaude-sh/registry
/plugin install docforge-sync@myclaude-sh
```

## About

---
audience: human-expert
status: stable
last-verified-against-commit: HEAD
generated-by: hybrid
---

# docforge-sync

Sub-skill of the **docforge** pack. Sensor + diagnostician + verifier for doc-code state.

> Drift is defect, not feeling.

## TL;DR

This skill quantifies documentation drift against code (DDS-1 metric), verifies docs via doctest dispatch + Vale + lychee + frontmatter schema, derives reference markdown from schemas (Pydantic / OpenAPI / Proto / GraphQL), and detects translation lag + diagram alt-text gaps.

The skill body lives in `SKILL.md`. Read that first.

## Directory layout

```
docforge-sync/
├── SKILL.md                            # primary skill body (<=500 lines, voice-DNA respected)
├── README.md                           # this file
├── references/                         # progressive disclosure — load on demand
│   ├── drift-classes.md                # D1-D5 with detection algorithms
│   ├── dds1-formula.md                 # DDS-1 components, weights, thresholds, calibration
│   ├── doctest-runners.md              # per-language dispatch table
│   ├── vale-rules.md                   # custom rules + regex
│   ├── frontmatter-schema.md           # contract reference
│   ├── traceability-matrix.md          # feature x ADR x test x doc algorithm
│   └── ci-templates.md                 # GitHub Actions + GitLab CI + pre-commit guidance
├── schema/                             # canonical JSON schemas
│   ├── frontmatter.schema.json         # imported by master skill
│   ├── docforge.config.schema.json
│   └── repo-inventory.schema.json
├── vale-styles/                        # Vale custom rule files
│   ├── docforge-A1-hedge.yml           # anti-pattern A1 detection
│   ├── docforge-A5-anonymous.yml       # anti-pattern A5 detection
│   ├── blameless.yml                   # postmortem-scoped blame language
│   └── redaction.yml                   # secret/internal-URL leak safety net
├── scripts/                            # functional stubs with full architecture
│   ├── scan.py                         # build repo-inventory.yaml
│   ├── check.py                        # compute DDS-1
│   ├── verify.py                       # orchestrated lifecycle gate
│   ├── parsers/
│   │   └── tree_sitter_universal.py    # 305+ language substrate
│   └── lib/
│       ├── exit_codes.py               # semantic exit code constants
│       ├── frontmatter.py              # parser + validator
│       └── git_helpers.py              # last-touched, churn, paired-edit
├── ci-templates/
│   └── github-actions.yml.tmpl         # ready-to-copy workflow
└── tests/                              # fixtures + smoke tests (to be expanded)
```

## Status of this build

**This is the v0.1 skill architecture forged in P4** by skill-architect. Scripts are
**functional stubs** — full method signatures, complete docstrings, architecture decisions
codified, but tree-sitter / Vale / lychee integrations are marked `# TODO`. Implementation
follows in subsequent PRs; the contracts (schemas, CLI surface, exit codes, output formats)
are stable.

What is **complete and authoritative** in this build:

- `SKILL.md` body — Anthropic-grade, voice-DNA respected, trigger keywords explicit.
- All `references/*.md` — algorithm specs, thresholds, calibration notes.
- All `schema/*.json` — canonical contracts (master skill imports `frontmatter.schema.json`).
- All `vale-styles/*.yml` — production-ready Vale rules.
- `scripts/` — function signatures, dataclasses, exit-code semantics, CLI argparsers — all in place.
- `ci-templates/github-actions.yml.tmpl` — directly usable.

## Sibling and parent skills

- **Parent (master):** `docforge` — orchestrator. Routes to this skill for drift + verify + derive operations.
- **Sibling:** `docforge-llms` — projection canonical -> per-page .md / llms.txt / AGENTS.md / CLAUDE.md / MCP scaffold.

## Provenance

Forged in `D:/lozano-system/workspace/docforge-build/P4-skills-forge/` from:
- `P3-athena-framework/prd.md` v1.0 + `prd-addendum-v1.1.md`
- `P3-athena-framework/identity-persona.md` (5-layer architecture)
- `P3-athena-framework/values-ranking.md` (E1>E5>E2>E4>E3 + tiebreaks)
- `P3-athena-framework/voice-dna.md` (7 signature phrases + 7 anti-phrases)
- `P2-research/C-drift-sot.md` (full technical architecture)
- `P2-research/D-philosophy.md` (anti-patterns A1-A5)

## Auto-validation summary

| Test | Result |
|---|---|
| (a) Trigger keywords explicit in description | PASS — `drift, doc-code sync, DDS-1, doctest, Vale, lychee, AST, tree-sitter` all present |
| (b) `SKILL.md` <= 500 lines | PASS — well under limit |
| (c) Voice DNA respected (no hedge words, signature phrases used) | PASS — SP3 ("Drift is defect, not feeling.") in TL;DR + check.py output; confidence labels in references |
| (d) Frontmatter contract spec present | PASS — `references/frontmatter-schema.md` + `schema/frontmatter.schema.json` |
| (e) >=1 concrete example per capability | PASS — every capability section in SKILL.md has a CLI invocation + output sample |
| (f) Self-reference test | PASS — SKILL.md has its own frontmatter + zero hedge soup + zero best-practice anonymous + last-verified set |

---

[![MCS-2](https://myclaude.sh/badge/mcs/2.svg)](https://myclaude.sh/quality)
[![Available on MyClaude](https://myclaude.sh/badge/available.svg)](https://myclaude.sh/p/docforge-sync)

<sub>Built with MyClaude Studio Engine</sub>


## Tags

`documentation` `drift-detection` `DDS-1` `doctest` `Vale` `lychee` `schema-derive` `tree-sitter` `frontmatter`

---

*Published on [MyClaude Marketplace](https://myclaude.sh/p/docforge-sync) — the curated marketplace for the Claude Code ecosystem.*

*This repository is automatically mirrored from MyClaude. To publish updates, use `myclaude publish`.*
