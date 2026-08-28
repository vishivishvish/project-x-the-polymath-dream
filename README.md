# Project X — The Polymath Dream

**A dual, parallel-tracked long-term Polymath project:**

1. **I become an intermediate-level polymath** across a deliberately sequenced set of scientific and engineering disciplines.
2. **A continual-learning agent** improves its own performance on an expanding set of metrics (representation stability, ML eval metrics, trading P&L/XIRR, writing quality, etc.), using the same curriculum as its source of experience.

Both halves share one curriculum, one repo, and one running log of ideas.

**Status:** 

[`Polymath_10_Year_Curriculum.xlsx`](Polymath_10_Year_Curriculum.xlsx) is locked in as the 10-year reference plan. 

**Day 1 of the curriculum:** 27th August 2026. 

Currently live without a break yet.

## The six tracks

Every curriculum module runs through some or all of these, in order, per run:

| Track | Name | What it is | Fires |
|---|---|---|---|
| **X.1** | Formal Learning | Textbook/course-rigor treatment of the module's topic — definitions, derivations, formal problem sets | Every module |
| **X.2** | Conceptual Learning | ELI5 distillation of X.1 — the *why* behind the *what*, plus extraction of core axioms/principles into the shared [Axioms Ledger](curriculum/axioms-ledger.md) | Every module |
| **X.3** | Agent Learning | The agent's actual code — its state representation, update rules, memory, evaluation | When a module teaches a transferable learning mechanism |
| **X.4** | Research Papers | Distillation of X.1–X.3 work into papers submitted to arXiv/elsewhere. Paper #1: [arXiv:2602.19655](https://arxiv.org/abs/2602.19655), "Representation Stability in a Minimal Continual Learning Agent" | Periodically, when a cluster of work earns it |
| **X.5** | Agent Trading | An experimental (not production) testbed where the agent's learning is applied to trading decisions, tracked against P&L/XIRR as one metric among several | When a module plausibly improves decision-making under uncertainty |
| **X.6** | Recursive Self-Improvement | The grand loop: does what we learned change *how* the agent learns, not just *what* it knows? Feeds back into X.3's code and into how the curriculum itself sequences | Periodic review, end of each tier |

**Seedling Log:**

Every module's X.2 write-up ends with one line each for X.3, X.4, X.5, and X.6 — "if this idea touched the agent's code / a paper / trading / the agent's learning-to-learn, what's the smallest version of that?" Most seeds go nowhere. That's fine — they're cheap, they compound, and periodic X.6 reviews scan the logs to decide which seeds are worth promoting into real work. See [curriculum/seedlings/](curriculum/seedlings/).

## The curriculum: 7 tiers, simple → complex, spiral

Built from the root field list in [curriculum/00-overview.md](curriculum/00-overview.md#field-list). Pass 1 is a shallow survey across all tiers in order; later passes re-enter the same order at increasing depth.

| Tier | Fields | Deepening happens in |
|---|---|---|
| 0 | Universal substrate — Touch Typing, Math Foundations, Abacus/Vedic Math, Software Eng, IT & Hardware | Year 1 (survey) → Years 2–3 (intermediate) |
| 1 | Data & compute core — Stats/Viz/DB, Data Engineering, Networking/Cybersecurity, Electronics basics | Year 1 (survey) → Years 2–3 (intermediate) |
| 2 | Intelligence core — ML Math, ML Engineering, GPU Programming, LLM/GenAI/Agentic AI, Info Theory, Graph Learning, DL & RL, Evolutionary Computation | Year 1 (survey) → Years 2–3 (intermediate) |
| 3 | Money & behavior — Financial Analysis & Econometrics, Quant Trading, Behavioral Psychology | Year 1 (survey) → Years 4–5 (intermediate) |
| 4 | Life & mind — Biology, Neuroscience, Neuro-engineering & BMI | Year 1 (survey) → Years 4–5 (intermediate) |
| 5 | Physical & materials engineering — Materials Science, Chemistry, Nanotech, Electronics (deep), Robotics, Drones/AAVs | Year 1 (survey) → Years 6–7 (intermediate) |
| 6 | Frontier physics & space — Engineering Physics & Astronomy, Special Relativity, Rocket Engineering, Satellite/Space Systems | Year 1 (survey) → Year 8 (intermediate) |
| 7 | Hardest peaks (capped at solid-beginner, not intermediate) — Quantum Computing, Quantum/Particle/Nuclear Physics, General Relativity | Year 1 (survey) → Years 9–10 (capped depth + grand synthesis) |

Note the shallow-first spiral: **every** tier gets its Year 1 survey pass at the same time (Pass 1), before any tier deepens. Deepening then proceeds tier-by-tier in the order above, not by calendar month — see the xlsx below for the literal module-by-module schedule this produces.

## 10-Year Module-Level Plan

[`Polymath_10_Year_Curriculum.xlsx`](Polymath_10_Year_Curriculum.xlsx) is the north-star artifact for the whole project — a 1000-row plan, exactly 100 modules per year for 10 years, one row per module. It's the literal realization of the tier table above, spiral structure included.

**Sheet 1 — "10-Year Curriculum"** (1000 rows), columns:
- `Row`, `Year`, `Month (approx)` — sequencing
- `Tier`, `Tier Name` — which of the 7 tiers (or `-` for a cross-track synthesis row)
- `Field / Discipline`, `Module Title`, `Depth Target` — what's being learned and how deep this pass goes
- `Why Here (tier rationale)`, `What Happens (X.1 + X.2)` — the formal + conceptual treatment for that module
- `X.3 Seed (Agent Code)`, `X.4 Seed (Paper Angle)`, `X.5 Seed (Trading)`, `X.6 Seed (Recursive Self-Improvement)` — one seedling per track, every row, per the [Seedling Log](#seedling-log-per-module-mandatory-kept-tight) discipline

**Sheet 2 — "Legend & Tier Map"** — the 7 tiers with their rationale and full field list, for quick reference.

**Year-by-year shape:**

| Year(s) | What happens |
|---|---|
| 1 | Pass 1 — shallow survey across all 41 fields/disciplines (2 modules each), plus 18 cross-track synthesis rows (Axioms Ledger consolidation, Seedling Log triage, cadence audits, etc.) |
| 2–3 | Deepen Tier 0–2 (Universal substrate, Data & compute core, Intelligence core) to intermediate |
| 4–5 | Deepen Tier 3–4 (Money & behavior, Life & mind) to intermediate |
| 6–7 | Deepen Tier 5 (Physical & materials engineering) to intermediate |
| 8 | Deepen Tier 6 (Frontier physics & space) to intermediate |
| 9–10 | Tier 7 (hardest peaks) to its capped depth, plus grand-synthesis rows: second-spiral deep dives back into earlier tiers at research depth, a decade-long X.4/X.5/X.6 retrospective, and a next-decade roadmap module |

Color-coded by tier, with a frozen header row and autofilter for slicing by year/tier/field. Generated as a structured first draft — real, tier-correct, dependency-ordered sequencing across all 41 fields, with the seed columns built from field-specific templates rather than individually hand-authored; treat it as the north star to react to and hand-tune, not a finished/final artifact.

## Cadence

15 minutes/day, non-negotiable floor (keeps the streak, runs the agent, does spaced review), supplemented by occasional deeper blocks when a new tier opens. See [curriculum/00-overview.md](curriculum/00-overview.md#cadence--mastery-bar) for the mastery-bar definitions (Beginner / Intermediate / Advanced) used to judge progress per field.

## Repo layout

```
curriculum/
  00-overview.md        tiers, cadence, mastery bar, loop design
  axioms-ledger.md       the living cross-domain axioms document (X.2 output)
  seedlings/              one running log per track (X.3/X.4/X.5/X.6 seeds)
tracks/
  X1-formal/              formal lessons, one file per module
  X2-conceptual/          conceptual/ELI5 lessons + axioms + seedling logs, one file per module
  X3-agent/               agent source code
  X4-papers/              paper drafts and the published-paper record
  X5-trading/             experimental trading testbed
  X6-recursive/           periodic recursive self-improvement reviews
starter.docx              unified copy of the same content, single-file-readable
Polymath_10_Year_Curriculum.xlsx   1000-row, module-level, 10-year plan (the north star)
```

A unified `starter.docx` is kept in sync with everything under `curriculum/` and `tracks/X1-formal` + `tracks/X2-conceptual`, for single-document reading.

## Progress Log

Real reps, logged as they happen — the ground truth this whole plan is measured against.

> **Convention:** every Log section in this README (this one included) is kept **reverse-chronological** — newest entry at the top, oldest at the bottom. New entries get added directly under this note, not appended to the end.

- **2026-08-29 — Row 1, Tier 0 · Touch Typing: Home row anchoring (second rep).** Home row drill: `asdf jkl;` x10, without looking down. Bigram drill: `a;lskdjf asdf jkl;` x10 — **10/10 clean, 0 errors** (up from 9/10 on 2026-08-27 — the rep-8 transposition is gone). Free-typing check: full name "vishnu subramanian" + "the quick brown fox" pangram, home-row-anchored. Second data point — error rate trending the right direction after 2 days.
- **2026-08-27 — Row 1, Tier 0 · Touch Typing: Home row anchoring (first rep).** Home row drill: `asdf jkl;` x10, without looking down. Bigram drill: `a;lskdjf asdf jkl;` x10 — 1 transposition error (`a;lskdfj` on rep 8), 9/10 clean. Free-typing check: own name + "the quick brown fox" pangram, home-row-anchored. First data point for next week's glance-down / error-rate comparison.
