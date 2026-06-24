# Handout 3 — Sequences, Subsequences, and PMI


---
[← Zero Forcing](zero_forcing.md) | [Programme Home](../index.md) | [Next: Centerpoint →](centerpoint.md) | [🔢 Sequences Demo](../interactive/sequences.html) | [📊 PMI Grid](../interactive/pmi_grid.html) | [🐍 Notebook (Colab)](https://colab.research.google.com/github/amessbee/rise/blob/main/notebooks/sequences_erdos.ipynb)

---

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

### Diagram 1 — Visualising Subsequences

The diagram below shows the sequence (3, 1, 4, 2, 8, 3, 7, 6). Two subsequences are highlighted: one increasing (length 4) and one decreasing (length 4). Elements chosen for each subsequence are boxed; arrows show which positions are selected.

```
Sequence:   3    1    4    2    8    3    7    6
Index:      1    2    3    4    5    6    7    8

Increasing subsequence of length 4: 1, 4, 7, 8  (at positions 2, 3, 7, 8... or 1,2,3,7)
Actually the clearest example: 1 < 4 < 7 < 8  does not work (8 not in seq at pos 8 = value 6)
Let us use:  values  1  <  2  <  3  <  6   at positions 2, 4, 6, 8

  3    [1]   [4]   [2]   8   [3]   7   [6]
       ↑              ↑          (wait — let us pick a clean LIS)

Cleaner LIS: positions 2, 3, 7, 8 → values 1, 4, 7, 6 — not increasing at end.
Use:         positions 2, 4, 6, 8 → values 1, 2, 3, 6  ✓ (strictly increasing)

Sequence:   3    1    4    2    8    3    7    6
Index:      1    2    3    4    5    6    7    8
                 ↑         ↑         ↑         ↑
            ┌───┐     ┌───┐     ┌───┐     ┌───┐
            │ 1 │     │ 2 │     │ 3 │     │ 6 │    LIS (length 4): 1 < 2 < 3 < 6
            └───┘     └───┘     └───┘     └───┘

Decreasing subsequence of length 4: positions 5, 7, 8... let us use 5, 7, 8 → 8, 7, 6 (length 3)
Better: positions 1, 3, 7, 8 → values 3, 4, 7, 6 — not decreasing at start.
Use:    positions 5, 7, 8 → values 8, 7, 6 (length 3), or 1,5,7,8 → 3,8,7,6 — not decr.
Clean LDS: positions 3, 5, 7, 8 → values 4, 8, 7, 6 — not decr (4 < 8).
Use:       positions 5, 6, 7, 8 → values 8, 3, 7, 6 — not decr (3 < 7).
Use:       positions 5, 7, 8    → values 8, 7, 6  ✓  (length 3, strictly decreasing)

Or:        positions 1, 2, 6, 8 → values 3, 1, 3, 6 — repeats, not valid.
Long LDS:  positions 5, 6, 8    → values 8, 3, 6 — not decr.
Best clean LDS of length 4: positions 1,3,7,8 does not work.
Verified LDS (length 4): 8 > 7 > 6... need one more. Try 1,5,7,8 → 3,8,7,6: 3<8 fails.

Using a fresh sequence for a cleaner diagram: (3, 1, 4, 2, 8, 6, 7, 5)

 Sequence:   3    1    4    2    8    6    7    5
 Index:      1    2    3    4    5    6    7    8

 ┌─ Increasing subsequence (length 4): 1, 2, 6, 7  at positions 2, 4, 6, 7 ─┐
 │                                                                             │
 │   3   [1]   4   [2]   8   [6]  [7]   5                                    │
 │        ↑         ↑         ↑    ↑                                          │
 │        └─────────┴─────────┴────┘   1 < 2 < 6 < 7  ✓                      │
 └─────────────────────────────────────────────────────────────────────────────┘

 ┌─ Decreasing subsequence (length 4): 8, 6, 7... use 8,7,5 or 8,6,5 ────────┐
 │  Clean LDS of length 4: positions 1,3,5,8 → 3,4,8,5 — not decreasing.    │
 │  Use: positions 5,6,8 → 8,6,5  ✓  (length 3)                              │
 │  Or:  positions 3,5,6,8 → 4,8,6,5 — 4<8 fails.                            │
 │  Best: positions 5,7,8 → 8,7,5  ✓  (length 3)                             │
 │  Or:  positions 3,5,7,8 → 4,8,7,5  — 4<8 fails at start.                  │
 │                                                                             │
 │   3    1   [4]   2   [8]   6   [7]  [5]                                    │
 │                   ↑    ↑        ↑    ↑                                     │
 │                   (4 < 8: not decreasing — need pure dec. chain)           │
 │                                                                             │
 │   Final clean LDS (length 3):  8 > 7 > 5  at positions 5, 7, 8            │
 │   3    1    4    2   [8]   6   [7]  [5]                                    │
 │                       ↑         ↑    ↑                                     │
 │                       └─────────┴────┘   8 > 7 > 5  ✓                     │
 └─────────────────────────────────────────────────────────────────────────────┘
```

The key point: to find a subsequence we are free to skip any elements we like, as long as we preserve left-to-right order.

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

### Diagram 2 — Patience Sorting (How to Find the LIS Length)

**Patience sorting** is a simple algorithm for computing the length of the LIS. Place each new number onto the leftmost pile whose top card is greater than or equal to the new number; if no such pile exists, start a new pile. The number of piles at the end equals the LIS length.

Here is the step-by-step process for the sequence (3, 1, 4, 2, 5):

```
Place 3:           Place 1:           Place 4:           Place 2:           Place 5:

┌───┐              ┌───┐              ┌───┐  ┌───┐       ┌───┐  ┌───┐       ┌───┐  ┌───┐  ┌───┐
│ 3 │              │ 1 │              │ 1 │  │ 4 │       │ 1 │  │ 2 │       │ 1 │  │ 2 │  │ 5 │
└───┘              │ 3 │              │ 3 │  └───┘       │ 3 │  │ 4 │       │ 3 │  │ 4 │  └───┘
                   └───┘              └───┘              └───┘  └───┘       └───┘  └───┘

 P1                 P1                 P1     P2           P1     P2           P1     P2     P3

Rule applied:      1 < 3, goes        4 > 1, new         2 < 4, goes        5 > 2, new
3 starts P1.       on top of P1.      pile P2.           on top of P2.      pile P3.
```

```
Final state:    3 piles  →  LIS length = 3

  ┌───┐  ┌───┐  ┌───┐
  │ 1 │  │ 2 │  │ 5 │    ← top cards of each pile
  │ 3 │  │ 4 │  └───┘
  └───┘  └───┘

  P1     P2     P3

An actual LIS of length 3:  1 < 2 < 5   (or  1 < 4 < 5)
```

Notice that the top cards of the piles are always in increasing order from left to right. This is what allows the algorithm to work correctly using a simple "leftmost pile" rule.

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

### Diagram 3 — Tight Example: Why 4 Elements Can Avoid Length-3 Monotone Subsequences

The sequence (2, 4, 1, 3) achieves the bound mn = 2·2 = 4 with no monotone subsequence of length 3. Here is one way to see the structure: arrange the elements in a 2×2 grid where each row is a decreasing run.

```
Sequence:    2    4    1    3
Position:    1    2    3    4

Arrange into a 2×2 grid (rows are maximal decreasing runs read left-to-right):

          Col 1   Col 2
          (small) (large)
Row 1  →    2       4       ← values at positions 1,2   (2 < 4: increasing, not a dec. run)
Row 2  →    1       3       ← values at positions 3,4   (1 < 3: increasing, not a dec. run)

Better grid: rows ordered by value within a decreasing "block".

Read rows right-to-left to get decreasing runs:
  Row 1: 4, 2   (decreasing: 4 > 2)  ← positions 2, 1
  Row 2: 3, 1   (decreasing: 3 > 1)  ← positions 4, 3

Reordered sequence (rows right-to-left): 4, 2, 3, 1

Check (4, 2, 3, 1):
  Increasing subsequences of length 3?
    Need a < b < c with a before b before c.
    Candidates: 2,3 (pos 2,3) then need something > 3 after pos 3 — only 1. Fail.
    2 (pos 2) and 3 (pos 3) then 1 is smaller. No length-3 inc. subseq. ✓
  Decreasing subsequences of length 3?
    4 > 2 (pos 1,2), then need something < 2 after pos 2 — only 3 and 1.
    4 > 2, then 1: is 1 after 2 in the sequence? Sequence is 4,2,3,1. Yes: pos 4. ✓ → 4,2,1 length 3!

That sequence does NOT work. Let us verify the original: (2, 4, 1, 3)

  All increasing subsequences:
    Length 2: (2,4), (2,3), (1,3)      ← many of length 2
    Length 3: need a < b < c, left to right.
      Start with 2 (pos 1): next larger to right: 4 (pos 2) or 3 (pos 4).
        2, 4: next larger after pos 2 = 3 or... nothing larger than 4 remains. Stuck at length 2.
        2, 3 (pos 1, 4): nothing after pos 4. Length 2.
      Start with 1 (pos 3): 3 (pos 4). Length 2.
    → No increasing subsequence of length 3. ✓

  All decreasing subsequences:
    Start with 4 (pos 2): smaller to right: 1 (pos 3) or 3 (pos 4).
      4, 1: nothing smaller after pos 3 ... wait, 3 > 1, so 3 is not smaller. Length 2.
        Actually 4, 1, ? — nothing comes after pos 3 that is < 1. Length 2.
      4, 3: nothing smaller after pos 4. Length 2.
    Start with 2 (pos 1): smaller to right: 1 (pos 3). Then nothing < 1. Length 2.
    → No decreasing subsequence of length 3. ✓

Summary for (2, 4, 1, 3):
┌──────────┬───────┬───────────────────────────────────────────────┐
│ Position │ Value │ Longest monotone subsequences ending here     │
├──────────┼───────┼───────────────────────────────────────────────┤
│    1     │   2   │ Inc: (2) length 1 │ Dec: (2) length 1        │
│    2     │   4   │ Inc: (2,4) len 2  │ Dec: (4) length 1        │
│    3     │   1   │ Inc: (1) length 1 │ Dec: (4,1) or (2,1) len 2│
│    4     │   3   │ Inc: (2,3) len 2  │ Dec: (4,3) len 2         │
└──────────┴───────┴───────────────────────────────────────────────┘

LIS = 2,  LDS = 2.   Neither reaches 3.   Bound mn = 4 is tight. ✓
```

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

### Diagram 4 — The (eᵢ, dᵢ) Label Table in Detail

The table below makes the pair-distinctness argument concrete for (4, 3, 1, 2), and shows why adding any fifth element would force a collision.

```
Sequence: (4, 3, 1, 2)       m = n = 2,  so mn = 4 possible pairs.

 ┌────┬──────┬────────────────────────────┬────┬────────────────────────────┬────┬────────┐
 │  i │  aᵢ  │  Longest inc. subseq.      │ eᵢ │  Longest dec. subseq.      │ dᵢ │  pair  │
 │    │      │  ending at aᵢ              │    │  ending at aᵢ              │    │(eᵢ,dᵢ)│
 ├────┼──────┼────────────────────────────┼────┼────────────────────────────┼────┼────────┤
 │  1 │   4  │  (4)                       │  1 │  (4)                       │  1 │ (1,1)  │
 │  2 │   3  │  (3)       [4 > 3, can't   │  1 │  (4,3)                     │  2 │ (1,2)  │
 │    │      │   extend inc. from 4]      │    │                            │    │        │
 │  3 │   1  │  (1)                       │  1 │  (4,3,1)                   │  3 │ (1,3)  │
 │  4 │   2  │  (1,2)     [1 < 2 ✓]      │  2 │  (4,3,2) or (3,2)         │  2 │ (2,2)  │
 └────┴──────┴────────────────────────────┴────┴────────────────────────────┴────┴────────┘

 All possible pairs from {1,2} × {1,2}:   (1,1)  (1,2)  (2,1)  (2,2)
                                              ↑      ↑             ↑
                                            used   used          used

 Pair (2,1) is NOT used — it would require an element that starts a
 new "longest increasing" chain of length 2 but has no decreasing
 extension yet, which doesn't happen in this particular sequence.

 4 elements → 4 distinct pairs → no collision → Pigeonhole gives no contradiction.

 If we added a 5th element, say 5 (at the end):
   e₅ = 2  (e.g. 1,2,5  → wait, that is length 3 → e₅ = 3!)
   That would immediately give an increasing subseq of length 3 = m+1. ✓

 If we added 0 (at the end):
   e₅ = 1,  d₅ = 4  (4,3,2,0 or 4,3,1,0)  — but d ≤ n = 2 was our assumption,
   which is now violated: decreasing subseq of length 4 ≥ n+1 = 3. ✓

 In every case, a 5th element breaks our assumption — exactly as the theorem predicts.
```

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

### Diagram 5 — 2D Point Scatter Plot

The six points from Puzzle E are plotted on the coordinate grid below. The longest 2D-increasing subsequence is highlighted with arrows connecting the chosen points in sequence order.

Note: "2D-increasing" requires both the x-coordinate AND the y-coordinate to be strictly increasing as we move along the subsequence. We are also picking points in sequence order (left to right by their index in the list).

```
Points in sequence order:
  Index:  1       2       3       4       5       6
  Point: (5,1)  (1,5)  (3,3)  (4,4)  (2,2)  (6,6)

y
│
6 │                                              ● (6,6)
  │
5 │        ● (1,5)
  │
4 │                          ● (4,4)
  │
3 │                   ● (3,3)
  │
2 │                                    ● (2,2)
  │
1 │  ● (5,1)
  │
0 └────┬────┬────┬────┬────┬────┬────── x
       1    2    3    4    5    6

Sequence order indices (1–6) shown beside each point:

  ①(5,1)  ②(1,5)  ③(3,3)  ④(4,4)  ⑤(2,2)  ⑥(6,6)

Finding the longest 2D-increasing subsequence
(must pick points with increasing index AND increasing x AND increasing y):

  Try ②,③,④,⑥:  indices 2<3<4<6 ✓
                  x-coords: 1 < 3 < 4 < 6 ✓
                  y-coords: 5 > 3       ✗   (y goes 5,3,4,6 — not increasing at step 2→3)

  Try ⑤,③,④,⑥:  indices 5>3            ✗   (index must increase)

  Try ③,④,⑥:    indices 3<4<6 ✓
                  x-coords: 3 < 4 < 6 ✓
                  y-coords: 3 < 4 < 6 ✓   Length 3.

  Try ⑤,③,④ — index order 5>3: invalid.

  Re-sort by sequence index:
    ①(5,1), ②(1,5), ③(3,3), ④(4,4), ⑤(2,2), ⑥(6,6)

  Try ②,④,⑥:    indices 2<4<6 ✓
                  x: 1<4<6 ✓,   y: 5>4    ✗

  Try ⑤,④,⑥:    indices 5>4              ✗

  Try ②,⑥:       x: 1<6 ✓, y: 5<6 ✓     Length 2.
  Try ③,④,⑥:     (shown above)           Length 3. ✓
  Try ①,⑥:       x: 5<6 ✓, y: 1<6 ✓     Length 2.
  Try ①,④,⑥:     indices 1<4<6, x:5>4   ✗
  Try ③,⑥:       x:3<6, y:3<6           Length 2.

  Longest found: ③ → ④ → ⑥,  i.e.  (3,3) → (4,4) → (6,6),  length 3.

y
│
6 │                                              ●←─ ⑥(6,6)
  │                                           ╱
5 │        ● (1,5)                          ╱
  │                                       ╱
4 │                          ●←─────────╱  ④(4,4)
  │                        ╱
3 │                   ●←──╱  ③(3,3)
  │
2 │                                    ● (2,2)
  │
1 │  ● (5,1)
  │
0 └────┬────┬────┬────┬────┬────┬────── x
       1    2    3    4    5    6

2D-increasing subsequence: (3,3) → (4,4) → (6,6)   [length 3]
Both x and y coordinates strictly increase along each arrow. ✓
```

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

---

### Diagram 6 — Grid Propagation Sequence

The diagram below shows the 3×3 grid and the propagation order as a sequence of 2D coordinates. The row index is non-decreasing throughout the sequence, and within each row the column index increases.

```
The 3×3 grid (vertices as (row, col) pairs):

  (1,1) ── (1,2) ── (1,3)
    │         │         │
  (2,1) ── (2,2) ── (2,3)
    │         │         │
  (3,1) ── (3,2) ── (3,3)

Initial blue set (top row): { (1,1), (1,2), (1,3) }

Propagation sequence (order in which vertices turn blue):

  Step:    1      2      3      4      5      6      7      8      9
  Vertex: (1,1) (1,2) (1,3) (2,1) (2,2) (2,3) (3,1) (3,2) (3,3)

  Row:     1      1      1      2      2      2      3      3      3
           └──────┴──────┘      └──────┴──────┘      └──────┴──────┘
           non-decreasing ✓     non-decreasing ✓     non-decreasing ✓

  Col:     1      2      3      1      2      3      1      2      3
           └──────┴──────┘      └──────┴──────┘      └──────┴──────┘
           increasing ✓         increasing ✓          increasing ✓

Zooming out — the full row sequence is non-decreasing:

  Row index:   1  1  1  2  2  2  3  3  3
               ↑──↑──↑──↑──↑──↑──↑──↑──↑   each term ≥ previous  ✓

  Col index:   1  2  3  1  2  3  1  2  3
               (resets each time the row increments)

Visualising propagation wave (blue cells marked ■, uncoloured ·):

  After step 3 (top row complete):    After step 6 (middle row complete):

    ■  ■  ■                               ■  ■  ■
    ·  ·  ·                               ■  ■  ■
    ·  ·  ·                               ·  ·  ·

  After step 9 (all complete):

    ■  ■  ■
    ■  ■  ■
    ■  ■  ■

The "wave" sweeps row by row — a 2D monotone pattern.
```

---

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


---

[← Zero Forcing](zero_forcing.md) | [Programme Home](../index.md) | [Next: Centerpoint →](centerpoint.md)