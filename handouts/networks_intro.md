# Handout 1 — Introduction to Graphs and Networks


---
[← Programme Home](../index.md) | [Next: Zero Forcing →](zero_forcing.md) | [🎮 Interactive Game](../interactive/zero_forcing_game.html) | [🐍 Notebook (Colab)](https://colab.research.google.com/github/amessbee/rise/blob/main/notebooks/zero_forcing.ipynb)

---

*Research Lab Internship — Day 1 Afternoon*

---

## The Königsberg Bridge Problem

In 1736, the city of Königsberg (now Kaliningrad, Russia) had seven bridges connecting four land masses across a river. Citizens wondered: is it possible to take a walk through the city, crossing each bridge **exactly once**?

Leonhard Euler answered this question — not just for Königsberg, but for all possible bridge configurations — by inventing what we now call **graph theory**.

**His insight:** Replace each land mass with a dot (vertex) and each bridge with a line (edge). The physical layout no longer matters. Only the *connections* matter.

The diagram below shows the city map alongside Euler's graph abstraction. The four land masses become vertices A, B, C, D, and each bridge becomes an edge. Notice that two bridges connect the island D to each bank, giving **double edges** (shown as ═).

```
  CITY MAP (schematic)               GRAPH ABSTRACTION

       North Bank                         A
      ___________                        / \\
     |           |                      /   \\
     |     A     |─────┐             ══╪═    ╲
     |___________|      \           ╱  C  ╲   ╲
           |  \          \         ╱    |   ╲   ╲
    bridge │   \ bridge   │       ╱     │    ╲   ╲
           │    \         │      B      │     D    A
     _____ ↓_____↓_____   │     (SB)   │    (Is.)
    |                   | │             │   ╱ ╲
    |   D (Kneiphof    |═╪═            │  ╱   ╲
    |     Island)      |═╪═            │═╪═   ═╪═
    |___________________|│            (connections below)
           |    /        │
    bridge │   / bridge  │
     _____ ↓__/___       │
     |          |────────┘
     |    B     |
     |__________|
       South Bank


  Cleaner graph view — vertices and edges:

            A  (North Bank)
           /|
          / |
         /  |                     Key:
        C   |                       ─  or  │  = single edge
       / \  |                       ══      = double edge (two bridges)
      /   \ |                       ×2      = two edges between same pair
     B─────[double edges to D]

  Drawn more precisely:

                  A
                 /║
                / ║  (A═D means two edges: two bridges)
               /  ║
              C   ║
             / \  ║
            /   \ ║
           B─────D
            ╲   ╱
             ╲ ╱  (B═D also means two edges)
              ╲
              (B═D)

  Adjacency list with DOUBLE EDGES shown explicitly:

        A ──── C          (1 bridge)
        A ════ D          (×2 bridges)
        B ──── C          (1 bridge)
        B ════ D          (×2 bridges)
        C ──── D          (1 bridge)

  Degree of each vertex (= number of bridges touching it):

        d(A) = 1 + 2     = 3   (odd)
        d(B) = 1 + 2     = 3   (odd)
        d(C) = 1 + 1 + 1 = 3   (odd)
        d(D) = 2 + 2 + 1 = 5   (odd)

        All four vertices have ODD degree.
        Sum of degrees = 3+3+3+5 = 14 = 2 × 7 edges.  ✓ (Handshaking Lemma)
```

*(The actual bridge map as drawn on the board will look more geographical — the diagram above captures only the connectivity.)*

Such a walk (visiting every edge exactly once) is now called an **Eulerian path**. Euler proved:

> **Euler's Theorem:** An Eulerian path exists if and only if the graph has exactly zero or two vertices with an odd number of edges.

In Königsberg, **all four** vertices had odd degree. So no such walk exists.

---

## Formal Definitions

**Graph:** A graph G = (V, E) consists of:
- A set V of **vertices** (also called nodes or points).
- A set E of **edges** (also called links), where each edge connects two vertices.

**Example:** V = {Alice, Bob, Carol}, E = {(Alice, Bob), (Bob, Carol)}.

```
Alice ─── Bob ─── Carol
```

**Degree of a vertex:** The number of edges touching that vertex. Written d(v).
- In the example: d(Alice) = 1, d(Bob) = 2, d(Carol) = 1.

**Key fact (Handshaking Lemma):** The sum of all degrees equals twice the number of edges:

$$\sum_{v \in V} d(v) = 2|E|$$

*Why? Every edge contributes exactly 1 to the degree of each of its two endpoints.*

**Consequence:** The number of vertices with odd degree is always even.

---

### Degree Sequence Example

The **degree sequence** of a graph is the list of all vertex degrees written in non-decreasing (or non-increasing) order. It gives a quick fingerprint of a graph's structure.

```
  Example graph on 5 vertices:

          1
         / \
        /   \
       2─────3
       |     |
       4─────5

  Edges: (1,2), (1,3), (2,3), (2,4), (3,5), (4,5)

  Vertex degrees:
    d(1) = 2   (connects to 2, 3)
    d(2) = 3   (connects to 1, 3, 4)
    d(3) = 3   (connects to 1, 2, 5)
    d(4) = 2   (connects to 2, 5)
    d(5) = 2   (connects to 3, 4)

  Degree sequence (sorted): 2, 2, 2, 3, 3

  Check — Handshaking Lemma:
    sum of degrees = 2+3+3+2+2 = 12 = 2 × 6 edges  ✓
```

---

**Path:** A sequence of distinct vertices v₁, v₂, ..., vₖ where each consecutive pair (vᵢ, vᵢ₊₁) is connected by an edge.

**Connected graph:** A graph where there is a path between every pair of vertices.

**Cycle:** A path where the first and last vertex are the same (and no vertex is repeated otherwise).

**Tree:** A connected graph with no cycles. A tree on n vertices has exactly n-1 edges.

---

## Special Families of Graphs

Here are the key named families you will meet repeatedly. Each is drawn below.

```
  ── P₅ (Path on 5 vertices, 4 edges) ──────────────────────────

     1 ─── 2 ─── 3 ─── 4 ─── 5

     Every internal vertex has degree 2; the two ends have degree 1.


  ── C₅ (Cycle on 5 vertices, 5 edges) ─────────────────────────

           1
          / \
         5   2
         |   |
         4───3

     Every vertex has degree 2.  (A "pentagon".)


  ── K₄ (Complete graph on 4 vertices, 6 edges) ─────────────────

     Every pair of vertices is joined by an edge.

             1
            /|\
           / | \
          /  |  \
         2───┼───3
          \  |  /
           \ | /
            \|/
             4

     Edges: (1,2),(1,3),(1,4),(2,3),(2,4),(3,4)
     Every vertex has degree 3.
     Total edges = 4×3/2 = 6  ✓


  ── K₁,₄ (Star with 4 leaves) ──────────────────────────────────

     One central hub connected to every leaf; leaves not connected
     to each other.

              ○  (leaf)
              |
     ○ ─────●───── ○
    (leaf)   │    (leaf)
             │
             ○  (leaf)

     Hub (●) has degree 4; each leaf has degree 1.
     Total edges = 4.
```

| Name | Notation | Description | # Edges |
|------|----------|-------------|---------|
| Path | Pₙ | n vertices in a line | n-1 |
| Cycle | Cₙ | n vertices in a ring | n |
| Complete graph | Kₙ | every pair connected | n(n-1)/2 |
| Star | K₁,ₙ | one hub, n leaves | n |
| Complete bipartite | Kₘ,ₙ | two groups, every cross-edge present | mn |
| Grid | Pₘ × Pₙ | m×n rectangular grid | 2mn-m-n |

---

### Bipartite Graphs

A graph is **bipartite** if its vertices can be split into two groups (call them "red" and "blue") so that every edge goes between the two groups — no edge stays within one group.

The complete bipartite graph **K₂,₃** has 2 vertices on one side and 3 on the other, with all 2×3 = 6 edges present.

```
  K₂,₃  —  Complete bipartite graph (2 top, 3 bottom)
  ────────────────────────────────────────────────────

      Top row  (group X):       A       B

                               /|\     /|\
                              / | \   / | \
                             /  |  \ /  |  \
                            /   |   X   |   \
                           /    |  / \  |    \
                          /     | /   \ |     \
                         /      |/     \|      \

      Bottom row (group Y):   P       Q       R

  All 6 cross-edges shown:
    A─P,  A─Q,  A─R
    B─P,  B─Q,  B─R

  Redrawn with explicit lines:

         A ─────────── B
        /|\           /|\
       / | \         / | \
      /  |  \       /  |  \
     P   Q   R─────B's edges...

  Cleaner layout:

         A           B
         │╲         ╱│
         │  ╲     ╱  │
         │    ╲ ╱    │
         │    ╱ ╲    │
         │  ╱     ╲  │
         │╱         ╲│
         P─────Q─────R
              (no edges within bottom row)

  Explicitly:
         A ─── P
         A ─── Q
         A ─── R
         B ─── P
         B ─── Q
         B ─── R

  d(A)=3, d(B)=3, d(P)=2, d(Q)=2, d(R)=2
  Sum of degrees = 3+3+2+2+2 = 12 = 2×6 edges  ✓
```

---

## Trees

**Tree:** A connected graph with no cycles. A tree on n vertices has exactly n−1 edges.

Trees arise everywhere — family trees, file-system directories, parse trees in compilers, evolutionary phylogenies.

```
  THREE TREE EXAMPLES
  ═══════════════════

  (i) PATH TREE — P₅
  ───────────────────

     ○ ─── ○ ─── ○ ─── ○ ─── ○

     5 vertices, 4 edges, 2 leaves (the two ends).
     This is both a path and a tree.


  (ii) STAR TREE — K₁,₄
  ──────────────────────

              ○
              │
     ○ ──── ● ──── ○
              │
              ○

     5 vertices, 4 edges, 4 leaves (all non-hub vertices).
     Hub (●) has degree 4.


  (iii) CATERPILLAR TREE
  ──────────────────────

     A "spine" (path) with extra leaves hanging off it.

     ○   ○       ○
      \  │       │
       ○─○───○───○
              │
              ○

     9 vertices, 8 edges.
     Remove all leaves → what remains is a path (the "spine").

     Labelled version:

          L1  L2       L5
           \  │         │
        L0──A──B───C───D
                │
               L3

     Spine: A─B─C─D
     Leaves: L0, L1 (on A),  L2, L3 (on B),  L5 (on D)
     d(A)=4, d(B)=4, d(C)=2, d(D)=2, all leaves have degree 1.
```

---

## Euler's Formula for Planar Graphs

A graph is **planar** if it can be drawn in the plane with no edges crossing. When you draw a planar graph, it divides the plane into regions called **faces** (including the unbounded outer region).

**Euler's Formula:**  For any connected planar graph,

$$V - E + F = 2$$

where V = number of vertices, E = number of edges, F = number of faces (including the outer face).

```
  EXAMPLE: K₄ drawn as a planar graph
  ─────────────────────────────────────

  Draw a triangle (vertices 1, 2, 3) with vertex 4 placed inside,
  connected to all three corners.

           1
          /|\
         / | \
        /  |  \
       /   4   \        4 is inside the triangle
      /  ╱   ╲  \
     / ╱       ╲ \
    2 ─────────── 3

  Edges:
    Outer triangle:  (1,2), (2,3), (1,3)
    Spokes to 4:     (1,4), (2,4), (3,4)

  Count:
    V = 4   (vertices: 1, 2, 3, 4)
    E = 6   (edges listed above)
    F = ?

  Faces (regions):
    f1 = triangle (1, 4, 2)   — lower-left inner region
    f2 = triangle (2, 4, 3)   — lower-right inner region
    f3 = triangle (1, 3, 4)   — upper inner region
    f4 = outer face (unbounded region outside triangle 1─2─3)

    F = 4

  Check Euler's formula:
    V − E + F  =  4 − 6 + 4  =  2  ✓

  Alternate check using a simpler graph (square + diagonal):

           1 ─── 2
           │ ╲   │
           │   ╲ │
           4 ─── 3

    V=4, E=5 (four sides + one diagonal 1─3), F=3
    (two inner triangles + outer face)
    V − E + F = 4 − 5 + 3 = 2  ✓
```

---

## Non-Planar Graphs: K₃,₃ and the Utilities Puzzle

Not every graph can be drawn without crossings. Two famous non-planar graphs are K₅ (complete graph on 5 vertices) and **K₃,₃** (complete bipartite graph on 3+3 vertices).

**The Utilities Puzzle:** Three houses (H1, H2, H3) each need to be connected to three utilities (Gas G, Water W, Electricity E) — 9 connections in total. Can you draw all 9 connection lines without any of them crossing?

The answer is **no** — K₃,₃ is non-planar. Here is an attempt that forces a crossing:

```
  UTILITIES PUZZLE — K₃,₃ attempt (one crossing is unavoidable)
  ═══════════════════════════════════════════════════════════════

  Houses:    H1       H2       H3
  Utilities: G        W        E

  Best attempt at a planar drawing — but one edge must cross:

        H1 ──────── H2 ──────── H3
        │ ╲         │         ╱ │
        │   ╲       │       ╱   │
        │     ╲     │     ╱     │
        │       ╲   │   ╱       │
        │         ╲ │ ╱         │
        │           ✗  ← CROSSING (unavoidable!)
        │         ╱ │ ╲         │
        │       ╱   │   ╲       │
        G ──────── W  ──────── E

  No matter how you reroute the edges, at least one pair must cross.

  Why? Euler's formula gives a constraint: for a planar graph,
       E ≤ 3V − 6  (when every face has at least 3 edges).
  For K₃,₃: V=6, E=9.
  Bipartite graphs have no triangles, so every face has ≥ 4 edges,
  giving the tighter bound E ≤ 2V − 4 = 8.
  But K₃,₃ has E=9 > 8.  Contradiction — K₃,₃ is NOT planar.

  (This is half of Kuratowski's theorem: every non-planar graph
   contains K₅ or K₃,₃ as a "subdivision".)
```

---

## Real-World Networks

These mathematical definitions abstract an enormous variety of real phenomena:

**Social networks:** Vertices = people; edges = friendships or follows. Understanding how information (or misinformation) spreads in these graphs is an active research area.

**Communication networks:** Vertices = computers or routers; edges = cables or wireless links. Robustness to failures is critical — removing which edges would disconnect the network?

**Biological networks:** Vertices = proteins; edges = biochemical interactions. Identifying "hub" proteins (high degree) may reveal drug targets.

**Transport networks:** Vertices = cities; edges = roads, flights, or rail lines. Optimising routes (the Travelling Salesman Problem) is computationally hard.

**Key insight:** The *same* mathematical tools apply to all of these, even though the underlying systems are completely different.

---

## Puzzles and Problems

**Puzzle 1 (easy):**  
Draw a graph with 6 vertices where every vertex has degree exactly 2. How many such non-isomorphic graphs are there?

**Puzzle 2 (medium):**  
A town has 8 people. Is it possible for every person to be friends with exactly 3 others? If yes, draw an example. If no, explain why not.

**Puzzle 3 (medium):**  
Prove that every tree on n ≥ 2 vertices has at least two vertices of degree 1 (called **leaves**). *(Hint: consider the longest path in the tree.)*

**Puzzle 4 (hard):**  
A graph is called **bipartite** if its vertices can be coloured with two colours (say, red and blue) such that every edge connects a red vertex to a blue vertex. Prove that a graph is bipartite if and only if it contains no cycle of odd length.

**Open Problem (describe, don't solve):**  
The **graph isomorphism problem** asks: given two graphs G and H, are they the "same" up to relabelling of vertices? No efficient (polynomial-time) algorithm is known. It is one of the few natural computational problems not known to be either easy (P) or hard (NP-complete).

---

## Homework

**H1.** Draw all non-isomorphic graphs on 4 vertices. (Two graphs are isomorphic if one can be obtained from the other by relabelling vertices.) How many are there?

**H2.** Prove the Handshaking Lemma: for any graph, $\sum_{v} d(v) = 2|E|$.

**H3.** A graph has n vertices and every vertex has degree at least n/2. Prove that the graph is connected. *(Hint: suppose two vertices u and v are not connected. Count how many vertices each can be adjacent to.)*

**H4 (Challenge).** In a social network of 20 people, is it possible that everyone has a different number of friends? Explain your answer.


---

[← Programme Home](../index.md) | [Next: Zero Forcing →](zero_forcing.md)