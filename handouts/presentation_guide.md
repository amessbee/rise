# Handout 5 — How to Give a Research Presentation


---
[← Centerpoint](centerpoint.md) | [Program Home](../index.md)

---

*Research Lab Internship — Week 4*

---

## Why This Handout Exists

You have spent three weeks learning hard mathematics. Now comes the step that most students underestimate: explaining it to someone else.

This is not a soft skill tacked on at the end. The ability to communicate a mathematical idea — clearly, honestly, and compellingly — is what separates useful research from research that sits unread on a shelf. The Fields Medal goes to mathematicians who also give extraordinary talks. This is not a coincidence.

This handout covers everything you need to prepare and deliver a 12–15 minute research presentation.

---

## Section 1 — Know Your Audience

Before writing a single word of your talk, answer these two questions:

**1. What does my audience already know?**

The follow-up presentation may be to:
- Other A-level students (no university mathematics)
- Teachers and parents (intelligent non-specialists)
- University students or researchers (some mathematics background)
- A mixed audience

Your answer determines every definition you include and every word you choose. "Graph" means something precise to a mathematician and something vague to everyone else. If your audience is mixed, define everything — but do it through examples, not through formal notation.

**2. What do I want my audience to take away?**

Pick one thing. Not five things, not a list. One thing.

Write it as a single sentence: *"After my talk, the audience will know that [X]."*

Examples:
- "After my talk, the audience will know that you can control a social network from a surprisingly small set of nodes, and that a simple coloring game tells you how small."
- "After my talk, the audience will know that the obvious way to find the centre of a 2D point cloud (take the median of each coordinate separately) can fail badly, and there is a better concept called the centerpoint."

Everything in your talk serves this sentence. If a slide doesn't serve it, cut the slide.

---

## Section 2 — The Four-Act Structure

Every good mathematics talk, regardless of length, has four acts. This is not a rigid formula — it is a description of what audiences need.

```
┌──────────┬───────────────────┬────────────────────────────┬──────────────┐
│  HOOK    │      SETUP        │         RESULT             │   SO WHAT    │
│ 10–15%   │     20–25%        │         40–50%             │   15–20%     │
│ ~2 min   │     ~3 min        │         ~6 min             │   ~2 min     │
└──────────┴───────────────────┴────────────────────────────┴──────────────┘
      ↑              ↑                       ↑                     ↑
   Question      Definitions            Main theorem           Open problems
   or puzzle     + examples             + proof/evidence       + connections
```

---

### Act 1 — The Hook (roughly 10–15% of your time)

Open with a question, a puzzle, or a surprising fact. Not a definition. Not an agenda slide.

The audience must want to know the answer before you give them the tools to find it.

**Example hooks (for our topics):**

*For zero forcing:*
> "If you could choose five Twitter accounts to hold a fixed opinion, and every account eventually follows the majority of accounts it follows — which five would you pick to take over the whole network? And what's the minimum number you'd ever need, for any network?"

*For Erdős–Szekeres:*
> "I pick any 17 numbers. No matter what I pick, I promise you can always find either four of them in increasing order or four of them in decreasing order. Is that obvious? It shouldn't be. And it's exactly the right bound — 16 numbers can be chosen so you can't do it."

*For centerpoint:*
> "A thousand robots on Mars need to send a single GPS coordinate back to Earth — one point that summarizes where they all are. The obvious answer turns out to be badly wrong. Here's why."

**What makes a good hook:**
- It is concrete (a specific number, a specific scenario)
- It raises a question the audience can hold in their head
- It is slightly surprising — the answer is not obvious
- It connects to something the audience cares about (data, robots, social media, games)

**What does not work as a hook:**
- "In this talk I will cover three topics: first, the definition of a graph..."
- "Let G = (V, E) be a graph."
- "Graph theory is an important branch of mathematics."

---

### Act 2 — The Setup (roughly 20–25%)

Introduce only the definitions, notation, and background results that the audience needs for *this specific talk*. Not everything you know. Not everything you were taught. Only what is necessary.

**Rules for setup:**

**Rule 1:** Every definition must be followed immediately by an example. No exceptions.

Bad: "A zero forcing set S is a subset of V(G) such that..."
Good: "Imagine coloring some vertices blue. A blue vertex with exactly one white neighbor forces that neighbor blue. [Draw on board.] A set S is a zero forcing set if, starting with S blue, eventually everything turns blue."

**Rule 2:** Use the same notation throughout. If you call edges "edges" in Act 2, do not call them "connections" in Act 3.

**Rule 3:** If a definition is only needed once, consider whether you can define it inline ("...what graph theorists call a tree — a connected graph with no cycles — ...") rather than on its own slide.

**Rule 4:** Put the hardest definition last in the setup. The audience's attention is highest at the start of Act 2; use it for the definition they will need most.

---

### Act 3 — The Result (roughly 40–50%)

This is the heart of your talk. It may be:
- A theorem you understood and can prove
- An open problem you can precisely state and give evidence for
- An exploration where you found examples, tested conjectures, and found patterns
- A connection between two areas (e.g., sequences and graph controllability)

**Before the proof, give the intuition.** Tell the audience what the theorem is saying in plain language before you give the formal statement. Then give the formal statement. Then the proof.

**Structure for a theorem:**

1. *Plain statement:* "It turns out that the minimum number of blue vertices you ever need equals the answer to a completely different question about sequences."
2. *Formal statement:* "Theorem: Z(G) = ..."
3. *Why it's not obvious:* "You might think we could just... but that fails because..."
4. *Key idea of proof:* "The clever step is to assign a label (eᵢ, dᵢ) to each element and apply pigeonhole."
5. *One worked example:* Trace through the proof on a small case.

**If there is no complete proof:** Be honest. "I understand why this should be true, but the full proof uses techniques we didn't cover. Here's the key idea..." is fine. Do not pretend to prove something you cannot.

**Structure for an exploration without a complete theorem:**

1. *The question:* State what you were trying to find out.
2. *Small cases:* What happened for n = 2, 3, 4?
3. *The pattern:* What did you conjecture?
4. *Evidence:* What supports the conjecture? What would break it?
5. *The open question:* What would a complete answer look like?

This structure is perfectly legitimate for a research talk — most real research talks look like this.

---

### Act 4 — The So What (roughly 15–20%)

Answer the implicit question in every audience member's mind: *Why should I care?*

This act has three optional ingredients — use at least two:

**Connections:** Does your result connect to something the audience already cares about? ("This is why GPS navigation apps don't get confused by a single broken sensor.")

**Open problems:** State one or two things that are still unknown. This is the most intellectually honest part of any mathematics talk — it shows the boundary of human knowledge.

**What you would do next:** "If I had another month, I would try to..." This shows the audience that research is ongoing, and that they are seeing a snapshot, not a finished monument.

**Your closing sentence:** Plan this word for word. It should:
- Be short (one sentence)
- Be memorable
- Land cleanly, so the audience knows you are done

Examples:
- "So the next time you want to influence a network, remember: you don't need to control everyone. You just need to find the right zero forcing set."
- "The average breaks. The coordinatewise median breaks. But the centerpoint holds — and that is the right notion of centre for any dimension."

---

### Timing Reference: A 12-Minute Talk

The diagram below maps the four acts onto actual clock minutes for a 12-minute presentation. Use it to rehearse and to cut material that doesn't fit.

```
0        2        5              11       13  (minutes)
│        │        │               │        │
├────────┼────────┼───────────────┼────────┤
│  HOOK  │  SETUP │    RESULT     │SO WHAT │
│ puzzle │ 2 defs │ theorem+proof │open Qs │
│ + story│+ 2 figs│  + 1 example  │+closing│
└────────┴────────┴───────────────┴────────┘
```

If you are running a 15-minute talk, scale each segment up by roughly 25%. The proportions stay the same; the absolute durations shift.

---

## Section 3 — Slides and Poster Design

### Slides

**The cardinal rule:** One idea per slide.

If you have two ideas, use two slides. This feels wasteful on paper. In a talk, it gives your audience time to absorb the first idea before the second arrives.

**Slide titles are conclusions, not topics.**

| Bad title (topic) | Good title (conclusion) |
|-------------------|------------------------|
| Zero Forcing Definition | A blue vertex forces its lone white neighbor |
| Main Result | Z(G) equals the minimum zero forcing set size |
| Example | On a path, one endpoint controls the whole graph |
| Conclusion | To control any network, find its zero forcing set |

Reading the slide titles of a good talk, in order, should tell you the complete story.

**Text:**
- Body text: ≥ 24pt font. If it's smaller, no one in the back row can read it.
- Prefer bullet points with 5–7 words each, not full sentences.
- Never read your slides aloud verbatim. The slides are the skeleton; your words are the flesh.

**Figures:**
- Every abstract definition should have a figure.
- Every figure should have a label or caption.
- Use color sparingly and consistently (in this program: blue = blue vertex, white circle = white vertex, always).
- Black and white must work as a fallback.

**Recommended slide count:** Roughly 1 slide per minute. For a 12-minute talk: 10–14 slides.

**Slide order:**
1. Title slide (your name, topic, date, institution)
2. Hook slide (the question or puzzle)
3. Setup slides (definitions + examples)
4. Result slides (theorem / exploration)
5. Connections / open problems
6. Closing slide (your one-sentence takeaway — not "Thank you" or "Questions?")
7. Backup slides (proofs, extra examples, answers to anticipated Q&A questions)

---

### What a Slide Should Look Like

The contrast below illustrates the cardinal rule in practice. The BAD slide tries to be a document; the GOOD slide is a single visual argument.

**BAD slide** — too much text, no figure, font too small:

```
╔══════════════════════════════════════════════╗
║  ZERO FORCING SETS: DEFINITION AND EXAMPLES ║
╠══════════════════════════════════════════════╣
║  • A zero forcing set S is a subset of V(G) ║
║    such that when S is colored blue and the ║
║    color change rule is applied repeatedly, ║
║    eventually all vertices of G become blue. ║
║  • The color change rule states that a blue ║
║    vertex with exactly one white neighbor   ║
║    forces that neighbor to become blue.     ║
║  • We define Z(G) = min|S| over all zero     ║
║    forcing sets S of G.                      ║
║  • Examples: Z(Pₙ)=1, Z(Cₙ)=2, Z(Kₙ)=n-1  ║
║  • Proof: consider vertex v with deg(v)=1... ║
╚══════════════════════════════════════════════╝
Font: 12pt. Five bullet points. No figure. Dense text.
```

**GOOD slide** — one idea, one figure, one equation:

```
╔══════════════════════════════════════════════╗
║  One endpoint controls the whole path        ║
╠══════════════════════════════════════════════╣
║                                              ║
║   ● ─── ○ ─── ○ ─── ○ ─── ○               ║
║   │                                          ║
║   └─ forces ──►  ● ─── ○ ─── ○ ─── ○      ║
║                   │                          ║
║                   └─ forces ──►  etc.        ║
║                                              ║
║   Z(Pₙ) = 1                                 ║
║                                              ║
╚══════════════════════════════════════════════╝
Font: 28pt. One idea. One figure. One equation.
```

The good slide's title is a conclusion. The figure does the explaining. The equation is the payoff. Your spoken words supply all the detail that is missing — and the audience is listening to you, not reading.

---

### Posters

A poster is a different medium from a talk. The audience walks up, glances at your poster, and decides in 5 seconds whether to engage. You then give a 3–5 minute pitch.

**Layout:** Three columns works best for A0 or A1 posters:
- Left column: The problem and motivation
- Middle column: Your main result / exploration
- Right column: Implications, open problems, references

```
┌──────────────────────────────────────────────────────────────────┐
│              TITLE (large font, readable from 3m)                │
│         Your Name • Theory Group • Date                              │
├────────────────────┬──────────────────┬───────────────────────────┤
│   INTRODUCTION     │   MAIN RESULT    │   IMPLICATIONS            │
│                    │                  │                           │
│  • The problem     │  Theorem:        │  • Why it matters         │
│                    │                  │                           │
│  • Why it matters  │  [Figure]        │  • Open questions         │
│                    │                  │                           │
│  [Motivating       │  Key example:    │  • What's next?           │
│   diagram]         │                  │                           │
│                    │  [Figure]        │  [Diagram or table]       │
│  • Background      │                  │                           │
│    definitions     │  Proof sketch:   │  References:              │
│                    │  ...             │  • [1] Author, Year       │
│  [Figure]          │                  │  • [2] ...                │
├────────────────────┴──────────────────┴───────────────────────────┤
│              ~40% white space throughout  │  Acknowledgements     │
└──────────────────────────────────────────────────────────────────┘
```

**Rules:**
- Title: readable from 3 metres (very large font, ≥ 60pt)
- Every section needs at least one figure
- Aim for 40% white space — blank space is not wasted space
- No paragraph of text should be longer than 5 lines

**The pitch:** When someone stops at your poster, deliver a 3-minute verbal summary (your "poster pitch"). This follows the same four-act structure but in 3 minutes instead of 15:
- 20 seconds: the hook question
- 45 seconds: key definition + one example
- 60 seconds: main result + one example
- 30 seconds: why it matters / what's open
- 15 seconds: "Happy to go into more detail — any questions?"

---

## Section 4 — Delivery

### Before the Talk

- Know your first sentence word for word. Say it aloud at least ten times before the talk.
- Know your last sentence word for word. It should arrive cleanly — do not trail off or say "...so, yeah, that's it."
- Run the complete talk in your head (or aloud, alone) at least once.
- Time yourself. A 12-minute talk that runs 18 minutes is a significant problem.

### During the Talk

**Look at your audience.** Look at the slide only to orient yourself, then return to faces. When writing on the whiteboard: write, pause, turn back, then speak.

```
   Presenter                         Audience
      (you)
                     80%
       [P] ════════════════════════► [faces]

        │
        │ 20%
        │
        ▼
     [slide]
   (glance only,
    to orient)
```

Spend 80% of your eye contact on audience faces. Glance at the slide only when you need to point something out or reorient yourself. Speaking to the screen is one of the most common — and most damaging — habits in student presentations.

**Pause intentionally.** After stating a definition or a theorem, pause for 3–5 seconds. It feels like an eternity. To the audience it feels like a respectful moment to absorb what you said.

**Signpost constantly.** Before each new section, tell the audience what's coming:
- "Now that we have the definition, let me show you the main result."
- "Here's the key step in the proof — I'll go slowly."
- "I'll skip the details of this part, but the punchline is..."

**If you lose your place:** Stop. Look at the slide title. Take a breath. Say "So, the key point is..." and continue. The audience will not notice or will not mind.

### Handling Questions

1. **Listen to the full question before answering.** Interrupting to answer what you think is being asked is a common error.
2. **Repeat or rephrase the question** before answering: "So you're asking why the bound is 1/3 rather than 1/2 — great question."
3. **"I don't know"** is always acceptable. Follow with "but my guess is..." or "that's a really interesting direction."
4. **"That's outside what I covered, but briefly..."** handles questions that go beyond your talk without dismissing the questioner.
5. If a question is confusing: **"Could you say a bit more about what you mean?"** buys you time and is always polite.

The diagram below shows the recommended response sequence for any question:

```
   Question asked
        │
        ▼
   Repeat / rephrase ("So you're asking...")
        │
        ▼
   Pause (think — silence is fine here)
        │
        ├─── Know the answer? ──► Answer clearly and concisely
        │
        └─── Don't know? ──► "I don't know, but my guess is..."
                                          │
                                          ▼
                               "That's a great future direction"
```

Never rush straight from hearing the question to giving an answer. The rephrase step confirms you understood, buys thinking time, and ensures the whole room heard the question.

---

## Section 5 — Common Mistakes and How to Avoid Them

| Mistake | Why it happens | Fix |
|---------|----------------|-----|
| Too many definitions at the start | Trying to be thorough | Cut to what is strictly needed for the main result |
| Reading off slides verbatim | Nervousness | Practice without the slides; know the content, not the words |
| Rushing at the end | Running over time | Practice timing; cut slides earlier rather than speeding up |
| No figures | "The maths is in the symbols" | Every abstract object must be drawn at least once |
| Saying "as I mentioned earlier" | Loss of structure | Each slide should stand alone; don't rely on recall |
| Apology ("I'm not sure this is right...") | Imposter syndrome | If you're not sure, either find out or flag it honestly: "I believe this is true but haven't verified it" |
| Ending with "any questions?" as the last slide | Convention | End with your conclusion slide; "any questions?" comes after that slide is up |

---

## Section 6 — Before You Step Up: A Checklist

**Content:**
- [ ] My opening hook is a question or puzzle, not a definition
- [ ] Every definition has an immediate example
- [ ] My main result is stated clearly and the audience knows why it matters
- [ ] I have at least one figure for the main concept
- [ ] My closing sentence is planned word for word
- [ ] I have 2–3 backup slides for likely Q&A questions

**Slides / Poster:**
- [ ] Body text ≥ 24pt; titles ≥ 36pt
- [ ] Slide titles are conclusions, not topic labels
- [ ] All figures are labeled
- [ ] The talk works in black and white
- [ ] Slide count matches time (roughly 1 per minute)

**Delivery:**
- [ ] I have timed myself at least once
- [ ] I know my first sentence by heart
- [ ] I know my last sentence by heart
- [ ] I have practiced the talk at least once out loud

---

## A Note on Mathematical Honesty

One thing distinguishes mathematics from most public communication: in mathematics, you must be precise about what you know and what you don't. In your talk:

- If you have a proof: say so, and give it (or a sketch).
- If you have verified something only for small cases: say "for all small cases I checked."
- If something is an open conjecture: say "we believe this is true, but it has not been proved."
- If you don't know the answer to a question: say "I don't know."

This is not a weakness. It is what makes mathematics trustworthy. Your audience will respect you more for it.


---

[← Centerpoint](centerpoint.md) | [Program Home](../index.md)