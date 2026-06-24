# RISE — Research Internship Programme

A **four-week mathematics research programme** for A-level students (ages 16–18), exploring graph theory, network controllability, combinatorics, and discrete geometry through hands-on exploration, open problems, and interactive tools.

🌐 **Live site:** [amessbee.github.io/rise](https://amessbee.github.io/rise)

---

## What is RISE?

RISE introduces students with no university mathematics background to **active research problems** — questions that professional mathematicians are still working on. By the end of the programme, every student can explain an open problem, state a theorem they have proved themselves, and deliver a polished 12–15 minute research presentation.

**Core mathematical content:**
| Track | Topics |
|-------|--------|
| Graphs & Networks | Graph theory, Euler's theorem, planarity, colouring |
| Network Controllability | Zero forcing sets, the forcing game, propagation sequences |
| Combinatorics | Sequences, Erdős–Szekeres theorem, PMI sequences |
| Discrete Geometry | Centerpoint theorem, Helly's theorem, Tukey depth |
| Communication | Scientific storytelling, slides/posters, Q&A skills |

---

## Programme Structure

4 weeks × 4 days × 4 hours = **64 hours** of contact time.

| Week | Theme | Days |
|------|-------|------|
| 1 | Graphs and Networks | Days 1–4 |
| 2 | Controlling Networks: Zero Forcing | Days 5–8 |
| 3 | Sequences and Geometry | Days 9–12 |
| 4 | Research Communication | Days 13–16 |

→ See [plan.md](plan.md) for the full day-by-day coordinator guide with timing, facilitator notes, problem sets, and student host assignments.

---

## Student Handouts

Printable A4 handouts, one per topic. Each contains definitions, worked examples, puzzles, homework problems, and at least one genuinely open problem.

| Handout | Topic | Key Result |
|---------|-------|-----------|
| [Survey](handouts/survey.md) | Background assessment | — |
| [Networks Intro](handouts/networks_intro.md) | Graphs, trees, planarity | Euler's theorem, V−E+F=2 |
| [Zero Forcing](handouts/zero_forcing.md) | Zero forcing sets and game | Z(G) characterises controllability |
| [Sequences & PMI](handouts/sequences_pmi.md) | Subsequences, Erdős–Szekeres | Any mn+1 elements → long monotone run |
| [Centerpoint](handouts/centerpoint.md) | Centerpoint theorem | Every point cloud has a "robust centre" |
| [Presentation Guide](handouts/presentation_guide.md) | Research communication | Four-act structure, slide design, Q&A |

---

## Interactive Demos

Run directly in your browser — no installation required.

| Demo | What it does |
|------|-------------|
| [🎮 Zero Forcing Game](interactive/zero_forcing_game.html) | Colour vertices blue and simulate the forcing propagation on paths, cycles, grids, stars, and the Petersen graph |
| [📊 PMI Grid Explorer](interactive/pmi_grid.html) | Explore zero forcing propagation sequences on grid graphs and see their 2D monotone structure |
| [📍 Centerpoint Visualiser](interactive/centerpoint.html) | Add points by clicking, then see the coordinatewise median, true centerpoint, and Tukey depth heatmap |
| [🔢 Sequences & Patience Sort](interactive/sequences.html) | Enter a sequence and watch patience sorting animate the LIS discovery step by step |

---

## Python Notebooks

Open any notebook in **Google Colab** (no installation needed) or run locally with Jupyter.

| Notebook | Topics | Open in Colab |
|----------|--------|--------------|
| [Zero Forcing](notebooks/zero_forcing.ipynb) | NetworkX graphs, Z(G) computation, propagation visualisation | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/amessbee/rise/blob/main/notebooks/zero_forcing.ipynb) |
| [Centerpoint & Tukey Depth](notebooks/centerpoint.ipynb) | 2D point clouds, Tukey depth, approximate centerpoint finder | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/amessbee/rise/blob/main/notebooks/centerpoint.ipynb) |
| [Sequences & Erdős–Szekeres](notebooks/sequences_erdos.ipynb) | Patience sorting, LIS, tight examples, 2D increasing subsequences | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/amessbee/rise/blob/main/notebooks/sequences_erdos.ipynb) |

---

## For Student Coordinators

The six student coordinators are: **Danish, Uzayr, Nimra, Ahsan, Maaz, Basit**.

Each of the 16 programme days has a host slot in [plan.md](plan.md). To claim a day:
1. Open `plan.md`
2. Find the day you want to host
3. Replace `—` in the `> **Host:** —` line with your name
4. Commit and push (or ask the lab coordinator to record it)

The [host assignment table](plan.md#host-assignments) near the top of `plan.md` gives an overview of all 16 days.

---

## Repository Layout

```
rise/
├── README.md                        ← you are here
├── plan.md                          ← full coordinator guide
├── handouts/
│   ├── survey.md
│   ├── networks_intro.md
│   ├── zero_forcing.md
│   ├── sequences_pmi.md
│   ├── centerpoint.md
│   └── presentation_guide.md
├── interactive/
│   ├── zero_forcing_game.html       ← browser-based zero forcing game
│   ├── pmi_grid.html                ← PMI propagation sequence explorer
│   ├── centerpoint.html             ← centerpoint & Tukey depth visualiser
│   └── sequences.html               ← patience sorting & LIS animator
└── notebooks/
    ├── zero_forcing.ipynb
    ├── centerpoint.ipynb
    └── sequences_erdos.ipynb
```

---

## Credits

Programme designed by the research group of [Professor Name], [University].  
Student coordinators: Danish, Uzayr, Nimra, Ahsan, Maaz, Basit.

Mathematical content covers research in graph controllability, zero forcing sets, and discrete geometry. Interactive tools and notebooks were developed as part of the RISE programme.
