# Tier 0 · Module 1 · Conceptual — Linear Algebra Foundations

## ELI5
A vector is just a snapshot of "what something currently is," written as a list of numbers. A document's vector could be how often it uses each word; a market's vector could be its prices and risks; a brain's vector could be how active each neuron is. Different things, same trick: turn "what it is right now" into a list of numbers so you can do math on it.

Once you have that, two more questions become answerable: *how big is it* (norm), and *how similar are two of them* (cosine similarity). And a matrix is just a rule for turning one such list into another — a transformation from one state to a new state.

## The "why" behind the "what"
Representation comes before intelligence. No algorithm can learn well from a bad encoding — if the numbers you chose to describe a system throw away the information that mattered, no amount of clever math afterward will bring it back. Conversely, a good representation makes the answer almost fall out. This is why linear algebra — the study of representations and the transformations between them — sits underneath every other discipline in this curriculum, from ML to quantum mechanics to finance.

Normalization matters because raw magnitude is usually noise, not signal — a loud version of the same message and a quiet version of the same message should be treated as the same thing. Removing magnitude (normalizing) is how you isolate the part of the representation that actually carries meaning: direction (L2) or relative proportion (L1).

## Axioms extracted
- **Axiom: representation precedes intelligence.** No update rule can outperform the ceiling set by its encoding. *First seen: Linear Algebra Foundations. Reappears in: every ML module, quantum state representation, econometric feature engineering.*
- **Axiom: similarity enables reuse of experience.** "Have I seen something like this?" is answerable the moment two situations can be encoded as vectors and compared — this is the root of generalization. *First seen: Linear Algebra Foundations. Reappears in: attention mechanisms, kernel methods, energy-based models, quantum overlap.*
- **Axiom: normalization isolates signal from scale.** Raw magnitude is usually an artifact of volume/scale, not meaning; removing it (L1 or L2) reveals the structure that actually matters, and the *choice* between L1 and L2 encodes what kind of structure you care about (direction vs. mass allocation). *First seen: Linear Algebra Foundations. Reappears in: softmax layers, embedding spaces, probability theory, signal processing.*
- **Axiom: a transformation acts on coordinates, not on the space itself.** The map is not the territory — a matrix changes how a vector is described, not the underlying space it lives in. *First seen: Linear Algebra Foundations. Reappears in: coordinate changes in physics, basis changes in quantum mechanics, feature transforms in ML.*

## Seedling Log
- **X.3 seed:** implement `normalize()` (L1 and L2) and `cosine_similarity()` from scratch as the agent's foundational state-comparison primitives — this is the literal math behind comparing the agent's state across runs.
- **X.4 seed:** a short note-to-self on why L1 vs. L2 normalization choice is itself a modeling decision, not a default — could become a section in a future paper on representation choices in minimal agents.
- **X.5 seed:** if trading features (returns, volumes, risk factors) get L2-normalized before feeding a similarity-based signal, direction (momentum regime) is preserved while raw scale (position size) is removed — a candidate feature-engineering step for an experimental signal.
- **X.6 seed:** should the agent's own state comparison metric be reconsidered — is cosine similarity actually the right measure, or would an L1-based "mass allocation" comparison (treating the state as a distribution rather than a direction) better serve the agent's actual learning objective? Flag for first X.6 review.
