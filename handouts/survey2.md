# Research Lab Internship — Background Survey

---

[← Program Home](../index.md) | [Next: Networks Intro →](networks_intro.md)

---

**Name:** \***\*\*\*\*\*\*\***\_\_\_\***\*\*\*\*\*\*\***  
**Date:** \***\*\*\*\*\*\*\***\_\_\_\***\*\*\*\*\*\*\***  
**School / Grade:** \***\*\*\*\*\*\*\***\_\_\_\***\*\*\*\*\*\*\***

_There are no right or wrong answers — partial attempts are welcome. The goal is to understand where you are starting from so we can make this program as useful as possible for you. Spend roughly 30–40 minutes on this._

---

## Part 1 — Mathematical Warm-Up

_Work through as much as you can. Show your reasoning, even if you are not sure of the answer._

**P1.** You have 6 people at a party. Every pair of people either knows each other or does not.

**(a)** How many pairs of people are there in total?

&nbsp;

**(b)** One person (call them Alice) either knows at least 3 others, or doesn't know at least 3 others. Explain why this must be true.

&nbsp;

&nbsp;

&nbsp;

**(c) (Harder)** Use your answer to (b) to argue that among any 6 people, there must be either 3 who all know each other, or 3 who are all mutual strangers. _(Hint: consider the group of 3 that Alice has a common relationship with.)_

&nbsp;

&nbsp;

&nbsp;

&nbsp;

---

**P2.** Consider the sequence of numbers: 3, 1, 4, 1, 5, 9, 2, 6.

**(a)** Find the longest subsequence of this list that is strictly increasing. _(A subsequence does not need to be contiguous — you can skip elements.)_

&nbsp;

&nbsp;

**(b)** The list has 8 numbers. By the [Erdős–Szekeres theorem](sequences_pmi.md), any sequence of more than (r−1)(s−1) distinct numbers must contain either an increasing subsequence of length r or a decreasing one of length s. For r = s = 4, the threshold is 9. Does your answer to (a) agree with what the theorem predicts? Explain.

&nbsp;

&nbsp;

&nbsp;

---

**P3.** Five cities — labeled 1 through 5 — are connected by direct roads as follows: there is a road between 1 and 2, between 1 and 3, between 2 and 4, between 3 and 4, and between 4 and 5. _(This kind of diagram is called a graph or network — see [Handout 2](networks_intro.md).)_

**(a)** Draw a diagram of the cities and roads.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

**(b)** For each city, count how many roads connect directly to it.

| City | Number of roads |
| ---- | --------------- |
| 1    |                 |
| 2    |                 |
| 3    |                 |
| 4    |                 |
| 5    |                 |

**(c)** Add up all the counts in part (b). Can you explain why the total must always be even, regardless of how the roads are arranged?

&nbsp;

&nbsp;

&nbsp;

**(d)** A rumor starts in city 5. The spreading rule is: _if a city has heard the rumor and has exactly one neighboring city that hasn't heard it yet, it immediately tells that neighbor._ Trace which cities eventually hear the rumor, and in what order.

&nbsp;

&nbsp;

&nbsp;

---

**P4.** Prove or disprove: the sum of the first n positive integers equals n(n+1)/2.

_You may use any method — induction, a visual/geometric argument, or algebra. Show your work._

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

---

**P5 (Challenge — skip if short on time).** Suppose you place 5 points anywhere inside a 2×2 square (points may be on the boundary).

**(a)** Divide the square into four 1×1 sub-squares. Explain why at least two of the 5 points must lie in the same sub-square (or on its shared boundary).

&nbsp;

&nbsp;

&nbsp;

**(b)** Two points inside a 1×1 square are at most how far apart? _(The diagonal of a 1×1 square has length √2 ≈ 1.41.)_ What does this, combined with (a), tell you?

&nbsp;

&nbsp;

&nbsp;

**(c)** What happens if you use 9 points inside a 2×2 square instead of 5? Can you guarantee an even smaller maximum distance between some pair of points? Explain.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

---

## Part 2 — Algorithms and Computing

**6.** Do you have any programming experience?

☐ None ☐ A little (school or tutorials) ☐ Moderate (own projects) ☐ Confident

If yes, languages / tools you have used: ************\_\_\_************

---

**7.** Here is a procedure described in plain English. No programming knowledge is needed — just follow the steps carefully. _(You can try this interactively at [🎮 Sequences Demo](../interactive/sequences.html).)_

> **Card-piling procedure.** You are given a list of numbers, one at a time. You have a row of piles in front of you (initially empty). For each new number:
>
> - Look at the top of each pile from left to right.
> - Place the number on top of the **first** pile whose top number is **greater than or equal** to the new number.
> - If no such pile exists, start a **new pile** on the right with just this number.

**(a)** Apply this procedure to the sequence: **3, 1, 4, 1, 5**. Show what the piles look like after each number is placed.

| After placing | Piles (left → right, top number shown) |
| ------------- | -------------------------------------- |
| 3             |                                        |
| 1             |                                        |
| 4             |                                        |
| 1             |                                        |
| 5             |                                        |

**(b)** How many piles do you end up with? How does that number compare to the longest increasing subsequence you found in P2(a)?

&nbsp;

&nbsp;

**(c)** Write out in your own words — as a numbered list of steps — how you would find the **largest** number in a list, if you can only look at one number at a time. Assume you have no way to remember more than one number at a time beyond what you write down.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

**(d) (Only if you have programming experience)** Write your procedure from (c) as code in any language you know.

&nbsp;

&nbsp;

&nbsp;

&nbsp;

---

## Part 3 — Research Thinking

**9.** Have you ever read a research paper (in any field)? ☐ Yes ☐ No

If yes, describe it briefly. What was the hardest part to understand?

&nbsp;

&nbsp;

&nbsp;

**10.** What is the difference between a problem that _no one has solved yet_ and a problem that _you personally haven't seen before_? Why does this distinction matter in research?

&nbsp;

&nbsp;

&nbsp;

**11.** Suppose you spend two hours trying to prove something and fail completely. What do you do next?

&nbsp;

&nbsp;

&nbsp;

**12.** In a 4-person group project involving: reading papers, running experiments / writing code, synthesizing results into a proof or argument, and designing a presentation — which role do you naturally take on? Which would you _like_ to get better at during this program?

&nbsp;

&nbsp;

&nbsp;

**13.** Is there an open mathematical or computational question — something no one knows the answer to — that you find genuinely interesting? It does not have to be famous. Describe it.

&nbsp;

&nbsp;

&nbsp;

---

## Part 4 — Goals and Self-Assessment

**14.** Which of the following best describes what you want most from this internship? _(Rank 1–4, with 1 being most important)_

**_ Getting a taste of what research actually feels like day-to-day  
_** Learning specific mathematical content I couldn't get in school  
**_ Building a project I can show to universities or employers  
_** Finding out whether I want to pursue mathematics or CS further

**15.** Where do you feel least prepared coming into this program? Be specific.

&nbsp;

&nbsp;

&nbsp;

**16.** By the end of this program, what would make you feel the four weeks were well spent?

&nbsp;

&nbsp;

&nbsp;

---

_Thank you._

---

[← Program Home](../index.md) | [Next: Networks Intro →](networks_intro.md)
