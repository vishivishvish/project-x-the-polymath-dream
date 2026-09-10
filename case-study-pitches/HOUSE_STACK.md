# Nova House Stack — Required Progression for Every Case Study

**Spirit:** Each case study (CS001–CS012, and all future CSxxx) must demonstrate this full stack. The layers build on each other; skipping a layer is only acceptable with an explicit "CPU skip" justification.

---

## Layer 1: Supervised ML + Unsupervised ML
**Purpose:** Establish baseline predictive power AND discover structure without labels.
- **Supervised:** Regression/classification with proper CV, metrics, calibration plots.
- **Unsupervised:** Clustering, dimensionality reduction, anomaly detection, graph communities.
- **Deliverable:** Side-by-side comparison — what supervision buys vs. what emerges for free.

---

## Layer 2: Explainable AI (SHAP / Intrinsic Interpretability)
**Purpose:** Make the model's reasoning transparent and auditable.
- **SHAP:** Global (beeswarm, dependence) + local (waterfall, force) explanations.
- **Intrinsic:** Linear/trees/rule-based models where coefficients/rules are directly interpretable.
- **Deliverable:** "Why this prediction?" answered for domain experts, not just ML engineers.

---

## Layer 3: Deep Learning (Light / CPU-Feasible Where Possible)
**Purpose:** Show representation learning on raw/structured data without massive compute.
- **Architectures:** Small MLPs, 1D/2D CNNs, LSTMs/GRUs, TabTransformer, simple Graph NNs.
- **Constraints:** Trainable on CPU in ≤30 min; ≤1M params; use mixed precision if GPU available.
- **Honest skip:** If domain fundamentally needs GPU (e.g., large vision, LLMs), state it explicitly and provide a CPU-friendly proxy (distilled model, ONNX, smaller architecture).

---

## Layer 4: Foundation Models (or Honest CPU Skip)
**Purpose:** Leverage pre-trained knowledge; show transfer/adaptation.
- **Options:** BERT-family (text), CLIP (vision+text), ESM (protein), TabPFN (tabular), MolBERT (chem), AstroBERT (astronomy), etc.
- **Modes:** Frozen embeddings + probe head; LoRA/adapter fine-tuning; full fine-tune (GPU only).
- **Honest CPU skip:** If no CPU-feasible foundation model exists for the domain, say so and use Layer 3 instead. Do not pretend.

---

## Layer 5: Generative AI
**Purpose:** Generate new data, augment, or model the data distribution.
- **Types:** VAE, Diffusion (small), GAN (tabular/image), Normalizing Flow, Autoregressive (small LLM), GFlowNet.
- **Use cases:** Data augmentation for Layer 1; counterfactual generation; synthetic minority oversampling; domain-specific generation (molecules, light curves, music).
- **Deliverable:** Quality/diversity metrics + domain expert validation (not just FID).

---

## Layer 6: GenAI for Feature Engineering
**Purpose:** Use generative models to *create* features for downstream tasks.
- **Patterns:**
  - Latent space embeddings → feed into supervised/unsupervised models (Layer 1)
  - Generated counterfactuals → causal feature importance
  - Synthetic data → augment small labeled sets
  - Foundation model embeddings (Layer 4) → rich feature vectors
- **Deliverable:** Ablation — downstream performance with vs. without GenAI features.

---

## Layer 7: Structured Agentic AI vs Autonomous Agentic AI
**Purpose:** Demonstrate decision-making loops, not just predictions.
- **Structured Agentic AI (Deterministic/Guided):**
  - Fixed pipeline: Plan → Tool → Observe → Act (e.g., AutoML, active learning loop, RAG with fixed steps)
  - Human-in-the-loop checkpoints; auditable trace.
- **Autonomous Agentic AI (Open-Ended):**
  - LLM-driven planning with dynamic tool selection; self-reflection; multi-step reasoning.
  - Higher capability, higher risk; requires guardrails (budget, time, safety).
- **Deliverable:** A working agent that solves a domain sub-task (e.g., "find the best alloy composition," "design an experiment," "choose the next simulation").

---

## Integration Rule: The "Rediscovery" Thread
Every layer must serve the **rediscovery narrative** — the case study's core promise:
> *Can the stack rediscover a known domain principle from raw data?*

- Layer 1: Rediscover clusters/classes
- Layer 2: Explain *why* the rediscovery works
- Layer 3: Learn representations that make rediscovery possible
- Layer 4: Transfer pre-trained knowledge to accelerate rediscovery
- Layer 5: Generate examples that illustrate the rediscovered principle
- Layer 6: Engineer features that make the principle explicit
- Layer 7: Build an agent that *uses* the principle to act/decide

---

## Domain-Specific Notes (Simulation / Robotics / Driving)
- **CS031 Robotics Sim / CS032 Driving Sim:** These use simulated environments (Gymnasium, PyBullet, custom NumPy/Pygame) as the "lab." The House Stack applies identically — L1 learns from sim data, L3/L5/L6 train policies in sim, L7 designs sim curricula. The **hybrid endgame** (Agentic + Neural + Graph + Evolutionary) is the *differentiator*: it shows an agent that not only solves the task but *invents the next layer of intelligence* (architectures, rewards, curricula, environments). This is the flagship demonstration of X.3 Agent Learning on Tier 5 Robotics.
- **Sim-to-real gap:** L7 Autonomous agent explicitly proposes sim modifications (noise, delay, friction) to close the gap — this is "agentic system identification."

---

## CPU Feasibility Tiers
| Tier | Layers | Typical Time (CPU) | Example Domains |
|------|--------|-------------------|-----------------|
| **Trivial** | 1, 2, 6, 7 (structured) | < 5 min | Tabular, small graphs, symbolic |
| **Easy** | 1–3, 5 (small), 6, 7 | 5–30 min | Time series, small NLP, small images |
| **Medium** | 3–5 (moderate), 7 (autonomous) | 30–60 min | Medium graphs, audio, protein sequences |
| **GPU-Needed** | 3–5 (large), 4 (full fine-tune) | > 60 min / needs GPU | Large vision, LLMs, big GNNs, diffusion |

**Guideline:** Target Trivial/Easy for Nova's main track. Medium = sprint 2. GPU-Needed = park for GPU box.

---

## Checklist for Every Pitch
When adding a new pitch, verify:
- [ ] Layer 1: Supervised + Unsupervised plan specified
- [ ] Layer 2: SHAP/intrinsic interpretability plan
- [ ] Layer 3: DL architecture + CPU time estimate
- [ ] Layer 4: Foundation model candidate OR explicit CPU skip note
- [ ] Layer 5: GenAI type + generation target
- [ ] Layer 6: How GenAI features feed downstream
- [ ] Layer 7: Structured vs. Autonomous agent scenario
- [ ] Rediscovery thread: What known principle does each layer help rediscover?
- [ ] CPU feasibility tier assigned
- [ ] Honest gaps called out (no hand-waving)