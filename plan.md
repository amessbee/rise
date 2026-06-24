# Research Lab Internship — Three-Week Program
## Coordinator's Detailed Guide

**Duration:** 3 weeks × 4 days × 4 hours = 48 hours of contact time  
**Schedule:** Monday–Thursday, 9:00–13:00 (with a 15-min break around 10:45)  
**Audience:** 3–4 A-level students (ages 16–18)  
**Fridays:** Free / independent reading / optional office hours

---

## Program Architecture

The program has three tracks that build progressively:

| Week | Theme | Core Content |
|------|-------|--------------|
| **1** | Graphs and Networks | Graph theory fundamentals, special families, properties, puzzles |
| **2** | Controlling Networks | Controllability motivation, zero forcing sets, the game, propagation sequences |
| **3** | Sequences and Geometry | Erdős–Szekeres, PMI sequences, centerpoint theorem |

**Each week ends on Thursday with a problem session and mini-presentations** — students present one result or worked example from the week. These are informal (whiteboard only, 5–8 minutes each) and not assessed.

---

## Daily Block Structure

Every session follows the same rhythm:

| Time | Block | Purpose |
|------|-------|---------|
| 0:00–0:30 | **Warm-up** | Puzzle, recap of previous session, or short exploration |
| 0:30–1:45 | **Main session** | New content: definitions, examples, proofs, discussion |
| 1:45–2:00 | **Break** | |
| 2:00–3:00 | **Problem session** | Students work problems individually or in pairs; coordinator circulates |
| 3:00–4:00 | **Discussion and preview** | Share solutions, discuss wrong turns, preview next session, assign homework |

On **Day 4 of each week** (Thursday), the structure changes: the morning is a full open problem/exploration session, and the afternoon is mini-presentations.

---

## Week 1 — Graphs and Networks

### Week 1 Goals
- Understand the formal definition of a graph and be comfortable with basic vocabulary.
- Recognise graphs in real-world contexts.
- Know the key families: paths, cycles, complete graphs, trees, bipartite graphs.
- Be able to prove simple graph properties using the Handshaking Lemma and basic arguments.
- Have encountered Euler's theorem and a few coloring/planarity ideas.

---

### Day 1 (Week 1, Monday) — Welcome, Survey, and the World of Networks

**Theme:** Why do we study graphs? What is a graph?

---

**0:00–0:30 — Welcome and Ice-Breakers**

Activity — *Two Truths and a Maths Lie:*  
Each student states three things about themselves — two true and one plausible but false mathematical claim. The group guesses the lie. Encourage mathematical lies that sound reasonable (e.g., "the sum of interior angles of any polygon is 360°").

Warm-up Puzzle on the whiteboard:

> *Nine dots arranged in a 3×3 grid. Connect all nine using four straight lines without lifting your pen.*

Let them struggle for 5 minutes. Reveal that the lines may extend outside the grid boundary. Moral: **unexamined assumptions are the biggest obstacle in research.**

---

**0:30–1:00 — Motivational Talk**

Key messages:
1. Research means asking questions that nobody — not even the professor — can currently answer.
2. The problems this week look playful. But the same mathematics underlies robot swarms, social media dynamics, cancer research, and internet security.
3. The goal this week is to build intuition slowly and carefully, not to rush to results.

Show or sketch three images:
- A social network graph (e.g., six people, friendships drawn as lines)
- A map of airline routes between cities
- A biological neural network (neurons and synapses)

*Ask:* What do these three pictures have in common? Take several answers. The answer: they are all **graphs** — collections of things (vertices) and connections (edges).

---

**1:00–1:45 — The Königsberg Bridge Problem**

Tell the story of Königsberg (1736): four land masses, seven bridges, the residents' puzzle.

Draw the map on the board, then redraw it as a graph (land masses → vertices, bridges → edges). Emphasise: **the graph captures only the structure that matters for the question**. Distance, shape, and colour of bridges are irrelevant.

State and explore Euler's theorem:

> A connected graph has an **Eulerian path** (traverse every edge exactly once) if and only if it has exactly 0 or 2 vertices of odd degree.
>
> It has an **Eulerian circuit** (start and end at same vertex) if and only if every vertex has even degree.

Verify for Königsberg: all four vertices have odd degree → no Eulerian path.

*Discussion:* Can you modify the Königsberg map (add or remove exactly one bridge) to make an Eulerian path possible? There are several ways; find them.

---

**1:45–2:00 — Break**  
Distribute **Handout: survey.md** during break so students can fill it in during the problem session.

---

**2:00–3:00 — Survey + First Problem Session**

*First 20 minutes:* Students complete the background survey. Coordinator circulates and chats informally.

*Remaining 40 minutes:* First problem set. Students work in pairs.

**Problem Set 1A:**

1. Draw all non-isomorphic graphs on 4 vertices. (Two graphs are isomorphic if one can be relabelled to match the other.) How many are there?

2. A party has 10 people. Each person shakes hands with some others. Prove that at least two people shook the same number of hands.  
   *(Hint: what are the possible numbers of handshakes? Can someone shake 0 hands and someone else shake 9 hands simultaneously?)*

3. Draw a graph with 6 vertices where every vertex has degree exactly 2. How many non-isomorphic such graphs exist?

4. Can you draw a graph with 5 vertices where the degree sequence (list of degrees) is (1, 2, 3, 4, 4)? If not, why not?

---

**3:00–4:00 — Discussion, Definitions, Preview**

Go over solutions together. Introduce formal definitions while discussing the solutions:

- **Graph G = (V, E)**: V = vertices, E = edges (unordered pairs of vertices)
- **Degree d(v)**: number of edges touching v
- **Handshaking Lemma**: Σ d(v) = 2|E| (consequence: number of odd-degree vertices is even)
- **Path, cycle, connected graph** (informal descriptions — formal definitions tomorrow)

Preview Day 2: "Tomorrow we'll formalise these definitions and explore special families of graphs."

**Homework:** Problems H1 and H2 from Handout networks_intro.md.

---

### Day 2 (Week 1, Tuesday) — Formal Definitions and Special Graphs

**Theme:** Building the vocabulary of graph theory.

---

**0:00–0:30 — Warm-up: Puzzle of the Day**

> A graph has n vertices and every pair of vertices is connected by an edge. This is called the *complete graph* Kₙ. How many edges does Kₙ have?

Give 5 minutes. Then: K₁ has 0 edges, K₂ has 1, K₃ has 3, K₄ has 6. Pattern? Answer: n(n-1)/2.

Review homework from Day 1. Ask two students to present their solutions to H1 (non-isomorphic graphs on 4 vertices) and H2 (Handshaking Lemma proof).

---

**0:30–1:45 — Main Session: Graph Vocabulary and Special Families**

Distribute **Handout: networks_intro.md**.

**Formal definitions (25 min):**

- **Walk, path, cycle**: careful distinction (a walk may revisit vertices; a path may not)
- **Connected**: there is a path between every pair of vertices
- **Component**: a maximal connected subgraph
- **Distance d(u,v)**: length of the shortest path between u and v
- **Diameter**: maximum distance over all pairs of vertices
- **Subgraph**: a graph formed by a subset of V and E

**Special families (30 min):**

| Graph | Notation | Key properties |
|-------|----------|----------------|
| Path | Pₙ | n vertices, n-1 edges, two leaves |
| Cycle | Cₙ | n vertices, n edges, every vertex degree 2 |
| Complete graph | Kₙ | every pair connected, n(n-1)/2 edges |
| Star | K₁,ₙ | one hub (degree n), n leaves (degree 1) |
| Complete bipartite | Kₘ,ₙ | two groups, all cross-edges |
| Grid | Pₘ × Pₙ | m×n lattice |

**Bipartite graphs (20 min):**

A graph is **bipartite** if vertices can be 2-coloured (red/blue) so every edge connects red to blue.

Examples: paths, even cycles, trees. Non-examples: odd cycles, K₃.

Theorem (state without proof): A graph is bipartite if and only if it contains no odd-length cycle.

*Activity:* Draw several graphs. Students identify which are bipartite and find a 2-colouring if so.

---

**1:45–2:00 — Break**

---

**2:00–3:00 — Problem Session**

**Problem Set 1B:**

1. Prove that a connected graph on n vertices has at least n-1 edges. When does equality hold?

2. A **complete bipartite graph** K₃,₃ has two groups of 3 vertices each, with every vertex in group 1 connected to every vertex in group 2. How many edges does it have? Draw it. Is it planar (can you draw it without edges crossing)? *(This is the famous "houses and utilities" puzzle.)*

3. Show that in any graph, the sum of all vertex degrees equals twice the number of edges. Use this to prove: the number of vertices with odd degree is always even.

4. A graph is called **regular** if every vertex has the same degree. Draw all non-isomorphic 3-regular (cubic) graphs on 6 vertices.

5. *(Challenge)* A graph on n vertices has more than n²/4 edges. Prove it must contain a triangle (K₃ as a subgraph). This is Turán's theorem for r=3 — try to find the argument.

---

**3:00–4:00 — Trees: Discussion and Introduction**

Go over Problem 1 — this naturally introduces **trees**:

**Definition:** A **tree** is a connected graph with no cycles. A **forest** is a graph with no cycles (connected or not).

Key facts (prove or sketch proofs as appropriate):
- A tree on n vertices has exactly n-1 edges.
- Between any two vertices in a tree there is exactly one path.
- Every tree with n ≥ 2 vertices has at least 2 leaves (degree-1 vertices).

*Proof of the third fact:* Take the longest path in the tree. Both endpoints must have degree 1 — otherwise there would be a longer path or a cycle. □

**Preview:** Trees turn out to be the "simplest" graphs and will reappear when we study zero forcing.

**Homework:** Problems H3 and H4 from networks_intro.md.

---

### Day 3 (Week 1, Wednesday) — Graph Properties and Colouring

**Theme:** Deeper properties — chromatic number, planarity, and graph invariants.

---

**0:00–0:30 — Warm-up: Map Colouring Puzzle**

Show a map with 8 regions. Challenge: colour the map so no two adjacent regions share the same colour. What is the minimum number of colours needed?

This naturally motivates **graph colouring**: create a graph where regions are vertices and adjacency between regions becomes edges. Colouring the map = colouring the graph.

---

**0:30–1:45 — Main Session: Graph Colouring and Planarity**

**Graph colouring (40 min):**

**Chromatic number χ(G):** The minimum number of colours needed to colour the vertices of G so no two adjacent vertices share the same colour.

Examples:
- Path Pₙ: χ = 2 (alternating colours)
- Odd cycle C₅: χ = 3
- Complete graph Kₙ: χ = n
- Bipartite graph: χ = 2 (that's the definition!)

**Greedy colouring:** Assign each vertex the smallest colour not used by any already-coloured neighbour. This gives at most Δ(G) + 1 colours, where Δ(G) is the maximum degree.

**Theorem (Brook's, 1941, state only):** For any connected graph G that is not a complete graph or an odd cycle: χ(G) ≤ Δ(G).

**The Four Colour Theorem (state and discuss):** Every planar graph (one that can be drawn without edge crossings) can be 4-coloured. Proved by Appel and Haken in 1976 — the first major theorem proved with substantial computer assistance. This was controversial at the time. Discuss: what counts as a mathematical proof?

**Planarity (35 min):**

A graph is **planar** if it can be drawn in the plane without edges crossing.

**Euler's formula for planar graphs:** For any connected planar graph drawn without crossings:
$$V - E + F = 2$$
where V = vertices, E = edges, F = faces (regions, including the outer unbounded region).

Verify with examples: triangle (V=3, E=3, F=2 → 3-3+2=2 ✓), cube graph (V=8, E=12, F=6 → 8-12+6=2 ✓).

**Consequence (edge bound):** For any simple planar graph with V ≥ 3: E ≤ 3V - 6.

*Proof:* Each face is bounded by at least 3 edges, each edge borders at most 2 faces, so 3F ≤ 2E. Substitute into Euler's formula. □

**Corollary:** K₅ and K₃,₃ are non-planar (check: K₅ has V=5, E=10 > 3·5-6=9; K₃,₃ has V=6, E=9 > 2·6-4=8 using the bipartite version of the bound).

---

**1:45–2:00 — Break**

---

**2:00–3:00 — Problem Session**

**Problem Set 1C:**

1. Compute χ(G) for: (a) the Petersen graph, (b) the 3×3 grid, (c) the "wheel graph" W₅ (a 5-cycle with one central hub connected to all 5 cycle vertices).

2. Prove: χ(G) ≥ ω(G), where ω(G) is the **clique number** — the size of the largest complete subgraph. *(A clique is a set of pairwise-connected vertices.)*

3. A graph G has 10 vertices and 40 edges. Prove G is non-planar.

4. Use Euler's formula to prove that K₃,₃ is non-planar. *(Hint: in a bipartite graph, every face is bounded by at least 4 edges, since there are no triangles.)*

5. *(Challenge)* The **chromatic polynomial** P(G, k) counts the number of proper k-colourings of G. For a tree Tₙ on n vertices, show P(Tₙ, k) = k(k-1)ⁿ⁻¹. *(Hint: root the tree and colour greedily from the root down.)*

---

**3:00–4:00 — Algorithms on Graphs + Preview of Week 2**

Brief introduction to two famous algorithms (describe informally, no code required):

**Breadth-First Search (BFS):** Start at a vertex. Explore all neighbours, then neighbours-of-neighbours, etc. Gives shortest paths. Think of it as "rings spreading outward."

**Depth-First Search (DFS):** Explore as far as possible down one branch before backtracking. Think of it as "always take the first new turn you see."

*Application:* BFS gives the distance (shortest path length) between any two vertices. The diameter of the graph is the maximum BFS distance over all starting vertices.

**Preview of Week 2:** Next week we ask: if you want to *control* a network — steer its behaviour to a target state — which vertices do you need direct access to, and how few can you get away with? This will lead us to the zero forcing game.

**Homework:** H3 and H4 from networks_intro.md, plus:  
*Bonus:* Find a planar graph where χ(G) = 4 and ω(G) = 3 (a graph needing 4 colours but containing no K₄). *(Hint: Grötzsch graph, or any odd-wheel.)*

---

### Day 4 (Week 1, Thursday) — Problem Session and Mini-Presentations

**Theme:** Consolidate Week 1; students present.

---

**0:00–1:45 — Open Problem Exploration**

Students choose one of the following investigation threads:

**Thread A — Graph Isomorphism:**  
Two graphs are isomorphic if one can be relabelled to match the other. How do you tell quickly if two graphs are not isomorphic? (Compare degree sequences, number of triangles, diameter, etc.) How do you tell they *are* isomorphic? This is a famously hard problem — no efficient general algorithm is known.
- Task: Find two non-isomorphic graphs with the same degree sequence. Try to find graphs that are hard to distinguish.

**Thread B — Ramsey Theory:**  
Suppose you have 6 people. Must there be either 3 mutual friends or 3 mutual strangers? (This is R(3,3)=6, the smallest Ramsey number.) Try to prove it. Then ask: what about 4 mutual friends or 4 mutual strangers? R(4,4) = 18 — it is known, but much harder. R(5,5) is unknown.
- Task: Prove R(3,3) ≤ 6 and demonstrate that 5 people are not enough.

**Thread C — Degree Sequences:**  
The **Erdős–Gallai theorem** says exactly which lists of non-negative integers can be the degree sequence of a simple graph. Try to discover the condition yourself by exploring small cases. When can (4,3,3,2,2) be a degree sequence? What about (4,4,3,3,2)?

---

**1:45–2:00 — Break**

---

**2:00–4:00 — Mini-Presentations**

Each student presents one result, puzzle, or worked problem from Week 1 (5–8 minutes, whiteboard only). Possible topics:

- Proof of the Handshaking Lemma
- Why K₃,₃ is non-planar
- A construction showing R(3,3) ≤ 6
- The chromatic polynomial of a path

Coordinator and other students ask at least one question per presentation. Emphasis on clarity and correctness, not polish.

**End of Week 1 discussion:** What surprised you? What is still unclear? Write one remaining question on a sticky note — these go on the board and are answered during Week 2 warm-ups.

---

## Week 2 — Controlling Networks: Zero Forcing

### Week 2 Goals
- Understand what network controllability means, physically and mathematically.
- Define zero forcing sets and the zero forcing number Z(G).
- Compute Z(G) for paths, cycles, complete graphs, stars, trees, and small grids.
- Understand the two-player zero forcing game and think about strategy.
- Understand propagation sequences and their structure.
- See the connection between Z(G) and linear-algebraic controllability.

---

### Day 5 (Week 2, Monday) — Controllability Motivation

**Theme:** What does it mean to control a network?

---

**0:00–0:30 — Warm-up: Answer the Sticky-Note Questions**

Address the open questions from Week 1 (collected on sticky notes on Day 4). Answer two or three; defer harder ones to the end of the week.

**Puzzle of the Day:**
> Ten dominoes are standing in a line, each balanced on its end. They are spaced so that each falling domino will knock over the next one. You push the first domino. What happens? Now suppose you have a 10×10 grid of dominoes. If you push one, can it start a chain reaction that topples all 100? Where would you push to topple as many as possible with a single push?

This is the zero forcing intuition. Discuss informally.

---

**0:30–1:45 — Main Session: Three Motivating Examples**

**Example 1 — Influencing a Social Network (30 min)**

Consider a simplified social network of 12 users as a graph. Each user holds a binary opinion (0 or 1). The influence rule: a user flips their opinion to match the majority of their neighbours if that majority is strong enough.

A political campaign can "buy" 3 accounts to hold a fixed opinion (1). The goal: through social dynamics, eventually all users adopt opinion 1.

*Question:* Which 3 accounts gives maximum eventual influence?

Draw a sample graph on the board. Let students propose which 3 vertices to colour. Simulate the dynamics. Notice that a badly chosen set of 3 gets "stuck" — the dynamics stall before everyone is converted. A well-chosen set propagates to everyone.

*Key insight:* The structure of the graph determines which sets work. This is a controllability question.

**Example 2 — Swarm of Robots (20 min)**

You have n drones in the air. Each drone adjusts its velocity to match the average velocity of its neighbours in the communication graph. You have direct radio control over only k drones.

*Question:* What is the minimum k such that you can steer the entire swarm to any target formation?

This is a linear dynamical system. The answer depends on Z(G), the zero forcing number — which we will define today.

**Example 3 — The Mexican Wave (15 min)**

In a football stadium, each person stands if both their immediate left and right neighbours are already standing. A coordinator seeds the wave by getting a group to stand simultaneously.

Draw the stadium as a cycle graph (seats in a ring). If the seeded group is S, simulate the wave.

*Question:* What is the minimum |S| so the wave goes all the way around? *(Answer: 2 adjacent people. We will see this is Z(Cₙ) = 2.)*

---

**1:45–2:00 — Break**

---

**2:00–3:00 — Defining Zero Forcing**

Distribute **Handout: zero_forcing.md**.

**The Colour Change Rule:**  
A **blue** vertex with exactly **one white** neighbour forces that neighbour to become blue.

Walk through examples: P₅ (starting from one endpoint), C₄, K₄, K₁,₃. Students follow along and predict the next step before the coordinator reveals it.

**Definitions:**
- **Zero forcing set S:** Starting with S blue, repeated application of the colour change rule eventually colours all vertices blue.
- **Zero forcing number Z(G):** Minimum |S| over all zero forcing sets S.

---

**3:00–4:00 — First Computations and Discussion**

Students work in pairs:

1. Find Z(P₆), Z(C₆), Z(K₄), Z(K₁,₄), Z(K₂,₃).
2. Prove Z(Pₙ) = 1 for all n ≥ 1.
3. Prove Z(Cₙ) = 2 for all n ≥ 3.

Discuss solutions. Introduce the key question: **how does the structure of G determine Z(G)?**

**Homework:** H5 from zero_forcing.md (grid conjecture).

---

### Day 6 (Week 2, Tuesday) — Computing Z(G): Examples and Bounds

**Theme:** How do we prove lower bounds on Z(G)?

---

**0:00–0:30 — Warm-up: Grid Exploration**

Students bring their Z(grid) computations from homework. Pool results:

| Grid | Z |
|------|---|
| 2×2 | 2 |
| 2×3 | 2 |
| 3×3 | 3 |
| 2×4 | 2 |
| 3×4 | 3 |
| 4×4 | 4 |

Conjecture together: **Z(Pₘ × Pₙ) = min(m, n).**

---

**0:30–1:45 — Main Session: Lower Bounds**

**Why lower bounds are hard (10 min):**  
To show Z(G) ≤ k, we exhibit a zero forcing set of size k. To show Z(G) ≥ k, we must argue that *every* set of size k-1 fails to zero force G. This requires ruling out all possible sets.

**Lower bound technique 1 — The Degree Argument (25 min):**

If every vertex in G has degree ≥ 3, then after forcing begins, a blue vertex with one white neighbour means all its other d(v)-1 ≥ 2 neighbours are already blue. This constrains propagation heavily.

Formal bound: Z(G) ≥ δ(G) in some cases — but not always. Find an example where Z(G) < δ(G).

**Lower bound technique 2 — Cut Vertices and Bridges (30 min):**

A **bridge** is an edge whose removal disconnects the graph. A **cut vertex** (articulation point) is a vertex whose removal disconnects the graph.

Claim: If G has a bridge e = (u,v) and removing e splits G into components G_u and G_v, then any zero forcing set must contain at least one vertex from each component *before* the bridge is traversed.

This gives a recursive structure for computing Z(G) on trees.

**Trees (20 min):**

For trees, Z(T) equals the **path cover number** P(T) — the minimum number of vertex-disjoint paths that together cover all vertices of T.

Intuition: each path in the cover corresponds to one "chain" of forcing.

*Example:* A star K₁,₅ has path cover number 5 (each leaf is its own path), so Z(K₁,₅) = 5... wait, we said Z(K₁,ₙ) = n-1. Recheck! With 4 leaves blue, the hub has exactly 1 white neighbour. So Z(K₁,ₙ) = n-1.

This corrects the path cover formula — the centre is also a path endpoint. Work through the star carefully.

---

**1:45–2:00 — Break**

---

**2:00–3:00 — Problem Session**

**Problem Set 2A:**

1. Find Z(G) for the Petersen graph (10 vertices, 15 edges). Prove both the upper and lower bound.

2. Let T be the tree formed by a path P₄ with a pendant (leaf) attached to each of the middle two vertices. Draw T and find Z(T).

3. Prove: for any graph G, Z(G) ≤ n-1, where n = |V(G)|. When does equality hold?

4. Prove: if G is a connected graph and v is a cut vertex, then Z(G) ≥ 2. *(Hint: consider what happens when propagation needs to "cross" through v.)*

5. *(Challenge)* Show that the zero forcing number is not monotone with respect to subgraphs: find graphs H ⊆ G where Z(H) > Z(G). Why does this make zero forcing harder to analyse than graph colouring?

---

**3:00–4:00 — The Linear Algebra Connection**

This session connects zero forcing to the original controllability motivation.

**The adjacency matrix:** The adjacency matrix A of a graph G is the n×n matrix where Aᵢⱼ = 1 if (i,j) ∈ E and 0 otherwise.

**Controllability of linear systems (on the board):**

A linear dynamical system on a graph G with controlled set S:

$$\dot{x}(t) = Ax(t) + Bu(t)$$

is **fully controllable** iff the controllability matrix [B | AB | A²B | ... | Aⁿ⁻¹B] has rank n.

**The connection (state as a theorem):**

> The minimum |S| for full controllability equals Z(G) (with appropriate matrix choice). More precisely: S is a zero forcing set ↔ A-S is not an eigenvalue set that prevents controllability.

This is a deep result. Students do not need to prove it, but they should see why the zero forcing rule is a natural "simulation" of the matrix rank condition.

*Discussion:* Why does a combinatorial rule (colouring) capture an algebraic condition (rank)?

**Homework:** H6 from zero_forcing.md.

---

### Day 7 (Week 2, Wednesday) — The Zero Forcing Game and Propagation Sequences

**Theme:** Playing the game; understanding propagation order.

---

**0:00–0:30 — Warm-up: Directed Zero Forcing**

Introduce the idea briefly: what if edges in G have a direction (directed graph / digraph)? The forcing rule can be adapted: a blue vertex forces its white out-neighbour only if it is the only white out-neighbour.

Does Z change for directed paths? Directed cycles? Explore on the board.

---

**0:30–1:45 — The Two-Player Zero Forcing Game**

**Game definition:**

- **Setter** wants to zero force G with as few initial blue vertices as possible.
- **Blocker** can, on each round, protect one vertex (that vertex cannot be forced this round even if it "should" be).

Play alternates: Setter picks a vertex to add to the initial set (or has already fixed S before the game starts — variants exist). Then Blocker picks a vertex to protect. Then the colour change rule is applied (skipping protected vertices). Repeat until all vertices are blue (Setter wins) or propagation stalls forever (Blocker wins).

**Play on a 4×4 grid (on the board):**

Draw a large 4×4 grid. Assign Setter and Blocker roles to two students. Others observe and advise. Play two rounds (switch roles after the first).

*Observe:* Where does Blocker's protection have the most impact? Blockers should target "bottleneck" vertices — places where propagation must pass through.

**The game zero forcing number Z_B(G):** The minimum |S| such that Setter has a winning strategy, assuming both play optimally.

*Question:* Is Z_B(G) always equal to Z(G)?

*Answer:* No — Z_B(G) ≥ Z(G) always, but strict inequality is possible. (Blocker can disrupt a zero forcing set that would work in the solo game.)

---

**1:45–2:00 — Break**

---

**2:00–3:00 — Propagation Sequences**

Every zero forcing process generates a **propagation sequence**: the order in which vertices turn blue.

**Formal definition:** Let S = {s₁, ..., sₖ} be a zero forcing set. The propagation sequence is an ordering of all n vertices of G such that:
1. The first k elements are the elements of S.
2. Each subsequent vertex vᵢ was forced by some vertex vⱼ with j < i (the forcing vertex appears earlier in the sequence).

**Example on P₅:**

```
Vertices: 1, 2, 3, 4, 5 (path in order)
S = {1}
Propagation sequence: (1, 2, 3, 4, 5) — increasing sequence
```

**Example on the 3×3 grid** (vertices labelled (row, column)):

Start with top row blue: S = {(1,1), (1,2), (1,3)}. Propagation:
- (1,1) forces (2,1) (only white neighbour)
- (1,2) forces (2,2)
- (1,3) forces (2,3)
- (2,1) forces (3,1)
- (2,2) forces (3,2)
- (2,3) forces (3,3)

Sequence: (1,1),(1,2),(1,3),(2,1),(2,2),(2,3),(3,1),(3,2),(3,3).

*Observation:* Row indices are non-decreasing throughout. This is a 2D monotonicity condition — we will formalise it in Week 3.

**Problem session extension:** Find all valid propagation sequences for Z-forcing on a 2×3 grid, starting from the minimum zero forcing set. Are they all "2D monotone" in some sense?

---

**3:00–4:00 — Discussion: What Makes a Good Propagation Sequence?**

Group discussion around these questions:
1. Can two different zero forcing sets produce the same propagation sequence?
2. Can the same zero forcing set produce multiple different propagation sequences (different forcing orders)?
3. Is there always a propagation sequence that is "monotone" in some natural sense?

These questions motivate Week 3. The answers connect to the PMI sequences defined by the professor.

**Homework:** H7 from zero_forcing.md.

---

### Day 8 (Week 2, Thursday) — Problem Session and Mini-Presentations

**0:00–1:45 — Extended Problem Exploration**

Students choose an investigation thread:

**Thread A — Zero Forcing Bounds Race:**  
For each of the following graphs, find the exact Z(G) with proof: (i) the icosahedron graph, (ii) the 3-cube graph Q₃ (vertices = binary strings of length 3, edges between strings differing in one bit), (iii) a random graph on 8 vertices (each edge present with probability 1/2 — draw it, then find Z).

**Thread B — Game Analysis:**  
For the zero forcing game on C₅ (5-cycle), determine Z_B(C₅). Write out the optimal strategy for both Setter and Blocker. Try the same for C₆. What pattern do you see?

**Thread C — Propagation Counting:**  
For the path Pₙ with S = {1}, there is exactly one propagation sequence: (1, 2, 3, ..., n). For the 2×2 grid with an appropriate S, count all valid propagation sequences. Can you find a formula for the number of propagation sequences for the n×n grid?

---

**1:45–2:00 — Break**

---

**2:00–4:00 — Mini-Presentations**

Each student presents one result from Week 2 (5–8 minutes, whiteboard):
- A proof that Z(Kₙ) = n-1
- The game analysis on a specific graph
- A worked example of a propagation sequence and its 2D structure
- The linear algebra connection explained in their own words

End of Week 2: collect new sticky-note questions for Week 3.

---

## Week 3 — Sequences and Geometry

### Week 3 Goals
- Understand sequences, subsequences, and the concept of monotonicity.
- Prove the Erdős–Szekeres theorem using the pigeonhole principle.
- Understand what PMI sequences are and how they relate to zero forcing propagation.
- Understand the centerpoint theorem: why it is needed, what it says, and a sketch of why it holds.
- Know at least one genuinely open problem well enough to explain it to a non-expert.

---

### Day 9 (Week 3, Monday) — Sequences and Erdős–Szekeres

**Theme:** Order in disorder.

---

**0:00–0:30 — Warm-up: A Sequence Puzzle**

> I have a sequence of 17 distinct real numbers. I claim there must be either an increasing subsequence of length 5 or a decreasing subsequence of length 5. Is this true? What is the minimum sequence length that forces a monotone subsequence of length 5?

*(Answer: 4²+1 = 17.)*

Let students explore small cases first: n=5 (length 5 → monotone subseq of length 3), n=9 (length 9+1 = 10 → length 4), etc.

---

**0:30–1:45 — Main Session: Sequences and the Theorem**

Distribute **Handout: sequences_pmi.md**.

**Definitions (20 min):**
- Sequence, subsequence
- Increasing / decreasing / monotone subsequence
- Longest increasing subsequence (LIS)
- Work puzzles A and B from the handout together

**Patience sorting (20 min):**

Describe the patience sorting algorithm informally — read numbers left to right, build "piles" where each new number goes on the leftmost pile with a smaller top. If none, start a new pile. The number of piles at the end equals the LIS length.

Trace through example: (3, 1, 4, 1, 5, 9, 2, 6):

| Card | Action | Piles (tops) |
|------|--------|------|
| 3 | New pile | [3] |
| 1 | New pile | [3][1] — No: place on leftmost pile with top > 1. Top of pile 1 is 3 > 1. |

*(Refine: place each card on the leftmost pile whose top card is ≥ the card. Start new pile only if all tops are smaller.)*

Trace carefully through the full example. Count piles. Verify it equals LIS length.

**The Erdős–Szekeres Theorem (45 min):**

State the theorem. Do two worked examples illustrating the bound is tight. Then give the full pigeonhole proof (see Handout sequences_pmi.md Section 2 for the complete proof — walk through it on the board step by step).

Emphasise the structure of the proof: assign a label to each element, observe that labels from a bounded set, apply pigeonhole, derive a contradiction.

---

**1:45–2:00 — Break**

---

**2:00–3:00 — Problem Session**

**Problem Set 3A:**

1. Find the LIS of (1, 5, 2, 4, 3, 8, 7, 6). Use patience sorting to verify.

2. Prove the Erdős–Szekeres bound is tight: construct a sequence of exactly n² distinct numbers with no increasing or decreasing subsequence of length n+1. *(This is Problem H8 from the handout.)*

3. Let σ be a permutation of {1, ..., n}. The LIS of σ and the number of piles in patience sorting are equal. Prove that the LIS is the length of the longest chain in the partial order where i ≤ j iff position(i) < position(j) and value(i) < value(j).

4. *(Dilworth's theorem)* For any finite partially ordered set (P, ≤): the minimum number of chains needed to cover P equals the maximum size of an antichain. Verify this for the Erdős–Szekeres poset.

5. *(Challenge)* The RSK correspondence is a bijection between permutations of {1,...,n} and pairs (P,Q) of standard Young tableaux of the same shape. Under RSK, the LIS of the permutation equals the length of the first row of P. Can you find (from a reference) what the longest decreasing subsequence corresponds to?

---

**3:00–4:00 — Towards 2D: Point Sets in the Plane**

Introduce 2D sequences of points. Define a "2D increasing subsequence" (both coordinates increase). Prove or conjecture a 2D Erdős–Szekeres theorem.

Work through Puzzle E from the handout. Introduce the connection to zero forcing propagation sequences for grid graphs (preview of Day 10).

**Homework:** H8 and H9 from sequences_pmi.md.

---

### Day 10 (Week 3, Tuesday) — PMI Sequences and Controllability

**Theme:** The heart of the research.

---

**0:00–0:30 — Warm-up**

Return to the grid propagation sequences from Week 2, Day 7. Ask: looking at these sequences as 2D point sequences, what monotonicity property do they satisfy?

Let students observe and conjecture before the formal definition.

---

**0:30–1:45 — Main Session: PMI Sequences**

*(The coordinator presents the formal definition of PMI sequences as given in the professor's research notes. The following is a framework into which that definition should be inserted.)*

**Step 1: Review the 1D picture (15 min)**

For path graphs, propagation sequences are exactly increasing sequences (in the natural labelling). The Erdős–Szekeres theorem gives bounds on their structure. The zero forcing number of a path is 1 — corresponding to the unique starting point of an increasing sequence.

**Step 2: The 2D picture (25 min)**

For grid graphs:
- Vertices are labelled by (row, column) pairs.
- A propagation sequence is a sequence of these 2D labels.
- The condition "blue vertex with exactly one white neighbour forces it" translates into a constraint on the order of the 2D labels.

**Step 3: PMI — Formal Definition (30 min)**

*[INSERT DEFINITION FROM PROFESSOR'S RESEARCH HERE]*

Present the definition carefully with:
- The formal statement
- A concrete example of a PMI sequence
- A concrete example of a sequence that fails to be PMI and why
- The theorem connecting PMI to zero forcing propagation

**Step 4: Main theorem statement (15 min)**

State the theorem connecting PMI sequences to network controllability:

*[THEOREM FROM PROFESSOR'S RESEARCH — e.g., "S is a zero forcing set whose propagation sequence is a PMI sequence if and only if..."]*

---

**1:45–2:00 — Break**

---

**2:00–3:00 — Exploration Problems on PMI**

Students work through Problems E1, E2, E3 from the sequences handout, now interpreted in the PMI framework.

**Additional explorations:**

1. For the 2×2 grid, list every valid propagation sequence starting from the minimum zero forcing set. Which are PMI?

2. For the 2×3 grid, is every zero forcing propagation sequence a PMI sequence? Or are there forcing sequences that are not PMI?

3. Conjecture: is the minimum Z(G) always achieved by a zero forcing set whose propagation sequence is PMI? Test your conjecture on small grids and trees.

---

**3:00–4:00 — Open Problems and Research Directions**

Present 2–3 open problems from the professor's research that the students can now understand:

**Open Problem 1:** [OPEN PROBLEM FROM PROFESSOR'S RESEARCH]

**Open Problem 2:** [OPEN PROBLEM FROM PROFESSOR'S RESEARCH]

**Open Problem 3 (standard, safe):**
> Characterise all graphs G for which Z(G) = Z(G - e) for every edge e — that is, graphs where removing any single edge doesn't change the zero forcing number.

Students discuss which open problem they find most compelling and why.

**Homework:** H10 from sequences_pmi.md; attempt to formulate one new conjecture related to PMI sequences.

---

### Day 11 (Week 3, Wednesday) — The Centerpoint Theorem

**Theme:** A completely separate gem of discrete geometry.

---

**0:00–0:30 — Warm-up: The Mars Data Problem**

Present the problem cold — no hints.

> One thousand robots are distributed across a 500km × 500km region of Mars. Each robot knows its precise (x, y) GPS coordinate. The robots need to collectively agree on and transmit a **single (x, y) point** back to Earth that best summarises where they are. Bandwidth is so limited that only one point can be sent per day, and no robot knows any other robot's location (they can only agree on a protocol in advance).
>
> What point should they send?

Take answers. Likely responses:
- "The average" → challenge: what if one GPS is broken and reports (10⁶, 10⁶)?
- "The median of both coordinates" → great idea — but does it work?

Write the challenge on the board: **the coordinatewise median can be badly non-central**. This motivates the session.

---

**0:30–1:45 — Main Session: Centerpoint Theorem**

Distribute **Handout: centerpoint.md**.

**Act 1 — The Failure of the Average (15 min)**

Work through the outlier counterexample from the handout. Emphasise the concept of **breakdown point**: the average's breakdown point is 0 (one bad point ruins it), the median's is 50%.

**Act 2 — The Median in 1D (15 min)**

The median of 1D data: every halfline through the median contains at least n/2 points. Proof: if the median were not a centerpoint, more than half the data would be on one side — contradicting the definition of median.

**Act 3 — The Naïve 2D Median Fails (25 min)**

Work through the explicit counterexample from the handout (5 points: (3,0),(4,0),(5,0),(0,3),(0,4)).

Coordinatewise median = (3,0). Draw this on the board. Find the halfplane through (3,0) that contains only 1 point (the point itself). Conclude: (3,0) has Tukey depth only 1/5 < 1/3.

Ask students: where should the "real" centerpoint be? Have them guess by looking at the picture.

**Act 4 — The Centerpoint Definition and Theorem (30 min)**

Define Tukey depth and centerpoint formally. State the Centerpoint Theorem. Verify the theorem on the 5-point example by identifying a valid centerpoint.

Compare 1D median (guarantee n/2) vs. 2D centerpoint (guarantee n/3): the "cost" of an extra dimension.

State the general d-dimensional version (guarantee n/(d+1)) and the Helly connection.

**Act 5 — Helly's Theorem (15 min)**

State Helly's theorem. Prove the 1D special case (intervals on a line). Sketch why it implies the centerpoint theorem (intersect all halfplanes containing at least n/3 of the data — if no common point, Helly's theorem would be violated).

---

**1:45–2:00 — Break**

---

**2:00–3:00 — Problem Session**

**Problem Set 3B:**

1. Find a centerpoint for the set {(0,0),(4,0),(2,4)} (triangle). Verify your answer satisfies the n/3 condition.

2. Prove: the set of all centerpoints of a finite point set is convex. *(Hint: if c₁ and c₂ are both centerpoints, show any convex combination is also a centerpoint by considering halfplanes and using linearity.)*

3. Prove Helly's theorem in 1D: if n intervals on the real line are pairwise intersecting, they all share a common point.

4. Show that the centerpoint bound n/3 is tight in 2D: construct a set of n points such that no point (not even from outside the set) has every halfplane through it containing more than n/3 of the points. *(Hint: use a triangle arrangement.)*

5. *(Challenge)* The **Radon partition theorem** says: any set of d+2 points in ℝᵈ can be partitioned into two sets whose convex hulls intersect. Use Radon's theorem (you may cite it without proving it) to give a short proof of Helly's theorem in the plane.

---

**3:00–4:00 — Applications and Open Problems**

Discuss applications of the centerpoint:

- **Robust statistics:** Centerpoint as a high-dimensional analogue of the median. Used in depth-based data analysis.
- **Computational geometry:** Finding centerpoints efficiently. Best known: O(n log n) in 2D. Can it be done in O(n)?
- **Voting theory:** The "median voter theorem" is the 1D centerpoint theorem. Plott's condition is the 2D analogue — and it almost never holds! This is why 2D voting is typically indeterminate.
- **Machine learning:** Outlier-robust classifiers use depth-based notions.

**Open Problems (all genuinely open):**

1. *Algorithmic Centerpoint:* Find a centerpoint of n points in ℝ² in O(n) time.

2. *Colourful Centerpoint:* If each point is coloured one of 3 colours with n/3 of each colour, must there be a "rainbow" centerpoint? (Every halfplane through it has points of all 3 colours.)

3. *First Selection Lemma (proved, but state it):* For n points in ℝ², some point of ℝ² lies inside at least cn³ triangles formed by the data points, where c > 1/27 is a universal constant. The best known c is approximately 1/27 — achieving exactly 1/27 is open.

**Homework:** H11 and H12 from centerpoint.md; prepare one slide (one piece of paper / one whiteboard section) for tomorrow's final presentation.

---

### Day 12 (Week 3, Thursday) — Final Presentations and Open Problems

**0:00–0:30 — Warm-up: Open Problem Speed Round**

Write 5 open problems on the board (one from each topic area). Students have 15 minutes to write a one-sentence description of each problem accessible to a 14-year-old. Share and compare.

---

**0:30–1:45 — Final Student Presentations**

Each student gives a 10–12 minute presentation. They may choose any topic from the three weeks and should:

1. State **one definition** clearly.
2. Give **one example** they worked out themselves.
3. State **one theorem** and give a sketch of the proof (or at least explain why the result is not obvious).
4. State **one open problem** related to the topic and explain why it is hard.

The coordinator and other students ask questions. Aim for mathematical depth over polish.

**Suggested topics if students are unsure:**
- Zero forcing on trees (characterise the zero forcing sets of a given tree)
- The Erdős–Szekeres theorem: statement, proof, and tight example
- Centerpoint theorem: the Mars motivation, why coordinatewise median fails, the theorem
- The zero forcing game and game zero forcing number
- PMI sequences and their connection to controllability

---

**1:45–2:00 — Break**

---

**2:00–3:30 — Open Problems Discussion**

A round-table discussion of genuinely open problems from all three weeks. Students vote on which problem they find most compelling.

Format: each student nominates one open problem. The coordinator (or the student) explains the problem in full. The group discusses:
- Why is it hard?
- What approaches might work?
- What small cases can we check?
- What would a solution even look like?

This is explicitly not a problem-solving session — the goal is to understand what open research looks like.

---

**3:30–4:00 — Closing Ceremony**

- Each student writes on an index card: *one thing I now understand that I didn't three weeks ago* and *one question I still have*.
- Coordinator reads them out (anonymously if preferred).
- Discuss next steps: recommended reading, research summer programs, competition mathematics, university mathematics.

**Resources to share:**

| Resource | For | Link/Note |
|----------|-----|-----------|
| Diestel, *Graph Theory* | Week 1–2 deepening | Free at diestel-graph-theory.com |
| Alon & Spencer, *The Probabilistic Method* | Combinatorics (advanced) | Classic textbook |
| Art of Problem Solving | More puzzles | artofproblemsolving.com |
| Graph Theory (Coursera/MIT OCW) | Structured video learning | Free online |
| Combinatorics: Topics, Techniques, Algorithms (Cameron) | Accessible graduate-level | Cambridge University Press |

---

## Coordinator's Reference Guide

### Pacing Notes

The schedule is intentionally generous — each main session has room to run long or short without derailing the week. Rough flexibility:

- If a group is strong: push harder on proofs, add more challenge problems, introduce directed graphs and digraph zero forcing.
- If a group is struggling: spend more time on worked examples, reduce the number of problems in each set, cut the game analysis from Day 7 and use that time for more practice.
- Never sacrifice the closing presentations — they are the most educationally valuable session of each week.

### Common Sticking Points by Topic

**Graphs:** Students often confuse "path" (no repeated vertices) with "walk" (repetition allowed). Be explicit about this distinction early. Also: "isomorphic" is conceptually hard — use physical analogies (same network, different labelling = same city map rotated and renamed).

**Zero Forcing:** The forcing rule seems simple but students regularly misapply it — they try to force a vertex that has more than one white neighbour. Slow down, trace step by step, and have students narrate each forcing step aloud before writing it down.

**Erdős–Szekeres:** The proof is elegant but the pigeonhole step is subtle (assigning (eᵢ, dᵢ) pairs). Work through it at least twice: once quickly, then very slowly with students narrating each line. The "tight example" (construction achieving exactly n²) is the best way to consolidate understanding.

**Centerpoint:** The coordinatewise median counterexample is the crux of the whole session — do not rush past it. Make sure students can compute a halfplane through the coordinatewise median that contains very few points. Then the gap between "what we have" and "what we need" is clear.

### Proof-Writing Guidance

Most A-level students have not written mathematical proofs. Introduce the following scaffold explicitly on Day 2 and reinforce throughout:

```
Proof structure:
1. "We want to show: [restate the claim]"
2. "Assume [set up notation/hypotheses]"
3. "Notice that [key observation]"
4. "Therefore [logical consequence]"
5. "This proves [restate what was proved] □"
```

Encourage students to circle "key steps" in their proofs — the one line that carries the argument. Everything else is set-up and clean-up.

### Differentiating for Strong Students

- Ask "can you generalise this to directed graphs?"
- Push on tight examples: not just proving the theorem but constructing extremal cases.
- Introduce the Zero Forcing Conjecture (maximum nullity conjecture): for any graph G, Z(G) + M(G) = n where M(G) is the maximum nullity of a matrix from the "family" associated with G. This is open.
- Introduce the connection to minimum rank problems (symmetric matrices with prescribed zero pattern).

### Differentiating for Students Who Find It Hard

- Stay with n = 3,4,5 vertex examples on every topic.
- For zero forcing: replace proof-writing with careful tracing of examples. Can they consistently apply the rule without error? That is the first milestone.
- For Erdős–Szekeres: focus on the statement and the tight example, skip the proof on first pass.
- For centerpoint: the counterexample to coordinatewise median is accessible even without the full theorem.

---

## Complete Materials Checklist

**Print one copy per student on Day 1:**
- [ ] `handouts/survey.md`
- [ ] `handouts/networks_intro.md`

**Print on Day 5 (Week 2, Monday):**
- [ ] `handouts/zero_forcing.md`

**Print on Day 9 (Week 3, Monday):**
- [ ] `handouts/sequences_pmi.md`

**Print on Day 11 (Week 3, Wednesday):**
- [ ] `handouts/centerpoint.md`

**Supplies (for the full three weeks):**
- [ ] Whiteboard markers in at least 3 colours (blue and white are thematic for zero forcing)
- [ ] Graph paper, 5+ sheets per student per session
- [ ] Sticky notes (for open questions board)
- [ ] Index cards (for Day 12 closing exercise)
- [ ] Coloured dot stickers (for physically playing zero forcing on large drawn graphs)
- [ ] Large paper or poster boards for the grid game on Day 7

---

## Quick Reference: All Key Definitions

| Concept | Definition |
|---------|-----------|
| Graph G = (V,E) | V = vertices, E = edges (pairs of vertices) |
| Degree d(v) | Number of edges at v |
| Handshaking Lemma | Σ d(v) = 2\|E\| |
| Tree | Connected acyclic graph |
| Bipartite | 2-colourable with no monochromatic edges |
| χ(G) | Chromatic number: min colours for proper colouring |
| Euler's formula | V - E + F = 2 (connected planar graph) |
| Colour change rule | Blue vertex with exactly 1 white neighbour forces it blue |
| Zero forcing set S | S such that propagation colours all vertices blue |
| Z(G) | Minimum size of a zero forcing set |
| Z(Pₙ) | 1 |
| Z(Cₙ) | 2 |
| Z(Kₙ) | n-1 |
| Z(K₁,ₙ) | n-1 |
| Z(Pₘ × Pₙ) | min(m,n) (conjectured in Week 2; prove in Week 3) |
| Propagation sequence | Ordering of V recording zero forcing order |
| LIS | Longest increasing subsequence |
| Erdős–Szekeres | Sequence of mn+1 → increasing subseq of length m+1 or decreasing of length n+1 |
| PMI sequence | [Definition from professor's research] |
| Tukey depth | Fraction of data in worst-case halfplane through a point |
| Centerpoint | Point of maximum Tukey depth; depth ≥ 1/(d+1) always |
| Helly's theorem | d+1 pairwise-intersecting convex sets in ℝᵈ → common intersection |
