# Case Study Pitches for Nova — Lyra's Polymath-Driven Ideas

**Style target:** Applied ML notebooks with domain story + methods + plots + "rediscovery" flavor (like CS001–CS012).
**Constraint:** No neuroscience/EEG (CS002), no robotics grasp/swarm (CS003/005), no finance panels (CS008), no rockets (CS009), no intrusion detection (CS010), no data quality drift (CS011), no speech recognition (CS012), no targeted alpha therapy (CS001), no QKD (CS007).

Each pitch: **Title | Linked discipline(s) | 3–5 sentence hook | Why it fits house style | CPU feasibility | Novelty note**

---

## 1. **CS013: Harmonic Syntax — Rediscovering Music Theory via Unsupervised Graph Learning**
**Disciplines:** Music (implied by Biological Science & Engineering, Information Theory, Graph Learning) × ML
**Hook:** Treat a corpus of symbolic music (MusicXML/MIDI) as a graph of note transitions and harmonic contexts. Apply spectral clustering and graph autoencoders to *rediscover* the circle of fifths, functional harmony categories (tonic/subdominant/dominant), and voice-leading rules — without ever teaching the model a single music theory concept. The "aha" plot: a 2D embedding where major/minor keys separate cleanly and the circle of fifths emerges as a topological loop.
**House fit:** Pure rediscovery flavor (like CS006's memory decay curves), domain story (music as humanity's oldest structured information), beautiful visualizations (embeddings, adjacency heatmaps), minimal supervision.
**CPU feasibility:** **Easy** — symbolic music is tiny; graph construction and spectral methods run in seconds on CPU.
**Novelty:** Most music ML focuses on generation; this frames theory *discovery* as unsupervised representation learning. Connects Information Theory (entropy of harmonic surprise) to Graph Learning (community detection = key areas).

---

## 2. **CS014: Phylogenetic Echoes — Reconstructing Language Families from Cognate Networks**
**Disciplines:** Linguistics (Biological Science & Engineering, Evolutionary Computation, Graph Learning) × ML
**Hook:** Build a weighted graph of cognate sets across 200+ languages (using ASJP or Lexibank data). Apply minimum spanning tree + hierarchical clustering to *rediscover* the Indo-European, Afro-Asiatic, Austronesian family trees — and detect known controversies (e.g., Altaic, Dene-Yeniseian) as ambiguous edges. Bonus: simulate lexical borrowing as edge rewiring and watch how "areal features" distort the tree.
**House fit:** Rediscovery of known science (comparative linguistics) from raw data; evolutionary computation angle (simulated borrowing = horizontal gene transfer); dendrograms + geographic maps as plots.
**CPU feasibility:** **Easy** — distance matrices of 200 languages are trivial; MST and clustering are O(n²) with n≈200.
**Novelty:** Frames historical linguistics as graph community detection with adversarial noise (borrowing). Bridges Evolutionary Computation (phylogenetics) and Graph Learning — both in Vishnu's Tier 2.

---

## 3. **CS015: Material Memory — Predicting Alloy Phase Diagrams from Sparse Experimental Data**
**Disciplines:** Materials Science & Engineering × Chemistry & Chemical Engineering × ML (Data Science, Sparse Regression)
**Hook:** Given a sparse ternary alloy dataset (composition → phase labels from CALPHAD or experimental papers), use Gaussian Process regression with physics-informed kernels (Gibbs free energy constraints) to *reconstruct* the full phase diagram. The rediscovery: the model "learns" lever rule, tie-lines, and eutectic points from ~50 data points. Plot: ternary heatmaps with uncertainty contours.
**House fit:** Materials informatics is a perfect "small data, big physics" domain — like CS001 (targeted alpha) but for alloys. Sparse data + strong priors = core Nova aesthetic.
**CPU feasibility:** **Medium** — GPs scale O(n³) but n<500; sparse approximations keep it CPU-friendly.
**Novelty:** Most materials ML uses massive DFT datasets; this uses *human-curated sparse experimental data* — the real bottleneck in alloy design. Ties to Vishnu's Tier 5 (Materials, Chemistry).

---

## 4. **CS016: Paleoclimate Proxy Fusion — Reconstructing Holocene Temperature from Noisy Multi-Proxy Records**
**Disciplines:** Climate/Ecology (Engineering Physics & Astronomy, Satellite & Space Systems) × ML (Time Series, State Space Models)
**Hook:** Fuse ice cores (δ¹⁸O), tree rings, speleothems, and marine sediments — each with different temporal resolution, dating uncertainty, and climate sensitivity — into a single latent temperature reconstruction using a hierarchical state-space model. The rediscovery: the Medieval Warm Period, Little Ice Age, and 8.2 kyr event emerge *without* being prescribed. Plot: spaghetti of proxy records → clean posterior with credible intervals.
**House fit:** Multi-source noisy data fusion (like CS004 AV fleet, CS011 data drift); domain story (Earth's memory); beautiful uncertainty visualization; physics-informed priors (Milankovitch cycles).
**CPU feasibility:** **Medium** — MCMC on ~10k time points is heavy but doable with variational inference or Kalman smoothing on CPU.
**Novelty:** Treats dating uncertainty as a first-class latent variable (not pre-aligned). Connects Satellite/Space (remote sensing proxies) to Tier 2 time-series ML.

---

## 5. **CS017: Legalese Embedding Geometry — Rediscovering Contract Clause Taxonomies from SEC Filings**
**Disciplines:** Law/NLP (Software Engineering, LLM/Generative AI) × ML (NLP, Clustering)
**Hook:** Embed 50k+ "Risk Factors" sections from 10-K filings using a small BERT (or TF-IDF + SVD for pure CPU). Cluster to *rediscover* the latent taxonomy of corporate risk: supply chain, regulatory, cyber, macroeconomic, litigation — and track how cluster centroids drift post-2020 (COVID), post-2022 (inflation), post-2023 (AI). Plot: UMAP of risk space with temporal trajectories.
**House fit:** Domain story (corporate anxiety as literature); rediscovery of known risk categories from raw text; temporal drift visualization (like CS011 but semantic); zero-shot taxonomy induction.
**CPU feasibility:** **Easy** — TF-IDF + TruncatedSVD runs in seconds; small BERT via ONNX/CPU is fine.
**Novelty:** Most legal NLP does classification; this does *unsupervised taxonomy discovery + temporal dynamics*. Ties LLM track to Behavioral Psychology (corporate risk perception).

---

## 6. **CS018: Exoplanet Light Curve Archetypes — Unsupervised Discovery of Transit Morphologies**
**Disciplines:** Astronomy (Engineering Physics & Astronomy, Satellite & Space Systems) × ML (Time Series Clustering, Shapelets)
**Hook:** Take 100k+ Kepler/TESS light curves. Normalize, align, and cluster using Dynamic Time Warping + k-medoids to *rediscover* the taxonomy: hot Jupiters (V-shape), grazing transits, disintegrating planets (asymmetric tails), binary star eclipses (double dips), stellar variability (sinusoidal). The "rediscovery" plot: medoid light curves labeled by human astronomers vs. cluster assignments.
**House fit:** Pure unsupervised morphology discovery (like CS005 drone swarm but for astrophysics); domain story (hunting worlds); beautiful folded light curve plots; zero labels needed.
**CPU feasibility:** **Medium** — DTW is O(n²) but 100k × 100k is too much; use random subset (5k) + DTW barycenter averaging (DBA) or shapelet transform.
**Novelty:** Most exoplanet ML is supervised (transit vs. false positive); this discovers *morphological classes* including rare/weird ones. Connects Space Systems to Tier 2 time-series ML.

---

## 7. **CS019: Epidemiological Wavelet — Rediscovering Disease Seasonality from Noisy Case Counts**
**Disciplines:** Epidemiology (Biological Science & Engineering) × ML (Signal Processing, State Space, Information Theory)
**Hook:** Weekly case counts for 50+ diseases (Dengue, Flu, Measles, Cholera) across 20 countries. Apply wavelet denoising + harmonic regression to *rediscover* annual/biannual cycles, climate-driven phase shifts (El Niño), and the "epidemic clock" — the phase relationship between latitude and peak timing. Plot: polar phase maps + wavelet scalograms.
**House fit:** Signal processing on biological data (like CS002 EEG but for populations); rediscovery of known epidemiology (seasonality); Information Theory angle (predictability horizon = mutual information between climate drivers and cases).
**CPU feasibility:** **Easy** — wavelet transforms and harmonic regression are O(n log n) and tiny data.
**Novelty:** Frames seasonality as *phase synchronization* across latitudes — a Kuramoto oscillator view of epidemics. Bridges Tier 4 (Bio) and Tier 2 (Info Theory, Signal Processing).

---

## 8. **CS020: Quantum Error Syndrome Decoding — Learning the Surface Code's Logical Operators from Syndrome Graphs**
**Disciplines:** Quantum Computing × Graph Learning × ML (Graph Neural Networks)
**Hook:** Simulate a distance-5 surface code under circuit-level noise. Feed syndrome graphs (stabilizer measurements → detection events) to a graph neural network that *learns* the logical operator (X/Z) without being taught the code structure. Rediscovery: the GNN learns minimum-weight perfect matching (MWPM) implicitly — and fails exactly where MWPM fails (correlated errors). Plot: decoding accuracy vs. physical error rate; attention heatmaps on syndrome graph.
**House fit:** Rediscovery of a known algorithm (MWPM) via learned representation; domain story (quantum fault tolerance); beautiful graph visualizations; zero domain knowledge in the model.
**CPU feasibility:** **Hard** — GNN training on CPU is slow; but distance-3 code with small graphs is doable. Recommend distance-3 for CPU, distance-5 for GPU.
**Novelty:** Most quantum decoding papers use MWPM or tensor networks; this frames decoding as *graph representation learning*. Directly hits Vishnu's Tier 7 (Quantum Computing) and Tier 2 (Graph Learning).

---

## 9. **CS021: Sports Biomechanics — Rediscovering the "Kinetic Chain" from Markerless Pose Estimation**
**Disciplines:** Sports Biomechanics (Robotics & Ground-based Autonomous Systems, Biological Science & Engineering) × ML (Pose Estimation, Dynamics)
**Hook:** Use OpenPose/MediaPipe on 1000+ YouTube videos of baseball pitches, tennis serves, golf swings. Compute joint angles, angular velocities, and estimate segment energies. *Rediscover* the proximal-to-distal sequencing (kinetic chain): pelvis → torso → shoulder → elbow → wrist. Plot: phase plots of joint angles; energy transfer bar charts; "ideal" vs. "amateur" trajectories.
**House fit:** Human motion as optimal control (like CS003 robot grasp but biological); rediscovery of known biomechanics; beautiful phase portraits; zero supervised labels (self-supervised from video).
**CPU feasibility:** **Medium** — pose estimation on 1000 videos is heavy on CPU; use a subset (100) +(MediaPipe is fast). Dynamics calculations are trivial.
**Novelty:** Most sports ML classifies actions; this *derives biomechanical principles* from raw video. Connects Robotics (Tier 5) to Bio (Tier 4) via self-supervised pose.

---

## 10. **CS022: Archaeological Seriation — Reconstructing Pottery Chronologies from Style Co-occurrence**
**Disciplines:** Archaeology (implied by Biological Science, Evolutionary Computation) × ML (Seriation, Ordinal Embedding)
**Hook:** Binary matrix: sites × pottery styles (presence/absence). Apply spectral seriation (Fiedler vector of similarity matrix) to *reconstruct* the temporal ordering of sites — the classic archaeological problem solved by Petrie (1899) and Kendall (1971). Rediscovery: the 1D embedding matches known stratigraphy. Add noise (looting, mixing) and watch the embedding degrade gracefully. Plot: Fiedler vector vs. true dates; Robinson matrix heatmaps.
**House fit:** Pure rediscovery of a 100-year-old method (seriation) via modern spectral graph theory; domain story (time from trash); elegant 1D visualizations; connects to Information Theory (optimal ordering = minimum description length).
**CPU feasibility:** **Easy** — eigendecomposition of 100×100 matrix is instant.
**Novelty:** Frames seriation as *spectral ordering with uncertainty quantification* — Bayesian seriation via MCMC on the latent order. Bridges Evolutionary Computation (cultural evolution) and Graph Learning.

---

## 11. **CS023: Molecular Property Extrapolation — Rediscovering QSAR Rules from 50 Molecules**
**Disciplines:** Chemistry & Chemical Engineering × ML (Gaussian Processes, Active Learning)
**Hook:** Given 50 molecules with measured logP/solubility/toxicity, use a GP with a Tanimoto kernel (molecular fingerprints) to *predict* properties of 10k virtual molecules. The rediscovery: the model learns Lipinski's Rule of Five boundaries (MW<500, logP<5, HBD<5, HBA<10) as high-uncertainty regions — "drug-like space" emerges from uncertainty, not labels. Active learning loop: query the oracle at max uncertainty, watch Rule of Five boundary sharpen.
**House fit:** Extreme small-data regime (like CS001); rediscovery of medicinal chemistry heuristics; active learning loop (agent-like); uncertainty visualization on chemical space.
**CPU feasibility:** **Easy** — 50×50 kernel matrix; 10k predictions via kernel vector products.
**Novelty:** Most QSAR uses 10k+ labeled molecules; this shows *rules emerge from uncertainty geometry* with n=50. Active learning as "agent choosing experiments" ties to X.3 Agent track.

---

## 12. **CS024: Gravitational Wave Glitch Classification — Rediscovering Noise Morphologies in LIGO Data**
**Disciplines:** Physics (General Relativity, Nuclear Physics) × ML (Time-Frequency, Anomaly Detection)
**Hook:** LIGO O3 public data: 10k+ glitches (non-astrophysical transients). Compute Q-transform spectrograms. Use a simple VAE or t-SNE on spectral features to *rediscover* the Gravity Spy classes: blip, whistle, scattered light, power line, koi fish — without labels. Plot: 2D embedding colored by true class (held out); example spectrograms per cluster.
**House fit:** Signal processing on extreme physics data (like CS007 QKD but for GR); rediscovery of known glitch taxonomy; beautiful time-frequency plots; anomaly detection flavor.
**CPU feasibility:** **Medium** — Q-transforms on 10k × 1s clips is heavy; use 2k subset + precomputed spectrograms.
**Novelty:** Most GW ML is supervised (signal vs. noise); this does *unsupervised glitch morphology discovery*. Directly hits Tier 6/7 (Relativity, Nuclear Physics).

---

## 13. **CS025: Cognitive Bias Embedding — Rediscovering Kahneman & Tversky from Choice Data**
**Disciplines:** Behavioral Psychology × ML (Choice Modeling, Embedding)
**Hook:** Synthetic or public dataset (e.g., risky choice tasks: 1000 participants × 50 gambles). Embed participants and gambles in a joint space using a Bradley-Terry-Luce model with cognitive parameters (loss aversion λ, probability weighting γ). *Rediscover* the fourfold pattern: risk aversion for gains, risk seeking for losses, probability overweighting for small p. Plot: embedding space with prospect theory curves overlaid.
**House fit:** Rediscovery of Nobel-winning theory from raw choices; domain story (human irrationality); beautiful parameter recovery plots; connects to X.5 Trading (agent learning biases).
**CPU feasibility:** **Easy** — BTL model fits in seconds via MM algorithm or PyMC.
**Novelty:** Joint embedding of *agents* and *stimuli* reveals population structure in bias space. Directly hits Tier 3 (Behavioral Psychology) and Tier 5 (Trading).

---

## 14. **CS026: Vedic Mental Arithmetic — Rediscovering Sutras as Algorithmic Primitives**
**Disciplines:** Vedic Mathematics × Abacus Mathematics × ML (Program Synthesis, Interpretable ML)
**Hook:** Encode the 16 Vedic sutras (e.g., "Vertically and Crosswise" for multiplication, "All from 9 and Last from 10" for subtraction) as rewrite rules. Use program synthesis (or brute-force search) to *rediscover* which sutra compositions solve arithmetic tasks optimally. Plot: decision tree of sutra selection; complexity comparison (Vedic vs. grade-school vs. Karatsuba).
**House fit:** Pure algorithmic rediscovery; domain story (ancient mental math as cognitive compression); interpretable by design; connects to X.1 Formal (derivations) and X.2 Conceptual (ELI5).
**CPU feasibility:** **Easy** — search space is tiny; synthesis runs in milliseconds.
**Novelty:** Treats Vedic math as a *domain-specific language for arithmetic* — not just tricks, but a compressed representation of number-theoretic identities. Hits Tier 0 (Abacus, Vedic) and X.3 Agent (learning to compose primitives).

---

## 15. **CS027: Evolutionary Circuit Design — Rediscovering Classic Analog Topologies from Scratch**
**Disciplines:** Evolutionary Computation × Electronics & Electrical Engineering (deep) × ML (Neuroevolution)
**Hook:** Define a circuit grammar (resistors, caps, transistors, op-amps). Run evolutionary search (NEAT or CGP) to design: a bandpass filter, a differential pair, a voltage reference. *Rediscover* the classic topologies: Sallen-Key, Gilbert cell, Brokaw bandgap — without ever seeing a textbook. Plot: fitness over generations; best-of-gen schematics; bode plots converging to textbook specs.
**House fit:** Evolutionary computation as "agent learning" (X.3); rediscovery of engineering canon; beautiful schematics + frequency response plots; zero human design knowledge.
**CPU feasibility:** **Medium** — evolutionary search needs 1000s of SPICE evaluations; use a fast surrogate (analytic transfer functions) or small population on CPU.
**Novelty:** Most evolutionary electronics uses fixed topologies; this evolves *topology + sizing* from a grammar. Directly hits Tier 2 (Evolutionary Computation) and Tier 5 (Electronics deep).

---

## 16. **CS028: Orbital Debris Taxonomy — Clustering Space Objects by Light Curve Shape**
**Disciplines:** Satellite & Space Systems Engineering × ML (Time Series, Clustering)
**Hook:** Light curves of 5000+ RSOs (Resident Space Objects) from ground-based telescopes. Cluster by shape (DTW + k-medoids) to *rediscover* object classes: intact rocket bodies (stable tumbling), fragmentation debris (chaotic), solar panels (specular glints), painted surfaces (diffuse). Plot: medoid light curves per cluster; 3D attitude reconstruction from photometry.
**House fit:** Space domain story (orbital sustainability); unsupervised morphology discovery (like CS018 exoplanets); photometry as rich signal; connects to X.5 (space situational awareness as decision-making).
**CPU feasibility:** **Medium** — similar to CS018; DTW on subset + DBA.
**Novelty:** Most space object classification uses radar cross-section + orbit; this uses *photometric signature alone* — passive, scalable, works for GEO.

---

## 17. **CS029: Nuclear Reactor Noise — Anomaly Detection in Neutron Flux Fluctuations**
**Disciplines:** Nuclear Physics × ML (Time Series Anomaly Detection, Signal Processing)
**Hook:** Simulated or real neutron detector time series from a PWR (ex-core detectors). Normal operation = stationary stochastic process (neutron noise). Inject anomalies: control rod vibration, coolant boiling, fuel assembly vibration. Train a normalizing flow or LSTM-autoencoder on normal data; *detect* anomalies via likelihood drop. Rediscovery: the frequency peaks (1/3 Hz rod vibration, 0.5 Hz boiling) match known physics. Plot: spectrogram + anomaly score over time.
**House fit:** Physics-informed anomaly detection (like CS007 QKD but for nuclear); domain story (safety critical); spectral signatures as fingerprints; streaming inference flavor.
**CPU feasibility:** **Medium** — normalizing flows train fast on CPU for 1D time series; simulation via point kinetics is trivial.
**Novelty:** Most nuclear monitoring uses spectral peaks (hand-crafted); this learns the *normal manifold* and detects deviations. Hits Tier 7 (Nuclear Physics) and Tier 2 (DL/RL).

---

## 18. **CS030: Special Relativity — Learning Lorentz Invariance from Particle Collision Data**
**Disciplines:** Special Relativity (Tier 6) × ML (Equivariant Networks, Symmetry Discovery)
**Hook:** Generate synthetic particle collisions (2→2 scattering) in the lab frame. Train an equivariant neural network to predict Mandelstam variables (s, t, u) from 4-momenta. *Rediscover* Lorentz invariance: the network learns to boost to the center-of-mass frame internally. Ablate equivariance → performance drops; enforce it → perfect generalization to unseen boosts. Plot: prediction error vs. boost γ; attention on 4-vectors.
**House fit:** Rediscovery of a fundamental symmetry (like CS006 rediscovering memory laws); domain story (Einstein from data); beautiful symmetry visualization; equivariant ML is hot.
**CPU feasibility:** **Easy** — synthetic data generation is fast; small equivariant network trains in minutes on CPU.
**Novelty:** Frames symmetry discovery as *representation learning with inductive bias ablation*. Directly hits Tier 6 (Special Relativity) and Tier 2 (GPU Programming equivariant kernels, Deep Learning).