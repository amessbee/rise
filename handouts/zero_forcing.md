# Handout 2 — Zero Forcing Sets and the Controllability Game

*Research Lab Internship — Days 2–3*

---

## Motivation: Can You Control a Network?

Consider a network of 50 robots floating in formation. Each robot adjusts its position based on a simple rule: move towards the average position of its neighbours. You can directly command only a few robots — the rest follow autonomously.

**Question:** What is the minimum number of robots you must directly command to steer the entire swarm to any target formation?

This is the **minimum controllability problem**. It turns out to have a beautiful answer in terms of a combinatorial game on the graph.

---

## The Zero Forcing Colour Rule

**Setup:** Assign each vertex of a graph a colour — either **blue** (active/controlled) or **white** (uncontrolled). We start with some vertices coloured blue, and we want to eventually colour all vertices blue.

**The Colour Change Rule:**
> A **blue** vertex that has exactly **one white** neighbour **forces** that neighbour to turn blue.

This rule is applied repeatedly until no more changes are possible.

**Example — Path P₅:**

Label vertices 1, 2, 3, 4, 5 in order.

```
Initial:  ● — ○ — ○ — ○ — ○
```

- Vertex 1 is blue. Its neighbours: only vertex 2. Vertex 2 is white. Vertex 1 has exactly one white neighbour → vertex 1 forces vertex 2.

```
Step 1:   ● — ● — ○ — ○ — ○
```

- Vertex 2 is now blue. Its white neighbours: vertex 3 (vertex 1 is already blue). Exactly one white neighbour → vertex 2 forces vertex 3.

```
Step 2:   ● — ● — ● — ○ — ○
          Step 3:  ● — ● — ● — ● — ○
          Step 4:  ● — ● — ● — ● — ●
```

Starting with just vertex 1 coloured blue, we eventually colour all 5 vertices blue. So {1} is a **zero forcing set** for P₅.

---

## Key Definitions

**Zero Forcing Set:** A set S of vertices such that, starting with S coloured blue, the colour change rule eventually colours all vertices blue.

**Zero Forcing Number Z(G):** The minimum size of a zero forcing set for graph G.

**Propagation sequence:** An ordering v₁, v₂, ..., vₙ of vertices recording the order in which they turn blue (vertices in S are coloured first, then the forced vertices in the order they are forced).

---

## Computing Z(G): Examples

### Path Pₙ

**Claim:** Z(Pₙ) = 1.

**Proof:** Label vertices 1 through n. Start with {1} blue. At each step, the rightmost blue vertex has exactly one white neighbour (the next vertex to its right), so it forces that neighbour. Eventually all vertices turn blue. □

### Cycle Cₙ (n ≥ 3)

**Claim:** Z(Cₙ) = 2.

*Why at least 2:* If only 1 vertex is blue, it has 2 white neighbours (on a cycle), so it cannot force either. Nothing propagates.

*Why 2 suffices:* Choose two adjacent vertices and colour them blue. The first has one white neighbour (the vertex to its left, since the other neighbour — the second blue vertex — is already blue), so it forces it. Similarly the second blue vertex forces to the right. Two "chains" propagate and meet on the opposite side of the cycle.

### Complete Graph Kₙ

**Claim:** Z(Kₙ) = n-1.

*Why at least n-1:* In Kₙ, every vertex is connected to every other. If fewer than n-1 vertices are blue, the remaining white vertices each have at least 2 white neighbours (in fact many), so no forcing can occur.

*Why n-1 suffices:* Colour n-1 vertices blue. The one remaining white vertex has exactly 1 white neighbour... wait, no: it has 0 white neighbours (all others are blue). Every blue vertex has exactly 1 white neighbour (the one uncoloured vertex). So any one of the blue vertices can force the last white one. □

### Star K₁,ₙ

The star has one hub connected to n leaves.

**Claim:** Z(K₁,ₙ) = n-1.

*Lower bound:* If k ≤ n-2 leaves are blue, the hub has at least 2 white neighbours (the remaining leaves). The hub is white and cannot force. The blue leaves each have only the hub as their neighbour, and it is white — but each blue leaf has exactly 1 white neighbour, so each leaf *can* force the hub. Once the hub turns blue, it has n-k ≥ 2 white neighbours — still can't force.

*Careful analysis:* With n-1 leaves blue: the hub has exactly 1 white neighbour (the last leaf). Each blue leaf forces the hub. Once hub is blue, hub has 1 white neighbour → forces the last leaf. Z(K₁,ₙ) = n-1. ✓

### 3 × 3 Grid

```
○ — ○ — ○
|       |       |
○ — ○ — ○
|       |       |
○ — ○ — ○
```

**Claim:** Z = 3. One full row (or column) suffices as a zero forcing set.

*Why 3 suffices:* Colour the top row {(1,1),(1,2),(1,3)} blue. Each top vertex has exactly one white neighbour directly below it in the second row. So all three top vertices simultaneously force the second row blue. Now the second row is blue, and similarly forces the third row.

*Why Z ≥ 3:* [This requires a more careful argument — see below.]

**Lower bound argument sketch:** In each column, at most one initial blue vertex in that column can "start" a chain going downward. To cover all 3 columns, we need at least 3 initial blue vertices.

---

## The Zero Forcing Game

A **two-player game** version:

- **Player A (Setter)** wants to zero force the graph with as few initially blue vertices as possible.
- **Player B (Blocker)** wants to prevent the propagation from completing.

**Game rules:**
1. Setter declares the initial set S (or builds it one vertex at a time — variants exist).
2. Blocker may "protect" one vertex per round — a protected vertex cannot be forced that round.
3. Setter applies the colour change rule (unprotected vertices may be forced).
4. Repeat until all vertices are blue (Setter wins) or the game stalls (Blocker wins).

**The game zero forcing number** (denoted Z_B(G) or similar) is the minimum |S| such that Setter wins regardless of Blocker's strategy.

**Questions for exploration:**
- For which graphs is Z_B(G) = Z(G)?
- Can Blocker's strategy always protect a specific vertex indefinitely?
- What is Z_B(Cₙ)? Z_B(Kₙ)?

---

## Puzzles and Problems

**Puzzle 1.** Find Z(G) for the "friendship graph" — three triangles sharing a common vertex. (Draw it.)

**Puzzle 2.** A *threshold graph* is built by repeatedly adding a vertex that is either isolated or connected to all existing vertices. Find Z(G) for a threshold graph built from 5 vertices.

**Puzzle 3.** For the Petersen graph (draw: a 5-cycle, a pentagram, and 5 spokes connecting outer to inner), what is Z?  
*(Answer: 5 — but prove it!)*

**Puzzle 4.** Prove that for any graph G on n vertices: Z(G) ≤ n-1. When does equality hold?

**Puzzle 5.** Prove that Z(G) ≥ δ(G) - 1 is NOT always true (find a counterexample). Here δ(G) is the minimum degree.

**Puzzle 6 (connect to controllability).** A graph G is called **controllable from S** if G can be driven from any state to any other state when S is the controlled set. It is known that G is controllable from S if and only if S is a zero forcing set AND... [additional condition the professor will specify]. What does "controllable" mean in terms of the graph structure?

---

## Homework

**H5.** Find Z(G) for the n×m grid graph for small values (2×2, 2×3, 3×3, 3×4). Conjecture a formula for Z(Pₙ × Pₘ).

**H6.** Show that for any tree T, the zero forcing number equals the *path cover number* P(T) — the minimum number of vertex-disjoint paths that cover all vertices of T.

**H7 (Challenge).** Let G be a graph with n vertices and let λ be the largest eigenvalue of the adjacency matrix of G (the matrix with 1s where edges are and 0s elsewhere). It is conjectured that Z(G) + (the maximum nullity of some associated matrix) = n. Look up what "nullity" means and try to state this conjecture precisely for a small example.

---

## Further Exploration: Zero Forcing and Linear Algebra

The connection to controllability goes through linear algebra. A linear dynamical system on a graph is governed by:

$$\dot{x}(t) = Ax(t) + Bu(t)$$

where:
- x(t) is the state vector (one entry per vertex).
- A is a matrix encoding the graph structure (the "adjacency" or "Laplacian" matrix).
- B is the control matrix (non-zero columns correspond to the controlled vertices S).
- u(t) is the input signal.

The system is **controllable** if and only if the controllability matrix [B, AB, A²B, ..., Aⁿ⁻¹B] has full rank.

The remarkable fact is: the minimum |S| for full controllability equals Z(G) (with appropriate matrix choice). The zero forcing game is a visual, combinatorial shadow of this algebraic condition.
