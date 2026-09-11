# CS032 Plan: Self-Driving Car Sim — Rediscovering Driving Intelligence from Endless Ribbon Roads

**Status:** Draft for Vishnu approval (pre-scaffold)  
**Author:** Grok Bot & OpenClaude + Nvidia NIM LLM
**Date:** 2026-09-11 IST  
**Pitch refs:** `CASE_STUDY_PITCHES.md` §CS032, `TOP_PICKS.md` #12, `HOUSE_STACK.md`

---

## 1. Thesis + success criteria

**Thesis.** On a minimal CPU-friendly driving sim (endless ribbon / CarRacing), climb the House Stack so each layer buys a measurable improvement in lane-keeping, speed, and smoothness — rediscovering classical control ideas (PID, pure pursuit / lookahead, racing line) from data and policies, then ending in a hybrid Agentic + Neural + Graph + Evolutionary stub that *proposes* curricula and track variants (not a full production AV stack).

**“CS001-complete” for CS032 means (structural):**
1. Gated pipeline script with approve-each-step status (CS002 style)
2. Executed notebook (or equivalent report notebook) with embedded plots
3. Metrics table + honest skips documented
4. README with results snapshot + reproduce commands
5. Git commit + PR into `case-studies` under dual authorship (`commit-cursor`)
6. House Stack L1–L7 touched with **honest CPU skips** called out (esp. L4)

**Not required for v1 “complete”:** CARLA, real car hardware, DonkeyCar, multi-hour RL to SOTA, live NIM GenAI loops in every step.

---

## 2. Primary environment (recommended default)

| Choice | Role |
|--------|------|
| **Default: Gymnasium `CarRacing-v3` (Box2D)** | Primary. Pure Python, trains in minutes on CPU, continuous or discrete actions, well-documented. |
| **Alt A: Custom NumPy + Pygame “Endless Ribbon”** | If Box2D install friction or we want full control of curvature/state (16-dim: curvature ahead, offset, heading error, speed). Same pipeline steps; swap env adapter. |
| **Stretch only: DonkeyCar** | Later PR. Avoid Udacity/Unity/CARLA for v1. |

**Why CarRacing first:** lowest install risk, fastest first PR, still supports BC → RL → viz → curriculum story. Endless Ribbon can be PR2 if CarRacing’s top-down view feels too toy for the narrative.

**Headless:** use `SDL_VIDEODRIVER=dummy` / gymnasium render modes that don’t need a display; save RGB frames to `plots/` offline.

---

## 3. Repo layout (when approved → `case-studies`)

Proposed folder (mirror existing naming):

```
case-studies/
  032 - Self-Driving Car Sim/
    README.md
    self_driving_car_sim.ipynb          # narrative notebook
    self_driving_car_sim_executed.ipynb # after execute step
    plots/
    data/                               # rollouts, expert demos (gitkeep; large npy gitignored)
  _nospace/cs032_work/                  # no-spaces work tree (OpenClaude-safe)
    cs032_pipeline.py
    STEPS.md
    step_status.json
    steps.log
    env_adapter.py                      # CarRacing (+ optional Ribbon)
    baselines/                          # PID / pure-pursuit
    ...
```

Notebook lives in the real `032` dir; heavy steps run from `_nospace` like CS002.

**Git identity:** Vishnu Subramanian + exactly one `Co-authored-by` via `git commit-cursor`.

---

## 4. Metrics ladder

Track these on a fixed eval suite (N seeded tracks / episodes):

| Metric | Meaning | Better |
|--------|---------|--------|
| Lane deviation (px or m) | Distance from lane center | ↓ |
| Mean / max speed | Progress | ↑ (with safety) |
| Jerk / action smoothness | Comfort | ↓ |
| Interventions | Safety agent or human takeover count | ↓ |
| Laps / tiles / distance | Completion | ↑ |
| Crash / off-track rate | Failure | ↓ |

Report a small **ladder table**: PID → BC → RL → (optional DL) → enriched/agentic stub.

---

## 5. Gated steps (22) — approve each like CS002

| # | Name | Title | Diff | Deps | Artifacts | Honest skip |
|---|------|-------|------|------|-----------|-------------|
| 1 | `env_check` | Python, gymnasium, box2d, torch/sklearn, pygame optional | E | — | `env_check.json` | If `box2d-py` fails → flag Alt A Ribbon path |
| 2 | `sim_smoke` | Create env, 1 random episode, save 3 frames | E | 1 | `plots/smoke_*.png` | — |
| 3 | `extract_stub_notebook` | Create skeleton notebook cells / outline | E | — | `self_driving_car_sim.ipynb` stub | — |
| 4 | `pid_baseline` | Hand-tuned PID / pure-pursuit on state or simple features | E | 2 | `baselines/pid_scores.json`, rollout gif/png | — |
| 5 | `collect_expert` | Rollout PID “expert” demos (states, actions) | E | 4 | `data/expert_rollouts.npz` (gitignored ok) | Cap episodes for CPU |
| 6 | `bc_train` | Behavioral cloning MLP on expert data | M | 5 | `models/bc.pt` or `.pkl`, CV/val metrics | — |
| 7 | `bc_eval` | Eval BC vs PID on metrics ladder | E | 6 | `metrics/bc_vs_pid.json` | — |
| 8 | `rl_ppo` | Short PPO (or SAC) fine-tune / from scratch — **time-boxed** | M | 2 | `models/ppo.zip` or torch ckpt, learning curve | Skip or shorten if >N min; document |
| 9 | `rl_eval` | Eval RL vs BC vs PID | E | 8 | `metrics/ladder_v1.json` | — |
| 10 | `xai_policy` | SHAP or occlusion / saliency on BC or linear probe | M | 6 | `plots/shap_or_saliency.png` | If image policy too heavy → state-feature SHAP only |
| 11 | `feature_clusters` | Unsupervised cluster maneuvers (straight/turn/recovery) | E | 5 | `plots/maneuver_clusters.png` | L1 unsupervised |
| 12 | `dl_light` | Small CNN/MLP policy variant (CPU, few epochs) | M | 5 | `models/dl_light.pt`, metrics | — |
| 13 | `foundation_skip` | Decision Transformer / driving FM | E | — | `tab_or_fm_skip.json` | **Default: honest skip** on CPU |
| 14 | `genai_tracks_stub` | Procedural / VAE-lite / rule-based novel curvature profiles | M | 2 | `data/synth_tracks.json`, sample plots | Full diffusion optional later; stub OK |
| 15 | `genai_features` | Condition policy or eval on track embedding / type | M | 14, 6 | ablation table | Lightweight |
| 16 | `agentic_stub` | Structured curriculum agent schema + safety intervention counter | E | 9 | `agent_schema.json` | Not full autonomous loop in v1 |
| 17 | `hybrid_endgame_note` | Write hybrid Agentic+Neural+Graph+Evo *design* + tiny CMA-ES or random-search toy over 2–3 reward weights | M | 16 | `plots/reward_search.png` or note | Keep tiny |
| 18 | `executed_notebook` | nbconvert execute (or assemble report notebook from artifacts) | M | many | `*_executed.ipynb` | `--allow-errors` only if pre-approved |
| 19 | `fill_conclusion` | Inject metrics ladder + skips into conclusion | E | 18 | notebook updated | — |
| 20 | `sync_to_real` | Copy plots/notebook into `032 - …/` | E | 18–19 | real dir synced | — |
| 21 | `readme_update` | README with results + reproduce | E | 20 | `README.md` | — |
| 22 | `git_commit` | Branch, `commit-cursor`, PR | E | 21 | PR URL | Selective paths; no large npz/mp4 |

**Critical path (sketch):**  
1 → 2 → 4 → 5 → 6 → 7 → 8 → 9 → 10/11/12 → 13 → 14 → 15 → 16 → 17 → 18 → 19 → 20 → 21 → 22

---

## 6. House Stack mapping (explicit)

| Layer | CS032 v1 move |
|-------|----------------|
| L1 Sup+Unsup | BC from PID expert; maneuver clustering |
| L2 XAI | SHAP/saliency / interpretable gains |
| L3 DL | Small MLP/CNN policy |
| L4 FM | Honest skip (DT/DriveGPT ONNX later) |
| L5 GenAI | Synthetic tracks / curvature profiles (stub→real) |
| L6 GenAI features | Track-type conditioning ablation |
| L7 Agentic | Curriculum + safety schema; structured vs autonomous note |
| Hybrid | Tiny evo/search over rewards + neural policy + roadmap for graph waypoints |

**Rediscovery thread (narrative):** PID gains / lookahead → BC imitates → RL improves residual → XAI shows what it “looks at” → GenAI invents harder roads → agent proposes curriculum.

---

## 7. Risks & mitigations

| Risk | Mitigation |
|------|------------|
| `box2d` / SWIG install pain | Fall back to Endless Ribbon (Alt A) at step 1 |
| Headless display errors | `SDL_VIDEODRIVER=dummy`; save frames, don’t live-render |
| RL burns hours | Hard time-box + fewer timesteps; BC may be “hero” of v1 |
| Huge rollouts in git | gitignore `*.npz`, `*.mp4`, `data/**`; commit metrics + small plots only |
| Spaces in path vs OpenClaude | `_nospace/cs032_work` |
| NIM rate limits in GenAI steps | Stub generators first; live NIM optional |
| Overclaiming “self-driving” | README: *sim rediscovery case study*, not AV product |

---

## 8. Calendar / PR slices

| Slice | Contents |
|-------|----------|
| **PR1 (first ship)** | Steps 1–7 + 21 partial: env, PID, BC, metrics, README stub, scaffolding |
| **PR2** | RL + eval ladder + XAI + clusters + dl_light |
| **PR3** | GenAI tracks stub, features ablation, agentic/hybrid stubs, executed notebook, full README, final polish |

Or one long gated run like CS002 if you prefer single PR at the end — recommend **PR1 early** so the folder exists on `main`.

---

## 9. Non-goals for v1

- CARLA / nuScenes / Waymo / real vehicles  
- Multi-agent traffic, pedestrians, full HD maps  
- Beating published CarRacing SOTA  
- Production safety case / ISO  
- Mandatory paid GPU  
- Full autonomous meta-agent writing code unsupervised  

---

## 10. Open questions for Vishnu (max 5)

1. **Env default:** lock **CarRacing-v3** for PR1, or start with **custom Endless Ribbon** for a stronger “ribbon road” story?  
2. **Shipping style:** early **PR1** after BC, or one CS002-style mega-run then a single PR?  
3. **RL appetite:** time-box (e.g. ≤15–20 min CPU) even if weak, or allow BC-first narrative with RL as optional step-skip?  
4. **Case number folder:** `032 - Self-Driving Car Sim` OK (pitch id CS032), or wait until case-studies numbering catches up past 012?  
5. **GenAI:** procedural stub only in v1, or must call NIM for text-to-track in the first complete pass?

---

## Approval gate

Reply with answers to §10 (or “defaults OK”) to approve scaffolding. Next action after approval: Nova scaffolds `_nospace/cs032_work` + `032 - …` stub and implements step 1 for your go.

