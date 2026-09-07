# Case Study Pitches for Nova — Lyra's Polymath-Driven Ideas

**Style target:** Applied ML notebooks with domain story + methods + plots + "rediscovery" flavor (like CS001–CS012).
**Constraint:** No neuroscience/EEG (CS002), no robotics grasp/swarm (CS003/005), no finance panels (CS008), no rockets (CS009), no intrusion detection (CS010), no data quality drift (CS011), no speech recognition (CS012), no targeted alpha therapy (CS001), no QKD (CS007).

Each pitch: **Title | Linked discipline(s) | 3–5 sentence hook | Why it fits house style | CPU feasibility | Novelty note | House stack fit**

---

## 1. **CS013: Harmonic Syntax — Rediscovering Music Theory via Unsupervised Graph Learning**
**Disciplines:** Music (implied by Biological Science & Engineering, Information Theory, Graph Learning) × ML
**Hook:** Treat a corpus of symbolic music (MusicXML/MIDI) as a graph of note transitions and harmonic contexts. Apply spectral clustering and graph autoencoders to *rediscover* the circle of fifths, functional harmony categories (tonic/subdominant/dominant), and voice-leading rules — without ever teaching the model a single music theory concept. The "aha" plot: a 2D embedding where major/minor keys separate cleanly and the circle of fifths emerges as a topological loop.
**House fit:** Pure rediscovery flavor (like CS006's memory decay curves), domain story (music as humanity's oldest structured information), beautiful visualizations (embeddings, adjacency heatmaps), minimal supervision.
**CPU feasibility:** **Easy** — symbolic music is tiny; graph construction and spectral methods run in seconds on CPU.
**Novelty:** Most music ML focuses on generation; this frames theory *discovery* as unsupervised representation learning. Connects Information Theory (entropy of harmonic surprise) to Graph Learning (community detection = key areas).
**House stack fit:**
- **L1 Supervised+Unsupervised:** Unsupervised — spectral clustering on note-transition graphs, graph autoencoders; Supervised — predict composer/era from graph embeddings (probe task).
- **L2 XAI:** SHAP on graph neural net predicting key signature; intrinsic interpretability via spectral embedding coordinates (Fiedler vector = circle of fifths position).
- **L3 Deep Learning:** Graph Autoencoder (2-layer GCN, ~10k params) — CPU trains in <1 min. Optional: small LSTM on note sequences as baseline.
- **L4 Foundation Models:** **CPU skip honest** — no music-specific foundation model runs on CPU. Use MusicBERT embeddings (frozen, via ONNX) if available, else skip to L3.
- **L5 GenAI:** VAE on graph latent space → generate novel chord progressions that respect voice-leading; conditional VAE keyed by "major/minor" label.
- **L6 GenAI Features:** VAE latent codes → feed into supervised composer classifier; compare accuracy vs. raw spectral embeddings (ablation).
- **L7 Agentic:** **Structured** — Active learning loop: agent queries "most harmonically ambiguous measure" for human labeling; **Autonomous** — LLM agent composes a 16-bar piece satisfying "modulate from C major to E minor using pivot chord."
- **Rediscovery thread:** L1 rediscovers circle of fifths topology; L2 explains *which intervals drive key separation*; L3 learns harmonic syntax representations; L5 generates theory-compliant progressions; L6 shows latent space encodes functional harmony; L7 uses rediscovered rules to compose.

---

## 2. **CS014: Phylogenetic Echoes — Reconstructing Language Families from Cognate Networks**
**Disciplines:** Linguistics (Biological Science & Engineering, Evolutionary Computation, Graph Learning) × ML
**Hook:** Build a weighted graph of cognate sets across 200+ languages (using ASJP or Lexibank data). Apply minimum spanning tree + hierarchical clustering to *rediscover* the Indo-European, Afro-Asiatic, Austronesian family trees — and detect known controversies (e.g., Altaic, Dene-Yeniseian) as ambiguous edges. Bonus: simulate lexical borrowing as edge rewiring and watch how "areal features" distort the tree.
**House fit:** Rediscovery of known science (comparative linguistics) from raw data; evolutionary computation angle (simulated borrowing = horizontal gene transfer); dendrograms + geographic maps as plots.
**CPU feasibility:** **Easy** — distance matrices of 200 languages are trivial; MST and clustering are O(n²) with n≈200.
**Novelty:** Frames historical linguistics as graph community detection with adversarial noise (borrowing). Bridges Evolutionary Computation (phylogenetics) and Graph Learning — both in Vishnu's Tier 2.
**House stack fit:**
- **L1 Supervised+Unsupervised:** Unsupervised — MST, hierarchical clustering, spectral clustering on cognate graph; Supervised — predict language family from graph embeddings (held-out families).
- **L2 XAI:** SHAP on family classifier; intrinsic — dendrogram cut heights = divergence times; edge weights = borrowing probability.
- **L3 Deep Learning:** GraphSAGE (2-layer, ~20k params) for inductive family prediction — CPU <2 min. Or skip: classical MST already *is* the model.
- **L4 Foundation Models:** **CPU skip honest** — no linguistic phylogeny foundation model. Use multilingual BERT (frozen) for cognate detection preprocessing only.
- **L5 GenAI:** VAE on language embeddings → generate "proto-language" feature vectors; conditional on geographic region.
- **L6 GenAI Features:** VAE latents + geographic coords → feed into borrowing detector (binary classifier: vertical vs. horizontal transmission).
- **L7 Agentic:** **Structured** — Active learning: agent selects language pairs with max borrowing uncertainty for expert annotation; **Autonomous** — Agent proposes "most likely cognate set for proto-form X" with evidence chain.
- **Rediscovery thread:** L1 rediscovers family trees as graph communities; L2 quantifies borrowing vs. inheritance; L3 generalizes to unseen languages; L5 generates proto-forms; L6 detects horizontal transfer; L7 automates comparative method.

---

## 3. **CS015: Material Memory — Predicting Alloy Phase Diagrams from Sparse Experimental Data**
**Disciplines:** Materials Science & Engineering × Chemistry & Chemical Engineering × ML (Data Science, Sparse Regression)
**Hook:** Given a sparse ternary alloy dataset (composition → phase labels from CALPHAD or experimental papers), use Gaussian Process regression with physics-informed kernels (Gibbs free energy constraints) to *reconstruct* the full phase diagram. The rediscovery: the model "learns" lever rule, tie-lines, and eutectic points from ~50 data points. Plot: ternary heatmaps with uncertainty contours.
**House fit:** Materials informatics is a perfect "small data, big physics" domain — like CS001 (targeted alpha) but for alloys. Sparse data + strong priors = core Nova aesthetic.
**CPU feasibility:** **Medium** — GPs scale O(n³) but n<500; sparse approximations keep it CPU-friendly.
**Novelty:** Most materials ML uses massive DFT datasets; this uses *human-curated sparse experimental data* — the real bottleneck in alloy design. Ties to Vishnu's Tier 5 (Materials, Chemistry).
**House stack fit:**
- **L1 Supervised+Unsupervised:** Supervised — GP regression (composition → phase fraction); Unsupervised — clustering in composition space to find phase regions.
- **L2 XAI:** SHAP on GP (via kernel SHAP); intrinsic — kernel lengthscales = interaction strength between elements; uncertainty contours = phase boundaries.
- **L3 Deep Learning:** Small MLP (3-layer, ~5k params) as GP surrogate for fast prediction; PINN with Gibbs free energy loss.
- **L4 Foundation Models:** **CPU skip honest** — no alloy foundation model on CPU. Use MatBERT (frozen, ONNX) for composition embeddings if available.
- **L5 GenAI:** Conditional VAE (composition | phase) → generate novel compositions in target phase region; Diffusion on ternary grid (small, 100 steps).
- **L6 GenAI Features:** VAE latent space → feed into GP as additional kernel dimensions; ablation: GP with vs. without latent features.
- **L7 Agentic:** **Structured** — Active learning loop: agent queries next (composition, temperature) to maximally reduce phase boundary uncertainty; **Autonomous** — Agent designs "find me a composition with single-phase FCC at 800°C" with uncertainty budget.
- **Rediscovery thread:** L1 rediscovers phase boundaries from sparse points; L2 reveals element interactions via lengthscales; L3 learns free energy landscape; L5 generates alloys in unexplored regions; L6 uses generative latent as physics-informed features; L7 closes the experimental design loop.

---

## 4. **CS016: Paleoclimate Proxy Fusion — Reconstructing Holocene Temperature from Noisy Multi-Proxy Records**
**Disciplines:** Climate/Ecology (Engineering Physics & Astronomy, Satellite & Space Systems) × ML (Time Series, State Space Models)
**Hook:** Fuse ice cores (δ¹⁸O), tree rings, speleothems, and marine sediments — each with different temporal resolution, dating uncertainty, and climate sensitivity — into a single latent temperature reconstruction using a hierarchical state-space model. The rediscovery: the Medieval Warm Period, Little Ice Age, and 8.2 kyr event emerge *without* being prescribed. Plot: spaghetti of proxy records → clean posterior with credible intervals.
**House fit:** Multi-source noisy data fusion (like CS004 AV fleet, CS011 data drift); domain story (Earth's memory); beautiful uncertainty visualization; physics-informed priors (Milankovitch cycles).
**CPU feasibility:** **Medium** — MCMC on ~10k time points is heavy but doable with variational inference or Kalman smoothing on CPU.
**Novelty:** Treats dating uncertainty as a first-class latent variable (not pre-aligned). Connects Satellite/Space (remote sensing proxies) to Tier 2 time-series ML.
**House stack fit:**
- **L1 Supervised+Unsupervised:** Unsupervised — latent state discovery via Kalman smoother / VAE; Supervised — predict held-out proxy values from latent temperature.
- **L2 XAI:** SHAP on proxy → temperature mapping; intrinsic — state-space coefficients = proxy sensitivity & lag; posterior credible intervals = uncertainty quantification.
- **L3 Deep Learning:** Deep State Space Model (DSSM) — small RNN (GRU, ~15k params) for latent dynamics; or Temporal CNN.
- **L4 Foundation Models:** **CPU skip honest** — no paleoclimate foundation model. Use ClimateBERT (frozen) for proxy metadata embeddings only.
- **L5 GenAI:** Conditional VAE on latent temperature → generate counterfactual Holocene trajectories (e.g., "what if 8.2 kyr event didn't happen?").
- **L6 GenAI Features:** VAE latent trajectories → feed into event detector (classify: MWP, LIA, 8.2kyr); compare vs. raw proxy features.
- **L7 Agentic:** **Structured** — Agent selects next proxy site to core for maximal information gain (active learning); **Autonomous** — Agent answers "was the MWP global?" by querying model + synthesizing evidence across proxies.
- **Rediscovery thread:** L1 fuses proxies into unified temperature; L2 attributes contribution per proxy; L3 learns non-linear proxy responses; L5 generates counterfactual climates; L6 detects climate events from latent space; L7 automates paleoclimate hypothesis testing.

---

## 5. **CS017: Legalese Embedding Geometry — Rediscovering Contract Clause Taxonomies from SEC Filings**
**Disciplines:** Law/NLP (Software Engineering, LLM/Generative AI) × ML (NLP, Clustering)
**Hook:** Embed 50k+ "Risk Factors" sections from 10-K filings using a small BERT (or TF-IDF + SVD for pure CPU). Cluster to *rediscover* the latent taxonomy of corporate risk: supply chain, regulatory, cyber, macroeconomic, litigation — and track how cluster centroids drift post-2020 (COVID), post-2022 (inflation), post-2023 (AI). Plot: UMAP of risk space with temporal trajectories.
**House fit:** Domain story (corporate anxiety as literature); rediscovery of known risk categories from raw text; temporal drift visualization (like CS011 but semantic); zero-shot taxonomy induction.
**CPU feasibility:** **Easy** — TF-IDF + TruncatedSVD runs in seconds; small BERT via ONNX/CPU is fine.
**Novelty:** Most legal NLP does classification; this does *unsupervised taxonomy discovery + temporal dynamics*. Ties LLM track to Behavioral Psychology (corporate risk perception).
**House stack fit:**
- **L1 Supervised+Unsupervised:** Unsupervised — clustering (HDBSCAN) on embeddings; Supervised — predict sector/year from risk embedding (probe).
- **L2 XAI:** SHAP on sector classifier; intrinsic — cluster centroids = risk archetypes; UMAP axes = semantic dimensions (financial vs. operational).
- **L3 Deep Learning:** Fine-tune DistilBERT (66M params) on CPU via LoRA (r=8) — ~15 min; or freeze + MLP head.
- **L4 Foundation Models:** **DistilBERT / LegalBERT (frozen, ONNX CPU)** — 2-3x speedup vs. PyTorch; embeddings as features for L1/L6.
- **L5 GenAI:** Small GPT-2 (124M) fine-tuned on risk factors (LoRA) → generate synthetic risk sections for data augmentation; conditional on sector/year.
- **L6 GenAI Features:** GPT-2 latent states → feed into drift detector (year classifier); ablation: frozen BERT vs. GPT-2 latents vs. TF-IDF.
- **L7 Agentic:** **Structured** — RAG agent: "find all filings mentioning 'AI risk' before 2023"; **Autonomous** — Agent writes "2025 Risk Factors section for a semiconductor company" using retrieved templates + GenAI.
- **Rediscovery thread:** L1 rediscovers risk taxonomy; L2 explains semantic axes; L3 adapts legal language understanding; L4 transfers legal knowledge; L5 generates plausible risks; L6 quantifies semantic drift; L7 automates legal research/drafting.

---

## 6. **CS018: Exoplanet Light Curve Archetypes — Unsupervised Discovery of Transit Morphologies**
**Disciplines:** Astronomy (Engineering Physics & Astronomy, Satellite & Space Systems) × ML (Time Series Clustering, Shapelets)
**Hook:** Take 100k+ Kepler/TESS light curves. Normalize, align, and cluster using Dynamic Time Warping + k-medoids to *rediscover* the taxonomy: hot Jupiters (V-shape), grazing transits, disintegrating planets (asymmetric tails), binary star eclipses (double dips), stellar variability (sinusoidal). The "rediscovery" plot: medoid light curves labeled by human astronomers vs. cluster assignments.
**House fit:** Pure unsupervised morphology discovery (like CS005 drone swarm but for astrophysics); domain story (hunting worlds); beautiful folded light curve plots; zero labels needed.
**CPU feasibility:** **Medium** — DTW is O(n²) but 100k × 100k is too much; use random subset (5k) + DTW barycenter averaging (DBA) or shapelet transform.
**Novelty:** Most exoplanet ML is supervised (transit vs. false positive); this discovers *morphological classes* including rare/weird ones. Connects Space Systems to Tier 2 time-series ML.
**House stack fit:**
- **L1 Supervised+Unsupervised:** Unsupervised — DTW + k-medoids / shapelet clustering; Supervised — predict known labels (planet vs. EB vs. variable) from cluster assignment.
- **L2 XAI:** SHAP on morphology classifier; intrinsic — medoid curves = archetypes; shapelets = discriminative subsequences.
- **L3 Deep Learning:** 1D CNN (3-layer, ~20k params) on folded light curves — CPU <5 min; or LSTM for raw sequences.
- **L4 Foundation Models:** **CPU skip honest** — no light curve foundation model on CPU. Use AstroBERT (frozen, ONNX) if available for metadata.
- **L5 GenAI:** Conditional VAE (light curve | morphology class) → generate synthetic transits for rare classes (disintegrating planets); diffusion on folded curves.
- **L6 GenAI Features:** VAE latent → feed into supervised classifier (planet vs. false positive); ablation: raw pixels vs. shapelets vs. VAE latents.
- **L7 Agentic:** **Structured** — Active learning: agent selects most ambiguous light curves for human vetting; **Autonomous** — Agent designs "observe this target at phase X to distinguish planet vs. binary" (follow-up planning).
- **Rediscovery thread:** L1 rediscovers transit morphologies; L2 identifies discriminative features (ingress/egress shape); L3 learns generalizable morphology encoder; L5 generates training data for rare classes; L6 shows generative latents capture morphology; L7 plans follow-up observations.

---

## 7. **CS019: Epidemiological Wavelet — Rediscovering Disease Seasonality from Noisy Case Counts**
**Disciplines:** Epidemiology (Biological Science & Engineering) × ML (Signal Processing, State Space, Information Theory)
**Hook:** Weekly case counts for 50+ diseases (Dengue, Flu, Measles, Cholera) across 20 countries. Apply wavelet denoising + harmonic regression to *rediscover* annual/biannual cycles, climate-driven phase shifts (El Niño), and the "epidemic clock" — the phase relationship between latitude and peak timing. Plot: polar phase maps + wavelet scalograms.
**House fit:** Signal processing on biological data (like CS002 EEG but for populations); rediscovery of known epidemiology (seasonality); Information Theory angle (predictability horizon = mutual information between climate drivers and cases).
**CPU feasibility:** **Easy** — wavelet transforms and harmonic regression are O(n log n) and tiny data.
**Novelty:** Frames seasonality as *phase synchronization* across latitudes — a Kuramoto oscillator view of epidemics. Bridges Tier 4 (Bio) and Tier 2 (Info Theory, Signal Processing).
**House stack fit:**
- **L1 Supervised+Unsupervised:** Unsupervised — wavelet clustering of diseases by seasonality pattern; Supervised — predict peak timing from climate covariates (ENSO, temperature).
- **L2 XAI:** SHAP on peak timing predictor; intrinsic — wavelet coefficients = dominant periodicities; phase angles = peak timing; mutual info = predictability.
- **L3 Deep Learning:** Small TCN (Temporal ConvNet, ~10k params) for multi-disease forecasting; or N-BEATS style.
- **L4 Foundation Models:** **CPU skip honest** — no epidemiology foundation model. Use general time-series foundation (e.g., TimeGPT-1 small, ONNX) if available.
- **L5 GenAI:** Normalizing Flow on wavelet coefficients → generate synthetic epidemic curves with realistic noise/seasonality.
- **L6 GenAI Features:** Flow latent codes → feed into early-warning classifier (outbreak vs. baseline); ablation.
- **L7 Agentic:** **Structured** — Agent triggers "alert" when wavelet anomaly score exceeds threshold; **Autonomous** — Agent recommends "vaccinate region X in month Y" based on phase forecast + climate outlook.
- **Rediscovery thread:** L1 rediscovers seasonal cycles; L2 quantifies climate-disease coupling; L3 forecasts multi-disease dynamics; L5 generates realistic counterfactuals; L6 enables early warning; L7 converts forecasts to actions.

---

## 8. **CS020: Quantum Error Syndrome Decoding — Learning the Surface Code's Logical Operators from Syndrome Graphs**
**Disciplines:** Quantum Computing × Graph Learning × ML (Graph Neural Networks)
**Hook:** Simulate a distance-5 surface code under circuit-level noise. Feed syndrome graphs (stabilizer measurements → detection events) to a graph neural network that *learns* the logical operator (X/Z) without being taught the code structure. Rediscovery: the GNN learns minimum-weight perfect matching (MWPM) implicitly — and fails exactly where MWPM fails (correlated errors). Plot: decoding accuracy vs. physical error rate; attention heatmaps on syndrome graph.
**House fit:** Rediscovery of a known algorithm (MWPM) via learned representation; domain story (quantum fault tolerance); beautiful graph visualizations; zero domain knowledge in the model.
**CPU feasibility:** **Hard** — GNN training on CPU is slow; but distance-3 code with small graphs is doable. Recommend distance-3 for CPU, distance-5 for GPU.
**Novelty:** Most quantum decoding papers use MWPM or tensor networks; this frames decoding as *graph representation learning*. Directly hits Vishnu's Tier 7 (Quantum Computing) and Tier 2 (Graph Learning).
**House stack fit:**
- **L1 Supervised+Unsupervised:** Supervised — GNN predicts logical error (X/Z/I) from syndrome graph; Unsupervised — cluster syndrome graphs by error mechanism (bit-flip vs. phase-flip vs. correlated).
- **L2 XAI:** GNNExplainer / attention visualization — show which syndrome edges drive logical error prediction; intrinsic — message passing steps = MWPM iterations.
- **L3 Deep Learning:** GNN (3-layer GraphSAGE/GAT, ~50k params) — CPU feasible for distance-3 (~100 nodes); distance-5 needs GPU.
- **L4 Foundation Models:** **CPU skip honest** — no quantum decoding foundation model. Skip.
- **L5 GenAI:** Graph VAE on syndrome graphs → generate syndrome patterns for rare correlated errors (data augmentation).
- **L6 GenAI Features:** VAE latent → feed into decoder as additional node features; ablation: GNN with vs. without generative features.
- **L7 Agentic:** **Structured** — Agent chooses "next syndrome measurement round" in adaptive decoding; **Autonomous** — Agent designs "optimal syndrome extraction circuit" for given noise profile (circuit synthesis).
- **Rediscovery thread:** L1 learns decoding from data; L2 shows GNN recovers MWPM logic; L3 scales to larger codes; L5 generates hard syndromes; L6 improves decoder robustness; L7 optimizes quantum circuits.

---

## 9. **CS021: Sports Biomechanics — Rediscovering the "Kinetic Chain" from Markerless Pose Estimation**
**Disciplines:** Sports Biomechanics (Robotics & Ground-based Autonomous Systems, Biological Science & Engineering) × ML (Pose Estimation, Dynamics)
**Hook:** Use OpenPose/MediaPipe on 1000+ YouTube videos of baseball pitches, tennis serves, golf swings. Compute joint angles, angular velocities, and estimate segment energies. *Rediscover* the proximal-to-distal sequencing (kinetic chain): pelvis → torso → shoulder → elbow → wrist. Plot: phase plots of joint angles; energy transfer bar charts; "ideal" vs. "amateur" trajectories.
**House fit:** Human motion as optimal control (like CS003 robot grasp but biological); rediscovery of known biomechanics; beautiful phase portraits; zero supervised labels (self-supervised from video).
**CPU feasibility:** **Medium** — pose estimation on 1000 videos is heavy on CPU; use a subset (100) + MediaPipe (fast). Dynamics calculations are trivial.
**Novelty:** Most sports ML classifies actions; this *derives biomechanical principles* from raw video. Connects Robotics (Tier 5) to Bio (Tier 4) via self-supervised pose.
**House stack fit:**
- **L1 Supervised+Unsupervised:** Unsupervised — cluster swing/pitch trajectories by kinetic chain quality; Supervised — predict ball velocity from joint kinematics.
- **L2 XAI:** SHAP on velocity predictor; intrinsic — phase plot topology = coordination pattern; energy flow = causal chain.
- **L3 Deep Learning:** Temporal CNN / LSTM on joint angle sequences (~30k params) — CPU <10 min for 100 videos.
- **L4 Foundation Models:** **CPU skip honest** — no biomechanics foundation model. Use VideoMAE (frozen, ONNX) for pose embeddings if available.
- **L5 GenAI:** Conditional VAE on joint trajectories (condition: sport, skill level) → generate "ideal" vs. "flawed" swings for coaching.
- **L6 GenAI Features:** VAE latent → feed into skill classifier / velocity predictor; ablation.
- **L7 Agentic:** **Structured** — Agent selects "next drill" based on kinetic chain deficit; **Autonomous** — Agent analyzes new video: "your hip rotation leads shoulder by 30ms — delay hip trigger" (coaching feedback).
- **Rediscovery thread:** L1 rediscovers kinetic chain from raw video; L2 explains energy transfer mechanics; L3 models temporal coordination; L5 generates coaching exemplars; L6 quantifies technique quality; L7 delivers personalized coaching.

---

## 10. **CS022: Archaeological Seriation — Reconstructing Pottery Chronologies from Style Co-occurrence**
**Disciplines:** Archaeology (implied by Biological Science, Evolutionary Computation) × ML (Seriation, Ordinal Embedding)
**Hook:** Binary matrix: sites × pottery styles (presence/absence). Apply spectral seriation (Fiedler vector of similarity matrix) to *reconstruct* the temporal ordering of sites — the classic archaeological problem solved by Petrie (1899) and Kendall (1971). Rediscovery: the 1D embedding matches known stratigraphy. Add noise (looting, mixing) and watch the embedding degrade gracefully. Plot: Fiedler vector vs. true dates; Robinson matrix heatmaps.
**House fit:** Pure rediscovery of a 100-year-old method (seriation) via modern spectral graph theory; domain story (time from trash); elegant 1D visualizations; connects to Information Theory (optimal ordering = minimum description length).
**CPU feasibility:** **Easy** — eigendecomposition of 100×100 matrix is instant.
**Novelty:** Frames seriation as *spectral ordering with uncertainty quantification* — Bayesian seriation via MCMC on the latent order. Bridges Evolutionary Computation (cultural evolution) and Graph Learning.
**House stack fit:**
- **L1 Supervised+Unsupervised:** Unsupervised — spectral seriation (Fiedler vector), Bayesian seriation (MCMC); Supervised — predict known dates from seriation position (probe).
- **L2 XAI:** Intrinsic — Fiedler vector = temporal coordinate; eigenvector components = style diagnostics; posterior uncertainty = mixing/looting.
- **L3 Deep Learning:** **Skip honest** — classical spectral method *is* the optimal model; no DL needed. Optional: VAE on style matrix for denoising.
- **L4 Foundation Models:** **CPU skip honest** — no archaeology foundation model. Skip.
- **L5 GenAI:** VAE on style matrix → generate "missing" styles for looted sites; conditional on seriation position.
- **L6 GenAI Features:** VAE latent → feed into site dating (regression); ablation: spectral vs. VAE features.
- **L7 Agentic:** **Structured** — Agent recommends "excavate site X next" for maximal chronological information; **Autonomous** — Agent reconstructs "most likely cultural transmission network" from style diffusion patterns.
- **Rediscovery thread:** L1 rediscovers Petrie's seriation as spectral ordering; L2 quantifies chronological uncertainty; L5 hallucinates missing data; L6 improves dating; L7 guides excavation strategy.

---

## 11. **CS023: Molecular Property Extrapolation — Rediscovering QSAR Rules from 50 Molecules**
**Disciplines:** Chemistry & Chemical Engineering × ML (Gaussian Processes, Active Learning)
**Hook:** Given 50 molecules with measured logP/solubility/toxicity, use a GP with a Tanimoto kernel (molecular fingerprints) to *predict* properties of 10k virtual molecules. The rediscovery: the model learns Lipinski's Rule of Five boundaries (MW<500, logP<5, HBD<5, HBA<10) as high-uncertainty regions — "drug-like space" emerges from uncertainty, not labels. Active learning loop: query the oracle at max uncertainty, watch Rule of Five boundary sharpen.
**House fit:** Extreme small-data regime (like CS001); rediscovery of medicinal chemistry heuristics; active learning loop (agent-like); uncertainty visualization on chemical space.
**CPU feasibility:** **Easy** — 50×50 kernel matrix; 10k predictions via kernel vector products.
**Novelty:** Most QSAR uses 10k+ labeled molecules; this shows *rules emerge from uncertainty geometry* with n=50. Active learning as "agent choosing experiments" ties to X.3 Agent track.
**House stack fit:**
- **L1 Supervised+Unsupervised:** Supervised — GP regression (fingerprint → property); Unsupervised — cluster virtual library in fingerprint space; detect "drug-like" region as high-density cluster.
- **L2 XAI:** SHAP on GP predictions; intrinsic — kernel lengthscales = fragment importance; uncertainty contours = Rule of Five boundaries.
- **L3 Deep Learning:** Small MPNN (Message Passing NN, ~20k params) on molecular graphs — CPU <5 min; or MLP on fingerprints.
- **L4 Foundation Models:** **MolBERT / ChemBERTa (frozen, ONNX CPU)** — 100M params but runs ~1s/mol on CPU; embeddings as GP kernel input.
- **L5 GenAI:** Conditional VAE / MolGPT (small, ~10M) on SMILES → generate molecules in target property range; GFlowNet for diverse generation.
- **L6 GenAI Features:** Foundation model embeddings / VAE latent → feed into GP as kernel features; ablation: Tanimoto vs. learned kernel.
- **L7 Agentic:** **Structured** — Active learning loop: agent selects max-uncertainty molecule for wet-lab assay; **Autonomous** — Agent designs "find me a molecule with logP∈[2,3], MW<400, low toxicity" via GFlowNet-guided search.
- **Rediscovery thread:** L1 rediscovers QSAR from tiny data; L2 shows Rule of Five as uncertainty geometry; L3 learns continuous representation; L4 transfers chemical knowledge; L5 explores chemical space; L6 fuses symbolic + learned features; L7 automates drug discovery loop.

---

## 12. **CS024: Gravitational Wave Glitch Classification — Rediscovering Noise Morphologies in LIGO Data**
**Disciplines:** Physics (General Relativity, Nuclear Physics) × ML (Time-Frequency, Anomaly Detection)
**Hook:** LIGO O3 public data: 10k+ glitches (non-astrophysical transients). Compute Q-transform spectrograms. Use a simple VAE or t-SNE on spectral features to *rediscover* the Gravity Spy classes: blip, whistle, scattered light, power line, koi fish — without labels. Plot: 2D embedding colored by true class (held out); example spectrograms per cluster.
**House fit:** Signal processing on extreme physics data (like CS007 QKD but for GR); rediscovery of known glitch taxonomy; beautiful time-frequency plots; anomaly detection flavor.
**CPU feasibility:** **Medium** — Q-transforms on 10k × 1s clips is heavy; use 2k subset + precomputed spectrograms.
**Novelty:** Most GW ML is supervised (signal vs. noise); this does *unsupervised glitch morphology discovery*. Directly hits Tier 7 (Nuclear Physics) and Tier 2 (DL/RL).
**House stack fit:**
- **L1 Supervised+Unsupervised:** Unsupervised — VAE / UMAP on Q-transform spectrograms; Supervised — predict Gravity Spy class from embedding (held-out labels).
- **L2 XAI:** SHAP on glitch classifier; intrinsic — VAE latent dimensions = morphology axes (frequency sweep, duration, bandwidth); reconstruction error = anomaly score.
- **L3 Deep Learning:** Small 2D CNN (3-layer, ~50k params) on spectrograms — CPU ~10 min for 2k samples.
- **L4 Foundation Models:** **CPU skip honest** — no GW foundation model on CPU. Use general audio foundation (AudioMAE, ONNX) for spectrogram embeddings.
- **L5 GenAI:** Conditional VAE (spectrogram | glitch class) → generate synthetic glitches for training detectors; diffusion on spectrograms.
- **L6 GenAI Features:** VAE latent + AudioMAE embeddings → feed into glitch vs. signal classifier; ablation.
- **L7 Agentic:** **Structured** — Agent flags "anomalous glitch cluster" for Gravity Spy volunteers; **Autonomous** — Agent optimizes "veto strategy" for O4 run: which aux channels to monitor for each glitch class.
- **Rediscovery thread:** L1 rediscovers glitch taxonomy unsupervised; L2 links latent dims to physical mechanisms; L3 classifies morphologies; L5 augments rare classes; L6 improves signal detection; L7 optimizes detector operations.

---

## 13. **CS025: Cognitive Bias Embedding — Rediscovering Kahneman & Tversky from Choice Data**
**Disciplines:** Behavioral Psychology × ML (Choice Modeling, Embedding)
**Hook:** Synthetic or public dataset (e.g., risky choice tasks: 1000 participants × 50 gambles). Embed participants and gambles in a joint space using a Bradley-Terry-Luce model with cognitive parameters (loss aversion λ, probability weighting γ). *Rediscover* the fourfold pattern: risk aversion for gains, risk seeking for losses, probability overweighting for small p. Plot: embedding space with prospect theory curves overlaid.
**House fit:** Rediscovery of Nobel-winning theory from raw choices; domain story (human irrationality); beautiful parameter recovery plots; connects to X.5 Trading (agent learning biases).
**CPU feasibility:** **Easy** — BTL model fits in seconds via MM algorithm or PyMC.
**Novelty:** Joint embedding of *agents* and *stimuli* reveals population structure in bias space. Directly hits Tier 3 (Behavioral Psychology) and Tier 5 (Trading).
**House stack fit:**
- **L1 Supervised+Unsupervised:** Unsupervised — joint embedding (participants × gambles) via BTL/IRT; cluster participants by bias profile; Supervised — predict choice from embedding.
- **L2 XAI:** Intrinsic — embedding coordinates = cognitive parameters (λ, γ, α); SHAP on choice predictor.
- **L3 Deep Learning:** Neural IRT (small MLP, ~5k params) for non-linear choice probability — CPU instant.
- **L4 Foundation Models:** **CPU skip honest** — no cognitive psychology foundation model. Skip.
- **L5 GenAI:** Conditional VAE on participant embeddings → generate synthetic participants with specified bias profiles (for simulation).
- **L6 GenAI Features:** VAE latent → feed into trading agent bias detector; ablation.
- **L7 Agentic:** **Structured** — Agent simulates "how would a loss-averse trader react to this portfolio?"; **Autonomous** — Agent designs "debiasing intervention" for a given bias profile (choice architecture nudge).
- **Rediscovery thread:** L1 rediscovers prospect theory parameters from choices; L2 visualizes bias space; L3 models non-linear probability weighting; L5 simulates populations; L6 detects biases in trading; L7 corrects them.

---

## 14. **CS026: Vedic Mental Arithmetic — Rediscovering Sutras as Algorithmic Primitives**
**Disciplines:** Vedic Mathematics × Abacus Mathematics × ML (Program Synthesis, Interpretable ML)
**Hook:** Encode the 16 Vedic sutras (e.g., "Vertically and Crosswise" for multiplication, "All from 9 and Last from 10" for subtraction) as rewrite rules. Use program synthesis (or brute-force search) to *rediscover* which sutra compositions solve arithmetic tasks optimally. Plot: decision tree of sutra selection; complexity comparison (Vedic vs. grade-school vs. Karatsuba).
**House fit:** Pure algorithmic rediscovery; domain story (ancient mental math as cognitive compression); interpretable by design; connects to X.1 Formal (derivations) and X.2 Conceptual (ELI5).
**CPU feasibility:** **Easy** — search space is tiny; synthesis runs in milliseconds.
**Novelty:** Treats Vedic math as a *domain-specific language for arithmetic* — not just tricks, but a compressed representation of number-theoretic identities. Hits Tier 0 (Abacus, Vedic) and X.3 Agent (learning to compose primitives).
**House stack fit:**
- **L1 Supervised+Unsupervised:** Unsupervised — cluster arithmetic problems by optimal sutra sequence; Supervised — predict optimal sutra from problem features (digit length, operation).
- **L2 XAI:** Intrinsic — decision tree / program = exact algorithm; SHAP on sutra selector.
- **L3 Deep Learning:** **Skip honest** — classical program synthesis *is* the model; no DL needed. Optional: Neural-guided search (tiny policy net).
- **L4 Foundation Models:** **CPU skip honest** — no program synthesis foundation model on CPU. Skip.
- **L5 GenAI:** LLM (small, e.g., Phi-3-mini ONNX) prompted with sutras → generate novel sutra compositions for new operations (division, square roots).
- **L6 GenAI Features:** LLM-generated programs → feed into synthesis as candidate primitives; ablation: human sutras only vs. human+LLM.
- **L7 Agentic:** **Structured** — Agent chooses sutra sequence for given problem (planner); **Autonomous** — Agent *discovers* new sutras by searching for compressed arithmetic identities (automated theorem proving).
- **Rediscovery thread:** L1 rediscovers optimal mental math algorithms; L2 makes them interpretable; L5 expands the sutra vocabulary; L6 hybridizes human+AI primitives; L7 automates algorithm discovery.

---

## 15. **CS027: Evolutionary Circuit Design — Rediscovering Classic Analog Topologies from Scratch**
**Disciplines:** Evolutionary Computation × Electronics & Electrical Engineering (deep) × ML (Neuroevolution)
**Hook:** Define a circuit grammar (resistors, caps, transistors, op-amps). Run evolutionary search (NEAT or CGP) to design: a bandpass filter, a differential pair, a voltage reference. *Rediscover* the classic topologies: Sallen-Key, Gilbert cell, Brokaw bandgap — without ever seeing a textbook. Plot: fitness over generations; best-of-gen schematics; bode plots converging to textbook specs.
**House fit:** Evolutionary computation as "agent learning" (X.3); rediscovery of engineering canon; beautiful schematics + frequency response plots; zero human design knowledge.
**CPU feasibility:** **Medium** — evolutionary search needs 1000s of SPICE evaluations; use a fast surrogate (analytic transfer functions) or small population on CPU.
**Novelty:** Most evolutionary electronics uses fixed topologies; this evolves *topology + sizing* from a grammar. Directly hits Tier 2 (Evolutionary Computation) and Tier 5 (Electronics deep).
**House stack fit:**
- **L1 Supervised+Unsupervised:** Unsupervised — cluster evolved circuits by topology; Supervised — predict circuit function (filter/amp/ref) from graph representation.
- **L2 XAI:** Intrinsic — evolved netlist = human-readable schematic; SHAP on function classifier.
- **L3 Deep Learning:** Graph NN on circuit graphs (~20k params) to predict transfer function — surrogate for SPICE; CPU feasible.
- **L4 Foundation Models:** **CPU skip honest** — no circuit foundation model. Skip.
- **L5 GenAI:** Graph VAE on circuit graphs → generate novel topologies; conditional on target specs (bandwidth, gain).
- **L6 GenAI Features:** VAE latent → feed into evolutionary search as initialization / mutation bias; ablation: random init vs. VAE-guided.
- **L7 Agentic:** **Structured** — Agent runs evolutionary loop with human-in-the-loop constraint checks; **Autonomous** — Agent designs "op-amp with GBW>10MHz, PM>60°" end-to-end: grammar → evolution → verification → netlist.
- **Rediscovery thread:** L1 rediscovers classic topologies via evolution; L2 yields readable schematics; L3 accelerates evaluation; L5 explores topology space; L6 bootstraps evolution; L7 closes the design loop.

---

## 16. **CS028: Orbital Debris Taxonomy — Clustering Space Objects by Light Curve Shape**
**Disciplines:** Satellite & Space Systems Engineering × ML (Time Series, Clustering)
**Hook:** Light curves of 5000+ RSOs (Resident Space Objects) from ground-based telescopes. Cluster by shape (DTW + k-medoids) to *rediscover* object classes: intact rocket bodies (stable tumbling), fragmentation debris (chaotic), solar panels (specular glints), painted surfaces (diffuse). Plot: medoid light curves per cluster; 3D attitude reconstruction from photometry.
**House fit:** Space domain story (orbital sustainability); unsupervised morphology discovery (like CS018 exoplanets); photometry as rich signal; connects to X.5 (space situational awareness as decision-making).
**CPU feasibility:** **Medium** — similar to CS018; DTW on subset + DBA.
**Novelty:** Most space object classification uses radar cross-section + orbit; this uses *photometric signature alone* — passive, scalable, works for GEO.
**House stack fit:**
- **L1 Supervised+Unsupervised:** Unsupervised — DTW + k-medoids / shapelet clustering on light curves; Supervised — predict object type (rocket/debris/payload) from cluster (held-out labels).
- **L2 XAI:** SHAP on type classifier; intrinsic — medoid curves = archetypes; shapelets = discriminative glints/tumbles.
- **L3 Deep Learning:** 1D CNN / TCN on light curves (~30k params) — CPU <10 min.
- **L4 Foundation Models:** **CPU skip honest** — no space photometry foundation model. Skip.
- **L5 GenAI:** Conditional VAE (light curve | object class) → generate synthetic light curves for rare classes (intact payloads).
- **L6 GenAI Features:** VAE latent → feed into classifier; ablation: raw vs. shapelet vs. VAE.
- **L7 Agentic:** **Structured** — Agent schedules "observe object X at phase Y" for max information gain; **Autonomous** — Agent correlates light curve clusters with TLE orbital elements → infers "this cluster = fragmentation event at epoch Z."
- **Rediscovery thread:** L1 rediscovers object taxonomy from photometry; L2 links morphology to physical structure; L3 generalizes to new objects; L5 augments rare classes; L6 improves classification; L7 fuses photometry + orbital dynamics.

---

## 17. **CS029: Nuclear Reactor Noise — Anomaly Detection in Neutron Flux Fluctuations**
**Disciplines:** Nuclear Physics × ML (Time Series Anomaly Detection, Signal Processing)
**Hook:** Simulated or real neutron detector time series from a PWR (ex-core detectors). Normal operation = stationary stochastic process (neutron noise). Inject anomalies: control rod vibration, coolant boiling, fuel assembly vibration. Train a normalizing flow or LSTM-autoencoder on normal data; *detect* anomalies via likelihood drop. Rediscovery: the frequency peaks (1/3 Hz rod vibration, 0.5 Hz boiling) match known physics. Plot: spectrogram + anomaly score over time.
**House fit:** Physics-informed anomaly detection (like CS007 QKD but for nuclear); domain story (safety critical); spectral signatures as fingerprints; streaming inference flavor.
**CPU feasibility:** **Medium** — normalizing flows train fast on CPU for 1D time series; simulation via point kinetics is trivial.
**Novelty:** Most nuclear monitoring uses spectral peaks (hand-crafted); this learns the *normal manifold* and detects deviations. Hits Tier 7 (Nuclear Physics) and Tier 2 (DL/RL).
**House stack fit:**
- **L1 Supervised+Unsupervised:** Unsupervised — normalizing flow / LSTM-AE learns normal manifold; Supervised — classify anomaly type from anomaly score + spectral features (small labeled set).
- **L2 XAI:** SHAP on anomaly classifier; intrinsic — flow likelihood = anomaly score; spectral peaks in reconstruction error = fault signature.
- **L3 Deep Learning:** Normalizing Flow (RealNVP, ~20k params) or LSTM-AE (~30k params) — CPU <5 min.
- **L4 Foundation Models:** **CPU skip honest** — no nuclear foundation model. Skip.
- **L5 GenAI:** Normalizing Flow *is* generative — sample normal operation for simulation; conditional Flow (anomaly type) → generate fault signatures for training.
- **L6 GenAI Features:** Flow latent / reconstruction error → feed into anomaly classifier; ablation.
- **L7 Agentic:** **Structured** — Agent monitors streaming data, triggers "investigate rod vibration" alert; **Autonomous** — Agent recommends "insert control bank D 5 steps" to suppress oscillation (control action).
- **Rediscovery thread:** L1 learns normal neutron noise manifold; L2 identifies fault frequencies; L3 models stochastic dynamics; L5 generates fault signatures; L6 enables classification; L7 closes the safety loop.

---

## 18. **CS030: Special Relativity — Learning Lorentz Invariance from Particle Collision Data**
**Disciplines:** Special Relativity (Tier 6) × ML (Equivariant Networks, Symmetry Discovery)
**Hook:** Generate synthetic particle collisions (2→2 scattering) in the lab frame. Train an equivariant neural network to predict Mandelstam variables (s, t, u) from 4-momenta. *Rediscover* Lorentz invariance: the network learns to boost to the center-of-mass frame internally. Ablate equivariance → performance drops; enforce it → perfect generalization to unseen boosts. Plot: prediction error vs. boost γ; attention on 4-vectors.
**House fit:** Rediscovery of a fundamental symmetry (like CS006 rediscovering memory laws); domain story (Einstein from data); beautiful symmetry visualization; equivariant ML is hot.
**CPU feasibility:** **Easy** — synthetic data generation is fast; small equivariant network trains in minutes on CPU.
**Novelty:** Frames symmetry discovery as *representation learning with inductive bias ablation*. Directly hits Tier 6 (Special Relativity) and Tier 2 (GPU Programming equivariant kernels, Deep Learning).
**House stack fit:**
- **L1 Supervised+Unsupervised:** Supervised — equivariant net predicts Mandelstam s,t,u; Unsupervised — cluster events by Lorentz-invariant features (invariant mass).
- **L2 XAI:** Intrinsic — equivariant layers = explicit Lorentz transformation; attention on 4-vectors = frame-invariant attention; ablation: equivariant vs. non-equivariant.
- **L3 Deep Learning:** Equivariant GNN / Tensor Field Network (2-layer, ~15k params) — CPU feasible; baseline: non-equivariant MLP.
- **L4 Foundation Models:** **CPU skip honest** — no particle physics foundation model on CPU. Skip.
- **L5 GenAI:** Equivariant VAE on 4-momenta → generate Lorentz-invariant collision events; conditional on sqrt(s).
- **L6 GenAI Features:** VAE latent (invariant) → feed into Mandelstam predictor; ablation: equivariant net with vs. without invariant latent.
- **L7 Agentic:** **Structured** — Agent designs "simulate collision at sqrt(s)=X TeV" for generator tuning; **Autonomous** — Agent discovers "new symmetry in this dataset" by testing equivariance w.r.t. candidate groups (automated symmetry discovery).
- **Rediscovery thread:** L1 learns Lorentz invariance from data; L2 proves it via ablation; L3 bakes symmetry into architecture; L5 generates symmetric data; L6 uses invariant latents; L7 automates symmetry discovery.