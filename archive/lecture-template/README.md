# Archived: lecture-creation template infrastructure

This directory holds the Beamer/Quarto lecture-creation assets that shipped with the
base "academic Claude Code workflow" template this repo was forked from. They were
moved here on 2026-06-24 because this repo is now dedicated to the *Doorstep
Deliberation* (AGH 2026) field experiment — a PAP/ethics/data project, not a course —
and the active `CLAUDE.md` no longer describes a lecture workflow.

## What's here

- `Slides/` — Beamer `.tex` source (`HelloWorld.tex` demo)
- `Quarto/` — RevealJS `.qmd` mirror + `theme-template.scss` (`HelloWorld.qmd` demo)
- `Preambles/` — shared LaTeX headers + the palette contract (`Preambles/README.md`)
- `Figures/` — figures/images for slides
- `master_supporting_docs/` — placeholder dirs for source papers/slides feeding lecture
  creation (superseded by `resources/` for this project)

Each was moved with `git mv`, so full history (including pre-move commits) is preserved
— `git log --follow` on any file inside still works.

## Restoring (if this repo teaches again)

1. `git mv archive/lecture-template/<dir> <dir>` for each of the five directories above,
   back to repo root.
2. Re-add the lecture-oriented sections to `CLAUDE.md` (folder structure, LaTeX/Quarto
   commands, Beamer environments / Quarto CSS class tables) — see git history on
   `CLAUDE.md` from before 2026-06-24 for the prior version.
3. The dormant lecture skills (`/create-lecture`, `/compile-latex`, `/deploy`,
   `/qa-quarto`, `/slide-excellence`, `/translate-to-quarto`, `/extract-tikz`,
   `/new-diagram`, `/syllabus`, `/teach-from-paper`, `/scaffold-exercises`,
   `/pedagogy-review`, `/devils-advocate`, `/visual-audit`) and their agents were never
   removed — they work as soon as the paths above exist again.

## What was *not* archived

`guide/` and `docs/` (the rendered workflow guide / GitHub Pages) document the skill
system itself, not lectures, and `scripts/check-surface-sync.py` depends on their paths
existing — they stay at repo root regardless of project type.
