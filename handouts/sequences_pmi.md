# Handout 3 — Sequences, Subsequences, and PMI

*Research Lab Internship — Days 3–4*

---

## Part 1: Sequences and Subsequences

### Definitions

A **sequence** is an ordered list of numbers: a₁, a₂, a₃, ..., aₙ.

A **subsequence** is formed by deleting zero or more elements from a sequence, without changing the order of the remaining elements.

*Example:* From the sequence (5, 1, 4, 2, 8, 3, 7, 6):
- (5, 4, 8, 7) is a subsequence.
- (1, 2, 3, 6) is a subsequence.
- (5, 8, 7, 6) is a subsequence.
- (8, 4, 2) is **not** a subsequence (order is reversed).

**Increasing subsequence:** Each element is strictly larger than the previous one.  
*Example:* (1, 2, 3, 7) is an increasing subsequence of (5, 1, 4, 2, 8, 3, 7, 6).

**Decreasing subsequence:** Each element is strictly smaller than the previous one.  
*Example:* (8, 7, 6) is a decreasing subsequence.

**Longest Increasing Subsequence (LIS):** The increasing subsequence of maximum possible length.

---

### Warm-Up Puzzles

**Puzzle A.** Find the longest increasing subsequence of: (3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5).  
*(Tip: the elements don't have to be adjacent. Elements can be repeated in the sequence but a strictly increasing subseq uses distinct values.)*

**Puzzle B.** Find the longest *decreasing* subsequence of the same sequence.

**Puzzle C.** Given the sequence (9, 8, 7, 6, 5, 4, 3, 2, 1):
- What is the longest increasing subsequence?
- What is the longest decreasing subsequence?
- Are these answers surprising?

**Puzzle D.** Can you construct a sequence of 9 distinct numbers where:
- The longest increasing subsequence has length exactly 3, and
- The longest decreasing subsequence has length exactly 3?

*(Hint: think in a grid...)*

---

## Part 2: The Erdős–Szekeres Theorem

This is one of the most elegant results in combinatorics. It was proved by Paul Erdős and George Szekeres in 1935.

---

### Statement

**Theorem (Erdős–Szekeres, 1935):**  
Any sequence of more than mn distinct numbers contains either an **increasing** subsequence of length **m+1** or a **decreasing** subsequence of length **n+1**.

**Special case:** Any sequence of n² + 1 distinct numbers must contain a monotone subsequence (increasing or decreasing) of length at least n+1.

---

### Examples Before the Proof

**Example 1:** n = m = 2. Any sequence of 5 distinct numbers has either an increasing or decreasing subsequence of length 3.

Check: (4, 3, 2, 1) — decreasing, length 4 ≥ 3. ✓  
Check: (1, 3, 2, 4) — increasing (1, 3, 4) or (1, 2, 4), length 3. ✓  
Check: (2, 4, 1, 3, 5) — increasing (1, 3, 5), length 3. ✓

**Example 2:** Can we have a sequence of 4 distinct numbers with no increasing or decreasing subsequence of length 3?

Try: (2, 4, 1, 3) — Note 4 > 2 and 3 > 1 and 3 > 1... longest increasing: (2,4) or (1,3) — length 2. Longest decreasing: (4,1) or (4,3) or (2,1) — length 2. Yes! We found a sequence of 4 elements with no monotone subsequence of length 3.

This shows the theorem's bound (mn + 1 = 5) is tight.

---

### Proof via Pigeonhole Principle

**Proof:**

Let a₁, a₂, ..., aₙ be our sequence of more than mn distinct numbers.

For each element aᵢ, define:
- **eᵢ** = length of the longest **increasing** subsequence **ending** at aᵢ (or starting — pick one convention and be consistent).
- **dᵢ** = length of the longest **decreasing** subsequence **ending** at aᵢ.

**Key observation:** If i < j and aᵢ < aⱼ (so aᵢ comes before and is smaller), then eⱼ ≥ eᵢ + 1.  
Similarly, if i < j and aᵢ > aⱼ, then dⱼ ≥ dᵢ + 1.

**Assume for contradiction:** No increasing subsequence of length m+1 exists and no decreasing subsequence of length n+1 exists. Then:
- Each eᵢ ∈ {1, 2, ..., m}
- Each dᵢ ∈ {1, 2, ..., n}

So each element aᵢ is assigned a pair (eᵢ, dᵢ) from {1,...,m} × {1,...,n}, which has only mn possible pairs.

We have more than mn elements but only mn possible pairs, so by the **Pigeonhole Principle**, two elements aᵢ and aⱼ (i < j) share the same pair: eᵢ = eⱼ and dᵢ = dⱼ.

But since i < j and all elements are distinct, either aᵢ < aⱼ or aᵢ > aⱼ:
- If aᵢ < aⱼ: then eⱼ ≥ eᵢ + 1. But eᵢ = eⱼ — contradiction.
- If aᵢ > aⱼ: then dⱼ ≥ dᵢ + 1. But dᵢ = dⱼ — contradiction.

In both cases we reach a contradiction. So our assumption was false: such a long increasing or decreasing subsequence must exist. □

---

### Walking Through the Proof with an Example

Consider the sequence (4, 3, 1, 2). We have 4 = 2² elements.

Compute (eᵢ, dᵢ) for each element (length of longest inc./dec. subseq. ending there):

| i | aᵢ | Longest inc. ending here | eᵢ | Longest dec. ending here | dᵢ |
|---|-----|--------------------------|-----|--------------------------|-----|
| 1 | 4 | (4) | 1 | (4) | 1 |
| 2 | 3 | (3) | 1 | (4,3) | 2 |
| 3 | 1 | (1) | 1 | (4,3,1) | 3 |
| 4 | 2 | (1,2) | 2 | (4,3,2) or (3,2) | 2 |

Pairs: (1,1), (1,2), (1,3), (2,2) — all distinct. The theorem guarantees that in any sequence of 5 elements, two would share a pair, forcing a contradiction. Here we only have 4 elements, so no contradiction is needed — and indeed we find no monotone subsequence of length 3 in this sequence.

---

## Part 3: From 1D to 2D

The Erdős–Szekeres theorem is about sequences — 1D objects. What about **2D point sets**?

### Points in the Plane

A **sequence of 2D points** is (P₁, P₂, ..., Pₙ) where each Pᵢ = (xᵢ, yᵢ).

**2D increasing subsequence:** A subsequence Pᵢ₁, Pᵢ₂, ..., Pᵢₖ (with i₁ < i₂ < ... < iₖ) such that:
$$x_{i_1} < x_{i_2} < \cdots < x_{i_k} \quad \text{and} \quad y_{i_1} < y_{i_2} < \cdots < y_{i_k}$$

Both coordinates increase simultaneously.

### Example

Points (in order): (3,1), (1,4), (2,3), (4,2), (5,5).

Looking for a 2D increasing subsequence:
- (3,1), (4,2), (5,5) — check: 3<4<5 ✓ and 1<2<5 ✓. Length 3.
- (1,4), (5,5) — check: 1<5 ✓ and 4<5 ✓. Length 2.
- Can we find length 4? We would need 4 points with both coordinates strictly increasing.

### Puzzle E.

Find the longest 2D increasing subsequence of:  
(5,1), (1,5), (3,3), (4,4), (2,2), (6,6).

---

## Part 4: PMI Sequences and Network Controllability

### Connecting Sequences to Zero Forcing

Recall from the zero forcing handout: every valid zero forcing propagation produces a **propagation sequence** — an ordering of the vertices recording when they turn blue.

For a **path graph** Pₙ with vertices labelled 1, 2, ..., n:
- Starting from vertex 1, the propagation sequence is (1, 2, 3, ..., n).
- This is an **increasing** sequence.

But what about more complex graphs?

### Propagation Sequences for Grid Graphs

For the 3×3 grid with vertices labelled by (row, column):

```
(1,1) — (1,2) — (1,3)
  |          |          |
(2,1) — (2,2) — (2,3)
  |          |          |
(3,1) — (3,2) — (3,3)
```

Starting with the top row blue, the propagation order is:

**(1,1), (1,2), (1,3), (2,1), (2,2), (2,3), (3,1), (3,2), (3,3)**

The row coordinate is non-decreasing throughout. Within each row, the column coordinate is increasing.

**Question:** What is the right 2D notion of "monotone" that captures all valid zero forcing propagation sequences for grid graphs?

### PMI Sequences (Formal Definition)

*(The precise definition will be provided by the coordinator based on the professor's research notes.)*

Informally, a **PMI (Propagation Monotone Increasing) sequence** is a sequence (of vertices from a graph, or of 2D points) satisfying a certain 2D monotonicity condition that:

1. Generalises the notion of an increasing sequence (in 1D, PMI = simply increasing).
2. Exactly characterises valid zero forcing propagation orders for certain graphs.
3. Has a combinatorial structure that can be studied independently, connecting to the Erdős–Szekeres framework.

### Why This Matters

The connection between PMI sequences and network controllability gives us a **new tool**:

- To determine if a graph is controllable from a given set S: check if the propagation sequence is a PMI sequence.
- To find the minimum Z(G): find the shortest PMI sequence that corresponds to a valid zero forcing propagation.
- The structure of PMI sequences can be studied using combinatorial methods (extensions of Erdős–Szekeres) rather than graph-theoretic methods.

---

## Exploration Problems

**E1.** For the 2×2 grid, list *all* valid zero forcing propagation sequences starting from the set {(1,1), (2,1)} (the left column). Which are "2D increasing"?

**E2.** For the 2×3 grid, find all zero forcing sets of minimum size. For each, write down all valid propagation sequences. Do any two of these look "the same" under some relabelling?

**E3.** The Erdős–Szekeres theorem says: sequence of n²+1 elements → monotone subseq. of length n+1. What would a **2D Erdős–Szekeres theorem** say? Try to formulate it.

**E4 (Open-ended research question).** The Erdős–Szekeres theorem has many proofs. One uses Dilworth's theorem from order theory. Can you state Dilworth's theorem and see how it implies Erdős–Szekeres?

---

## Homework

**H8.** Find a sequence of exactly mn distinct numbers with no increasing subsequence of length m+1 and no decreasing subsequence of length n+1. Show that your construction works. *(This proves the Erdős–Szekeres bound is tight.)*

**H9.** Prove: every sequence of n distinct numbers contains a monotone subsequence of length at least √n. *(Hint: use Erdős–Szekeres with m = n' chosen so mn = n.)*

**H10 (Challenge).** A *Young tableau* of shape (λ₁, λ₂, ..., λₖ) is an array of distinct numbers where each row is increasing left-to-right and each column is increasing top-to-bottom. The RSK correspondence is a beautiful bijection between permutations of {1,...,n} and pairs of Standard Young Tableaux of the same shape. Look up the RSK correspondence. What does it say about longest increasing subsequences?
