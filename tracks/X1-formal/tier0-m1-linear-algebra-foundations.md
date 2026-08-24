# Tier 0 · Module 1 · Formal — Linear Algebra Foundations

## Objective
Formal fluency with vectors, vector spaces, norms, dot products, and matrices-as-transformations — the mathematical substrate every later module (ML, physics, robotics, quantum computing) is built on.

## Curriculum

### 1. Vectors and vector spaces
A vector space over a field (we'll use ℝ) is a set closed under addition and scalar multiplication, satisfying associativity, commutativity, distributivity, and the existence of a zero vector and additive inverses. A vector v ∈ ℝⁿ is an ordered tuple (x₁, ..., xₙ).

### 2. Norms
A norm ‖·‖ is any function satisfying: (i) ‖v‖ ≥ 0, and = 0 iff v = 0; (ii) ‖αv‖ = |α|‖v‖; (iii) triangle inequality ‖u+v‖ ≤ ‖u‖+‖v‖.
- **L2 (Euclidean) norm:** ‖v‖₂ = √(x₁² + ... + xₙ²)
- **L1 norm:** ‖v‖₁ = |x₁| + ... + |xₙ|

### 3. Normalization
- **L2-normalize:** v / ‖v‖₂ → unit vector, ‖v‖₂ = 1. Components can be negative; they do not need to sum to 1.
- **L1-normalize:** v / ‖v‖₁ → if v has non-negative components, this produces a vector whose components sum to 1 — a probability distribution. This is the distinction between the L2 sphere (direction-preserving geometry) and the probability simplex (mass-allocation geometry); they are not interchangeable.

### 4. Dot product and cosine similarity
u · v = Σ uᵢvᵢ. Geometrically, u · v = ‖u‖‖v‖cos(θ). Cosine similarity = (u · v) / (‖u‖‖v‖) isolates the angular alignment between two vectors independent of their magnitude — the standard operational measure of "how similar are these two states/representations."

### 5. Matrices as transformations
A matrix A ∈ ℝᵐˣⁿ maps v ∈ ℝⁿ to Av ∈ ℝᵐ. The vector space itself is unchanged; the transformation acts on the coordinates of the vector, not the space. A composition of matrices is a chain of transformations.

## Problem set

1. Given v = (1,2), w = (2,4): are they the same direction? Prove it using the definition of cosine similarity.
2. Compute the dot product and cosine similarity of v = (1,0,1), w = (0,1,1). What angle does this correspond to?
3. Normalize v = (3,4) under L2. Normalize v = (2,3,5) under L1. Which one is now a valid probability distribution, and why does the other one fail that test even though all its components are positive?
4. Normalize v = (−3,4) under L2. Show that L2 normalization does *not* guarantee components in [0,1].
5. If cosine similarity between two vectors is 0, what does that mean geometrically, and what would it mean if those two vectors were successive "state" snapshots of a learning system?
6. Explain, using only the definitions above, why Euclidean distance can be a worse similarity measure than cosine similarity for high-dimensional representations.

## Mastery checkpoint
Intermediate bar reached at: can derive (not just recall) cosine similarity from the dot-product definition, can correctly choose L1 vs. L2 normalization for a given downstream use (probability output vs. embedding direction) without prompting, and can implement both from scratch (see X.3 for the agent-code seed this module produces).
