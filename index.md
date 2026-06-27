---
layout: home
title: RISE — Research Internship Program
---

## Welcome

RISE is a four-week mathematics research program for A-level students. The program covers graph theory, network controllability, combinatorial sequences, and discrete geometry — topics drawn from active mathematical research that are accessible with only A-level background.

---

## Program Materials

### 📋 Coordinator Guide

[**Full week-by-week plan →**](plan.md)  
Day-by-day schedule, facilitator notes, problem sets, and student host assignments for all 16 sessions.

---

### 📄 Student Handouts

|     | Handout                                                                    | When       |
| --- | -------------------------------------------------------------------------- | ---------- |
| 1   | [Background Survey](handouts/survey.md)                                    | Day 1      |
| 2   | [Introduction to Graphs and Networks](handouts/networks_intro.md)          | Days 1–2   |
| 3   | [Zero Forcing Sets and the Controllability Game](handouts/zero_forcing.md) | Days 5–7   |
| 4   | [Sequences, Subsequences, and PMI](handouts/sequences_pmi.md)              | Days 9–10  |
| 5   | [The Centerpoint Theorem](handouts/centerpoint.md)                         | Days 11–12 |
| 6   | [How to Give a Research Presentation](handouts/presentation_guide.md)      | Days 13–16 |

---

### 🎮 Interactive Demos

Run in your browser — no installation needed.

| Demo                                                    | Description                                                                                   |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| [Zero Forcing Game](interactive/zero_forcing_game.html) | Click vertices to color them blue, then simulate the zero forcing rule on various graphs     |
| [PMI Grid Explorer](interactive/pmi_grid.html)          | Explore zero forcing propagation on grid graphs and visualize the 2D sequence structure       |
| [Centerpoint Visualizer](interactive/centerpoint.html)  | Click to place points, then find the coordinatewise median, true centerpoint, and Tukey depth |
| [Sequences & Patience Sort](interactive/sequences.html) | Animate patience sorting on any sequence to find the longest increasing subsequence           |

---

### 🐍 Python Notebooks

Open in Google Colab (free, no installation) or download for Jupyter.

| Notebook                                                      | Topics                                            |                                                                                                                                                |
| ------------------------------------------------------------- | ------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| [Zero Forcing](notebooks/zero_forcing.ipynb)                  | NetworkX, Z(G), propagation animation             | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/amessbee/rise/blob/main/notebooks/zero_forcing.ipynb)    |
| [Centerpoint & Tukey Depth](notebooks/centerpoint.ipynb)      | Point clouds, depth computation, visualisation    | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/amessbee/rise/blob/main/notebooks/centerpoint.ipynb)     |
| [Sequences & Erdős–Szekeres](notebooks/sequences_erdos.ipynb) | Patience sorting, tight examples, 2D subsequences | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/amessbee/rise/blob/main/notebooks/sequences_erdos.ipynb) |
| [Graph Theory Networking](https://colab.research.google.com/drive/1ra0HqAxoRvdXzdqeGkK_W4xGr2HiuAQk?usp=sharing) | Graph foundations, topologies, degree centrality | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1ra0HqAxoRvdXzdqeGkK_W4xGr2HiuAQk?usp=sharing) |
---

## Open Problems

By the end of the program, students will be able to state and discuss these open problems:

- **Zero Forcing Conjecture:** Is Z(G) always equal to the maximum nullity M(G) for any graph G?
- **Algorithmic Centerpoint:** Can a centerpoint of n points in ℝ² be found in O(n) time?
- **Colorful Centerpoint:** If n points are colored with k colors (n/k of each), must there be a rainbow centerpoint?
- **PMI Sequences:** [Open problem from the professor's research — to be stated in session.]
- **Ramsey Numbers:** What is R(5,5)? (Known to be between 43 and 48.)

---

_Program hosted by Dr. Mudassir Shabbir at LUMS. Student coordinators: Danish, Uzayr, Nimra, Ahsan, Maaz, Basit._
