# Handout 4 — The Centerpoint Theorem

*Research Lab Internship — Day 4–5*

---

## The Problem: Aggregating Data Across Distance

Imagine a swarm of 1000 robots deployed on the surface of Mars. Each robot is a mobile sensor stationed at a different location (think of their coordinates as 2D points on a map of the Martian terrain). Every few hours, each robot takes readings from thousands of different sensors: temperature, soil composition, pressure, radiation levels, and so on.

Your research lab on Earth would love to analyse all of this raw data. But there's a problem: **transmitting data from Mars to Earth is extremely expensive**. The signal is weak, the distance is vast (up to 20 minutes at the speed of light), and bandwidth is extremely limited.

You cannot afford to send all 1000 robots' full sensor readings every hour.

**The challenge:** Each robot must send just a single representative number (or a 2D point — its "position summary") such that when your lab on Earth receives all 1000 reports, it can reconstruct a good aggregate picture of what's happening on Mars.

Alternatively: the robots must agree among themselves on a **single representative point** to send back, and it should be a "good central" summary of where they are.

How should the robots choose this representative point?

---

## Option 1: The Average (Arithmetic Mean)

The most natural idea: compute the average of all the robots' coordinates.

$$\bar{x} = \frac{1}{n}\sum_{i=1}^n x_i, \qquad \bar{y} = \frac{1}{n}\sum_{i=1}^n y_i$$

**Why it's appealing:** Easy to compute, well-understood, minimises squared distances to the data.

**Why it fails:** One faulty sensor can ruin everything.

**Example:** Suppose 999 robots are clustered in a 10km × 10km region, but 1 robot's GPS is broken and it reports its location as (1,000,000 km, 0). The average gets pulled far away from all the actual robots.

```
         ● ● ●          ← 999 real robots here
         ● ● ●
             ×           ← average: pulled far to the right
                                        ◆  ← faulty robot
```

The average is **not robust** to outliers. In statistics, we say the average has **breakdown point 0** — even a single bad measurement can corrupt it completely.

---

## Option 2: The Median (1D)

For 1D data — say, just the temperature readings — the **median** is the middle value when all readings are sorted.

**Example:** Readings from 7 sensors: {12, 15, 14, 100, 13, 11, 16}.  
Sorted: 11, 12, 13, **14**, 15, 16, 100.  
Median = 14. The outlier (100) has no effect on the result.

**Key property of the median:** Any halfline (ray) starting at the median contains at least half the data points.

More precisely: there are at least ⌈n/2⌉ values ≤ median and at least ⌈n/2⌉ values ≥ median.

**Breakdown point:** The median can tolerate up to 50% corrupted data and still give a reasonable answer. This is the best possible for any estimator.

**So the median is great for 1D data.** What about 2D?

---

## The Naïve 2D Extension: Coordinatewise Median

The obvious attempt: take the median of all x-coordinates and the median of all y-coordinates separately, and use the pair (median_x, median_y) as the 2D representative.

**Does it work?**

Let's test with a small example. Consider 5 points:

$$P_1 = (3, 0), \quad P_2 = (4, 0), \quad P_3 = (5, 0), \quad P_4 = (0, 3), \quad P_5 = (0, 4)$$

```
  y
5 |
4 |  ● P₅
3 |  ● P₄
2 |
1 |
0 |_ _ _ ●_ _ ●_ _ ●_ _  x
  0  1  2  3  4  5
              P₁  P₂  P₃
```

**Coordinatewise medians:**
- x-values: 0, 0, 3, 4, 5 → median = **3**
- y-values: 0, 0, 0, 3, 4 → median = **0**

So the coordinatewise median is **(3, 0)** — which is the point P₁.

**Is P₁ = (3,0) a good "central" representative?**

A "good" central point should have the property that no matter which direction you look, a reasonable fraction of the data points are "behind" you (on the other side from where you're looking). Formally:

> A point c is **central** if every halfplane containing c also contains at least n/3 of the data points.

(*A halfplane is everything on one side of a line.*)

Let's check P₁ = (3, 0):

Draw the line through P₁ = (3,0) with equation y = -¾(x - 3), i.e., y = -¾x + 9/4.

```
  y
  |   / line
4 |  ● P₅         Points above the line:
3 |  ● P₄           P₁, P₂, P₃, P₄, P₅ — all 5!
  | /              Points below the line:
  |/_ _ _ _ _       only P₁ is on the line.
 /|          x
  P₁ P₂ P₃
```

The halfplane *below* this line (on the opposite side from P₄ and P₅) contains **only P₁ itself**. That is just 1 out of 5 points, which is only 20% — far less than 1/3 ≈ 33%.

**Conclusion: The coordinatewise median is NOT a "central" point for this dataset.** It ends up on the edge, not in the middle.

This is the fundamental problem with the naïve 2D extension: it does not account for the *direction* of the data's spread. The points P₄ and P₅ are far above P₁, but the coordinatewise approach doesn't "see" this directionality.

---

## The Right Definition: Centerpoint

We need a definition that works in all directions simultaneously.

**Definition (Centerpoint):**  
A point c (not necessarily one of the data points) is a **centerpoint** of a point set P = {P₁,...,Pₙ} in the plane if:

> Every halfplane that contains c also contains at least ⌈n/3⌉ of the points.

Equivalently: no halfplane that *excludes* c can contain more than 2n/3 of the points.

**Back to our example:** For P = {(3,0),(4,0),(5,0),(0,3),(0,4)}, what is the centerpoint?

A good candidate: the "central" region of the convex hull of the points. 

Let's try c = (2, 1):
- Every halfplane through (2,1) must contain at least ⌈5/3⌉ = 2 points.
- Intuitively, (2,1) is "inside" the spread of the data.

*(Full verification: check several directions — above, below, left, right, and diagonal.)*

---

## The Centerpoint Theorem

**Theorem (Centerpoint Theorem):**  
For any finite set of n points in the plane, there exists a **centerpoint** — a point c such that every halfplane containing c contains at least n/3 of the data points.

More generally, in d-dimensional space: every set of n points has a centerpoint c such that every halfspace containing c contains at least n/(d+1) of the points.

**Important:** The centerpoint is guaranteed to exist, but it may not be one of the data points.

**The bound 1/3 is tight:** For 3 points forming a triangle, the only centerpoint is the interior of the triangle — and the bound ⌈3/3⌉ = 1 is achieved with equality for any direction.

---

## Comparison with the 1D Median

| Property | 1D Median | 2D Centerpoint |
|----------|-----------|----------------|
| Fraction guaranteed on each side | ≥ 1/2 | ≥ 1/3 |
| Unique? | Yes (up to tie-breaking) | Generally not unique |
| One of the data points? | Yes (for odd n) | Not necessarily |
| Computation | Sort: O(n log n) | O(n log n) in 2D |
| Breakdown point | 50% | 33% |

The reduction from 1/2 to 1/3 is the "cost" of moving from 1D to 2D. In general dimension d, the guarantee is 1/(d+1).

---

## Why This Matters for the Mars Robots

Returning to our Mars scenario:

- The robots' positions are n points in 2D.
- If up to n/3 robots have faulty GPS (they report wrong locations), the centerpoint of the *true* positions is still a good representative.
- The faulty robots are the "outliers" — and 1/3 of them can be tolerated.
- No other single-point summary can guarantee this robustness.

So the robots should compute and transmit the **centerpoint** of their positions.

**Bonus:** The centerpoint also minimises the "Tukey depth" — the worst-case fraction of data on the wrong side. This has applications in statistics (robust regression), machine learning (outlier-tolerant clustering), and data visualisation.

---

## Helly's Theorem (A Beautiful Related Result)

The centerpoint theorem follows from a result called **Helly's theorem**, which is even more general.

**Helly's Theorem (1923):**  
Let C₁, C₂, ..., Cₙ be convex sets in ℝᵈ. If every d+1 of these sets have a common point, then all n sets have a common point.

In the plane (d=2): if every 3 of your convex sets overlap pairwise, then all of them share a common point.

**Example (d=1):** Let C₁, C₂, ..., Cₙ be intervals on the number line. If every 2 of them overlap, then all n of them share a common point (i.e., they all have a common intersection).  
*(This is clear from the 1D median: the median of all left endpoints lies in all intervals if any two overlap.)*

**Counterexample showing d+1 is necessary:** In the plane, take 3 intervals (thin rectangles) arranged like a "Y" — each pair overlaps at the centre, but no single point is in all three.

---

## Puzzles and Problems

**Puzzle 1.** For 6 points in the plane, what is the minimum number of points that must lie in every halfplane containing the centerpoint?  
*(Answer: ⌈6/3⌉ = 2 points.)*

**Puzzle 2.** Place 4 points at the corners of a square: (0,0), (1,0), (1,1), (0,1). Find a centerpoint. Is it unique?  
*(Hint: any point strictly inside the square works. So the centerpoint is not unique here.)*

**Puzzle 3.** Can the centerpoint be a vertex of the convex hull of the data? If yes, give an example. If no, prove it.  
*(Answer: No. If c is on the convex hull, there is a halfplane tangent to the hull at c that contains no other data points — but it must contain at least n/3 ≥ 1 other points.)*

**Puzzle 4.** Prove that the set of all centerpoints (points c satisfying the centerpoint condition) is a convex set.

**Puzzle 5.** Consider the 1D case: a set of n real numbers. Show that the **median** is a 1D centerpoint (satisfying every halfline through it containing ≥ n/2 values). Why is the bound n/2 better than n/(1+1) = n/2? (They're the same!)

**Puzzle 6 (Hard).** Prove Helly's theorem in 1D: if n intervals on the real line are pairwise overlapping, they all share a common point. *(Hint: take the maximum of all left endpoints.)*

---

## Homework

**H11.** Find a set of 9 points in the plane such that the centerpoint bound (≥3 points in every halfplane) is achieved with equality — i.e., there exists a halfplane through the centerpoint containing exactly 3 of the 9 points.

**H12.** In 3D, the centerpoint theorem says every n-point set has a centerpoint such that every halfspace through it contains ≥ n/4 points. Find a set of 4 points (not all on the same plane) where the centerpoint is the average and the bound n/4 = 1 is tight.

**H13 (Challenge).** The **Tukey depth** (or halfspace depth) of a point c with respect to a dataset P is:
$$\text{depth}(c, P) = \min_{\text{halfplane } H \ni c} \frac{|\{p \in P : p \in H\}|}{|P|}$$
The centerpoint is the point of maximum Tukey depth.

(a) Compute the Tukey depth of every point in {(0,0), (1,0), (0,1)} for the dataset P = {(0,0),(1,0),(0,1)}.  
(b) What is the maximum Tukey depth? What is the centerpoint?  
(c) The Tukey depth is always at most 1/(d+1) away from being maximally central. Can you make this precise?

---

## Open Problems

**Open Problem 1 (Algorithmic):** Given n points in ℝ² and a parameter δ, find a point c such that every halfplane containing c has at least δ·n points. The best known deterministic algorithm runs in O(n log n) time. Can you do it in O(n) time (linear time)?

**Open Problem 2 (Higher-Dimensional Centerpoint):** For points in ℝᵈ, the guaranteed fraction is 1/(d+1). This comes from Helly's theorem which is tight. But can you find a point that is "central" in a stronger sense in high dimensions? This connects to the unsolved **Grünbaum's conjecture** on centrally symmetric bodies.

**Open Problem 3 (Colourful Centerpoint):** Suppose you have n points, each coloured one of k colours, with n/k points of each colour. Must there be a "rainbow" centerpoint — a point that every halfplane through it contains points of all k colours? This is related to the **Colourful Helly theorem** and remains an active research area.
