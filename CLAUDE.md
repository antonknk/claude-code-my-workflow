# CLAUDE.MD — Doorstep Deliberation (AGH 2026)

**Project:** Doorstep Deliberation — a field experiment on deliberative vs. non-deliberative doorstep canvassing
**Institution:** London School of Economics and Political Science, Department of Government
**Branch:** main

---

## Project Context

This is a field experiment run in cooperation with a political party ahead of the 2026
Berlin Abgeordnetenhauswahl (state election). Doorstep canvassing visits are randomised
between a **deliberative** condition (canvassers discuss the issue, put forward the
party's position, and respond to counterarguments) and a **non-deliberative** condition
(canvassers use active listening but only pitch the party's position). Voters complete a
short, anonymous, condition-specific paper questionnaire collected via ballot box.

The design builds directly on a prior, already-run study — the *Doorstep Reciprocity
Experiment* (reciprocal vs. unidirectional canvassing scripts; see
`resources/anton_reciprocity_LESS.pdf` and `resources/pap_reciprocity_doorstep.qmd`) — and
sits alongside a sibling PAP for a related canvassing-efficacy study in the same district
(`resources/pap_agh26_exp.qmd`), which is a useful source for power-analysis patterns
(DeclareDesign simulation grids) and GDPR-compliant recruitment-data architecture, but is
**not** this project's own design document.

**Note on the rest of this repo:** this clone was forked from a generic academic Claude
Code workflow template that also supports lecture-slide creation. That infrastructure
(`Slides/`, `Quarto/`, `Preambles/`, `Figures/`, `master_supporting_docs/`) has been moved
to `archive/lecture-template/` because this project doesn't teach from this repo —
`README.md`'s Quick Start / HelloWorld walkthrough still describes those original
locations and is **not authoritative for this project**; this file is.

---

## Core Principles

- **Plan first** — enter plan mode before non-trivial tasks; save plans to `quality_reports/plans/`
- **Verify after** — render/check outputs and confirm at the end of every task
- **The PAP is the design's source of truth** — `pap/deliberation_pap.qmd` is the authoritative statement of design, hypotheses, and analysis plan. `party_deliverables/` (partner-facing material) and `ethics/` (the ethics application) describe the same design but should never introduce a design decision the PAP doesn't already state — update the PAP first, then propagate.
- **Quality gates** — nothing ships below 80/100
- **[LEARN] tags** — when corrected, save `[LEARN:category] wrong → right` to [MEMORY.md](MEMORY.md)

Cross-session context lives in [MEMORY.md](MEMORY.md); past plans, specs, and session logs are in [quality_reports/](quality_reports/).

---

## Folder Structure

```
deliberation_door/
├── CLAUDE.md                    # This file
├── .claude/                     # Rules, skills, agents, hooks (generic toolkit — see note below)
├── Bibliography_base.bib        # Centralized bibliography — cite from here in new PAP/ethics content
├── pap/                         # Pre-Analysis Plan (Quarto .qmd) — authoritative design + analysis plan
│   └── deliberation_pap.qmd     # Currently empty — not yet drafted
├── ethics/                      # Ethics application materials (LSE Research Ethics) — not yet started
├── party_deliverables/          # Concept notes / briefings for the partner party
│   └── AGH-2026-Experiment.qmd  # Project concept note (draft)
├── resources/                   # Reference material — prior study + sibling PAP (read-only inputs)
│   ├── anton_reciprocity_LESS.pdf       # Completed reciprocity-experiment paper
│   ├── pap_reciprocity_doorstep.qmd     # That experiment's PAP — design/estimators to adapt
│   └── pap_agh26_exp.qmd                # Sibling AGH26 canvassing-efficacy PAP — power-sim + GDPR patterns
├── data/                        # Raw + processed data — gitignored, never commit raw respondent data
├── scripts/                     # Utility scripts + R code (power simulations, analysis)
├── quality_reports/             # Plans, session logs, merge reports, decision records
├── explorations/                # Research sandbox (see rules)
├── templates/                   # Session log, quality report, preregistration templates
├── archive/lecture-template/    # Dormant Beamer/Quarto lecture-creation infra from the base template
├── guide/, docs/                # Template's own documentation (not project-specific) — leave alone
```

**Bibliography note:** the reference copies in `resources/` point at `../../phd.bib` (a
path from the other project). New content in `pap/` or `party_deliverables/` should cite
`../Bibliography_base.bib` instead.

---

## Commands

```bash
# Render the PAP / party deliverable (Quarto)
quarto render pap/deliberation_pap.qmd
quarto render party_deliverables/AGH-2026-Experiment.qmd

# Power analysis / simulation (R) — see resources/pap_agh26_exp.qmd for the
# DeclareDesign pattern this project's own power script should follow
Rscript scripts/R/power_simulation.R

# Quality score
python scripts/quality_score.py pap/deliberation_pap.qmd

# Surface-count sync (README ↔ CLAUDE.md ↔ guide ↔ landing page) — generic gate, still runs
./scripts/check-surface-sync.sh
```

---

## Quality Thresholds (advisory)

| Score | Checkpoint | Meaning |
|-------|------|---------|
| 80 | Commit | Good enough to save |
| 90 | PR | Ready for the ethics board / partner party |
| 95 | Excellence | Aspirational |

Applies to PAP, ethics, and party-deliverable documents the same way it applies to any
`.qmd`/`.R` file — enforced by `/commit` (halts + asks for override) **and** — once you
run `./scripts/install-hooks.sh` — by the real git pre-commit hook (`.githooks/pre-commit`)
on every commit. Bypass sparingly with `SKIP_QUALITY_GATE=1` or `--no-verify`.

---

## Skills Quick Reference

Most-used for this project, by workflow:

- **Design / preregistration:** `/interview-me` `/research-ideation` `/lit-review` `/preregister` `/power-analysis`
- **Data / reproducibility:** `/data-analysis` `/data-management-plan` `/disclosure-check` `/audit-reproducibility` `/replication-package` `/capture-environment` `/diagnose`
- **Writing / review:** `/review-paper` (`--peer`) `/verify-claims` `/proofread` `/humanize` `/submission-disclosures` `/respond-to-referees`
- **Meta / workflow:** `/commit` `/learn` `/new-skill` `/checkpoint` `/context-status` `/deep-audit` `/coauthor-brief` `/triage-inbox`

The teaching-oriented skills (`/create-lecture`, `/compile-latex`, `/deploy`, `/qa-quarto`,
`/slide-excellence`, `/translate-to-quarto`, `/extract-tikz`, `/new-diagram`, `/syllabus`,
`/teach-from-paper`, `/scaffold-exercises`, `/pedagogy-review`, `/devils-advocate`,
`/visual-audit`) still exist and work — see [README.md](README.md) for the full index —
but are dormant for this project since there's no lecture content to point them at.

---

## Current Deliverables

| Deliverable | File | Status | Key Content |
| --- | --- | --- | --- |
| Pre-Analysis Plan | `pap/deliberation_pap.qmd` | Not started (empty) | Design, hypotheses, power, analysis plan for the deliberative vs. non-deliberative treatment |
| Party concept note | `party_deliverables/AGH-2026-Experiment.qmd` | Draft | Core idea, theoretical background, key challenges, variables |
| Ethics application | `ethics/` | Not started | LSE Research Ethics submission |
| Reference: completed reciprocity experiment | `resources/anton_reciprocity_LESS.pdf`, `resources/pap_reciprocity_doorstep.qmd` | Complete (prior study) | Reciprocal vs. unidirectional script RCT — design + estimators to adapt |
| Reference: sibling AGH26 canvassing-efficacy study | `resources/pap_agh26_exp.qmd` | Complete (sibling PAP) | ITT/CACE DeclareDesign power-sim pattern; GDPR two-stream recruitment architecture |
