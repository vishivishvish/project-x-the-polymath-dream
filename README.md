# Project X — The Polymath Dream

A dual, parallel-tracked long-term project:

1. **Vishnu becomes an intermediate-level polymath** across a deliberately sequenced set of scientific and engineering disciplines.
2. **A continual-learning agent** improves its own performance on an expanding set of metrics (representation stability, ML eval metrics, trading P&L/XIRR, writing quality, etc.), using the same curriculum as its source of experience.

Both halves share one curriculum, one repo, and one running log of ideas. Neither is a side project to the other.

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

**Seedling Log:** every module's X.2 write-up ends with one line each for X.3, X.4, X.5, and X.6 — "if this idea touched the agent's code / a paper / trading / the agent's learning-to-learn, what's the smallest version of that?" Most seeds go nowhere. That's fine — they're cheap, they compound, and periodic X.6 reviews scan the logs to decide which seeds are worth promoting into real work. See [curriculum/seedlings/](curriculum/seedlings/).

## The curriculum: 7 tiers, simple → complex, spiral

Built from the root field list in [curriculum/00-overview.md](curriculum/00-overview.md#field-list). Pass 1 is a shallow survey across all tiers in order; later passes re-enter the same order at increasing depth.

| Tier | Fields | Timeframe |
|---|---|---|
| 0 | Universal substrate — Touch Typing, Math Foundations, Abacus/Vedic Math, Software Eng, IT & Hardware | Months 1–4 |
| 1 | Data & compute core — Stats/Viz/DB, Data Engineering, Networking/Cybersecurity, Electronics basics | Months 4–9 |
| 2 | Intelligence core — ML Math, ML Engineering, GPU Programming, LLM/GenAI/Agentic AI, Info Theory, Graph Learning, DL & RL, Evolutionary Computation | Year 1–2 |
| 3 | Money & behavior — Financial Analysis & Econometrics, Quant Trading, Behavioral Psychology | Year 2–3 |
| 4 | Life & mind — Biology, Neuroscience, Neuro-engineering & BMI | Year 3–4 |
| 5 | Physical & materials engineering — Materials Science, Chemistry, Nanotech, Electronics (deep), Robotics, Drones/AAVs | Year 4–6 |
| 6 | Frontier physics & space — Engineering Physics & Astronomy, Special Relativity, Rocket Engineering, Satellite/Space Systems | Year 6–8 |
| 7 | Hardest peaks (capped at solid-beginner, not intermediate) — Quantum Computing, Quantum/Particle/Nuclear Physics, General Relativity | Year 8–10+ |

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
```

A unified `starter.docx` is kept in sync with everything under `curriculum/` and `tracks/X1-formal` + `tracks/X2-conceptual`, for single-document reading.
