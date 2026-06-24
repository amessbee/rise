# Handout 1 — Introduction to Graphs and Networks

*Research Lab Internship — Day 1 Afternoon*

---

## The Königsberg Bridge Problem

In 1736, the city of Königsberg (now Kaliningrad, Russia) had seven bridges connecting four land masses across a river. Citizens wondered: is it possible to take a walk through the city, crossing each bridge **exactly once**?

```
         [Island A]
        /           \
[Left] — — — [Island B] — — — [Right]
        \           /
         [Island A]
```

*(Sketch the actual bridge map here as drawn on the board.)*

Leonhard Euler answered this question — not just for Königsberg, but for all possible bridge configurations — by inventing what we now call **graph theory**.

**His insight:** Replace each land mass with a dot (vertex) and each bridge with a line (edge). The physical layout no longer matters. Only the *connections* matter.

Such a walk (visiting every edge exactly once) is now called an **Eulerian path**. Euler proved:

> **Euler's Theorem:** An Eulerian path exists if and only if the graph has exactly zero or two vertices with an odd number of edges.

In Königsberg, all four vertices had odd degree. So no such walk exists.

---

## Formal Definitions

**Graph:** A graph G = (V, E) consists of:
- A set V of **vertices** (also called nodes or points).
- A set E of **edges** (also called links), where each edge connects two vertices.

**Example:** V = {Alice, Bob, Carol}, E = {(Alice, Bob), (Bob, Carol)}.

```
Alice — Bob — Carol
```

**Degree of a vertex:** The number of edges touching that vertex. Written d(v).
- In the example: d(Alice) = 1, d(Bob) = 2, d(Carol) = 1.

**Key fact (Handshaking Lemma):** The sum of all degrees equals twice the number of edges:

$$\sum_{v \in V} d(v) = 2|E|$$

*Why? Every edge contributes exactly 1 to the degree of each of its two endpoints.*

**Consequence:** The number of vertices with odd degree is always even.

---

**Path:** A sequence of distinct vertices v₁, v₂, ..., vₖ where each consecutive pair (vᵢ, vᵢ₊₁) is connected by an edge.

**Connected graph:** A graph where there is a path between every pair of vertices.

**Cycle:** A path where the first and last vertex are the same (and no vertex is repeated otherwise).

**Tree:** A connected graph with no cycles. A tree on n vertices has exactly n-1 edges.

```
Trees on 5 vertices (some examples):

Path:  ○—○—○—○—○

Star:      ○
          /|\
         ○ ○ ○
           |
           ○

"Caterpillar":  ○—○—○—○
                   |
                   ○
```

---

## Special Families of Graphs

| Name | Notation | Description | # Edges |
|------|----------|-------------|---------|
| Path | Pₙ | n vertices in a line | n-1 |
| Cycle | Cₙ | n vertices in a ring | n |
| Complete graph | Kₙ | every pair connected | n(n-1)/2 |
| Star | K₁,ₙ | one hub, n leaves | n |
| Complete bipartite | Kₘ,ₙ | two groups, every cross-edge present | mn |
| Grid | Pₘ × Pₙ | m×n rectangular grid | 2mn-m-n |

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
