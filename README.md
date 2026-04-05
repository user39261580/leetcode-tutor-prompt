<div align="center">

# 🧠 LeetCode Interview Tutor Prompt

**A carefully engineered system prompt that turns any capable LLM into a Socratic coding interview tutor**

[![Version](https://img.shields.io/badge/version-2.0-blue?style=flat-square)](./CHANGELOG.md)
[![Primary Language](https://img.shields.io/badge/prompt-English%20(canonical)-black?style=flat-square)](./prompts/en/leetcode-tutor.md)
[![Output Language](https://img.shields.io/badge/output-Traditional%20Chinese%20(zh--TW)-red?style=flat-square)](#-language-architecture)
[![Compatible](https://img.shields.io/badge/LLM-GPT%20%7C%20Claude%20%7C%20Gemini%20%7C%20Perplexity-green?style=flat-square)](#-quick-start)
[![License](https://img.shields.io/badge/license-MIT-lightgrey?style=flat-square)](./LICENSE)

*From memorizing solutions to truly owning them — guided by the Socratic method, one problem at a time.*

[**→ Get the Prompt**](./prompts/en/leetcode-tutor.md) · [Example Walkthrough](./examples/best-time-to-buy-and-sell-stock-demo.md) · [Changelog](./CHANGELOG.md) · [繁體中文版](./prompts/zh-TW/leetcode-tutor.md)

</div>

---

## Background

This prompt started as a personal tool.

I came to the University of Washington (UW) as an international student and started applying for software engineering internships. Like most people going through this, I was grinding LeetCode — but I kept running into the same frustration: I could memorize a solution and still fail the next problem of the same type.

I wanted something that would teach me **how to think**, not just what to type. So I built a system prompt that acts as a patient, Socratic tutor: gives you the full picture of a problem first, then walks through the reasoning with you rather than handing you the answer.

A few weeks in, some classmates asked to try it. The feedback was good enough that I iterated on it, added new modes based on how actual study sessions went, and eventually put it on GitHub in case it's useful to others going through the same preparation.

---

## What This Is

A **system prompt** — paste it into your preferred AI chatbot as a persistent system instruction, then just name any LeetCode problem to start a session.

> **Core philosophy:** The goal is not to solve LeetCode problems. The goal is to understand them so deeply that you can solve problems you've never seen before.

---

## Key Features

### 📋 Structured First Response — Every New Problem

Before any back-and-forth begins, every new problem gets a consistent, scannable overview:

| Section | Purpose |
|---------|---------|
| 📋 **Problem Analysis** | Input/output rules, core concepts, and interview importance rating |
| 🛠️ **Core Algorithms & Data Structures** | What techniques apply and why |
| 🎯 **Solution Strategies & Comparison Table** | Brute force → optimal, with complexity tradeoffs side-by-side |
| 🔗 **Related Problems & Extensions** | Learning path and follow-up problems worth trying |
| ⚠️ **Common Mistakes & Pitfalls** | Edge cases and frequent errors, named explicitly |

### 🔑 One-Sentence Key Takeaway

After solving, the tutor distills the solution into a single memorable sentence — a retrieval cue designed to resurface in a real interview.

> *Two Sum:* "Use a Hash Map to store the needed complement `(target - current_value)` as you iterate, allowing O(1) lookups — don't search for the answer, set up the wall so the answer walks into it."

### ⚡ Smart Mode Switching

| Scenario | Behavior |
|----------|----------|
| **Brute force is obvious** | Acknowledges it in one line, pivots straight to optimization |
| **Interview recap / "I know this one"** | Suspends Socratic mode; delivers fast-track overview + prompts you to recall the key takeaway |
| **Student is stuck** | Breaks the step into sub-problems; uses analogies and minimum-necessary hints |

### 🗣️ Four-Phase Socratic Teaching Flow

1. **Understanding & Pattern Recognition** — Connect the problem to known patterns before touching code
2. **Solution Strategy Development** — You lead; the tutor steers toward optimization
3. **Implementation Guidance** — Pseudocode first, then line-by-line walkthrough
4. **Testing, Reflection & Transfer** — Edge cases, complexity review, and what to practice next

---

## Quick Start

### Step 1 — Copy the Prompt

Open [`prompts/en/leetcode-tutor.md`](./prompts/en/leetcode-tutor.md) and copy the content inside the code block.

### Step 2 — Set It Up

Paste it into the persistent system instruction field of your chosen platform:

| Platform | Where to Set the System Prompt |
|----------|-------------------------------|
| **ChatGPT** | Create a **Project** → **Project Settings** → **Instructions** |
| **Claude** | Create a **Project** → **Instructions** |
| **Gemini** | Create a **Gem** → **Instructions** |
| **Perplexity** | Create a **Space** → **Add Instructions** |

> Using Projects / Gems / Spaces (rather than one-off custom instructions) means the tutor persona persists across all conversations in that context. You don't need to re-paste the prompt every time you open a new chat.

### Step 3 — Start a Session

```
[Attach the screenshot of the question description]
Teach me Two Sum (#1)
I want to review all Binary Search variations
Help me prepare for Sliding Window problems
Interview recap mode: Merge Intervals
```

---

## How This Compares to Similar Prompts

There are existing prompts that do related things. The most prominent:

- **[LeetCodeGPT](https://www.reddit.com/r/ChatGPTPro/comments/12yvjm4/leetcodegpt_prompt/)** (Reddit, 2023) — An early popular prompt focused on interview simulation: the AI poses a problem and waits for a solution, then gives direct feedback. Primarily tests you; does not guide the reasoning process.
- **[ai-boost/awesome-prompts](https://github.com/ai-boost/awesome-prompts)** — A collection of general-purpose prompts including some coding-adjacent ones, without structured pedagogical phases or a dedicated tutor persona.

**What this prompt does differently:**

| Feature | Typical LeetCode Prompts | This Prompt |
|---------|--------------------------|-------------|
| First response structure | Unstructured, varies | Fixed 5-section overview every time |
| Teaching approach | Direct answer or simulation | Socratic — never gives the answer directly |
| Post-solution summary | None | One-sentence key takeaway for long-term recall |
| Mode adaptation | Single mode | Smart switching based on context |
| Complexity comparison | Rarely included | Mandatory side-by-side table for every problem |
| Related problem mapping | Rarely included | Explicit LeetCode problem numbers with learning path |

The most distinctive decision is the **structured first response**. Most tutor prompts jump straight into Socratic dialogue, which is disorienting without a mental map of the problem. This prompt always delivers the landscape view first.

---

## Design Notes & References

**Why a structured first response?**
Inspired by how good textbook chapters are organized: overview and motivation before the deep dive. Without it, AI tutors tend to either ask too many clarifying questions before providing useful context (frustrating) or jump straight to code without building conceptual foundations (shallow learning). The fixed 5-section format ensures the student always has a complete mental map before interactive exploration begins.

**Why the one-sentence takeaway?**
Drawing from research on spaced repetition and retrieval cue theory: a well-formed retrieval cue significantly outperforms re-reading full solutions for long-term retention. The one-sentence takeaway is designed as that cue — short enough to internalize, precise enough to reconstruct the full approach from.

**Why four phases instead of six?**
The original v1.0 had six phases. In practice, "Comprehension" and "Pattern Recognition" always happened together — artificially separating them created a checkpoint that interrupted natural dialogue flow. Four phases match how sessions actually unfold.

**Academic references:**
- *"Prompting Large Language Models With the Socratic Method"* — arXiv:[2303.08769](https://arxiv.org/pdf/2303.08769.pdf) (2023)
- *"The Socratic Method for Self-Discovery in Large Language Models"* — Princeton NLP / [SocraticAI](https://princeton-nlp.github.io/SocraticAI/) (2023)
- *"Teach AI How to Code: Using LLMs as Teachable Agents for Programming Education"* — arXiv:[2309.14534](https://arxiv.org/pdf/2309.14534.pdf) (2024)

---

## Repository Structure

```
leetcode-tutor-prompt/
│
├── README.md                          ← You are here
├── CHANGELOG.md                       ← Version history & design decisions
├── LICENSE                            ← MIT
│
├── prompts/
│   ├── en/
│   │   └── leetcode-tutor.md         ← ✅ English — canonical version (use this)
│   └── zh-TW/
│       └── leetcode-tutor.md         ← 🇹🇼 Traditional Chinese — localized translation
│
└── examples/
    └── best-time-to-buy-and-sell-stock-demo.md  ← Full interaction walkthrough (LeetCode #121)
```

---

## Contributing

Found a scenario the prompt handles poorly? Have a suggestion?

1. Open an **Issue** describing the scenario and expected vs. actual behavior
2. Or submit a **PR** with your proposed change and the reasoning behind it
3. Include an example interaction demonstrating the difference

---

## License

MIT — use, adapt, and build on this freely for personal or educational purposes.

---

<div align="center">

*Built at UW during internship prep. Refined with classmate feedback. Shared for anyone grinding through the same process.*

</div>
