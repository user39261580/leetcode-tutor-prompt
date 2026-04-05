# Changelog

All notable changes are documented here, including the reasoning behind each design decision.

---

## [v2.0] — 2026 Q1

### The "Classmate Feedback" Update

After sharing v1.1 with classmates at UW who were also applying for internships, the most consistent feedback was:

> *"The structured overview is great — but after I've reviewed a problem once, I don't want the full Socratic walkthrough again. I just need a quick memory check."*

This led to the two biggest additions in v2.0.

### Added
- **🔑 "One-Sentence" Key Takeaway** — A condensed mnemonic triggered after the student reaches the optimal solution. Inspired by retrieval cue theory: a well-formed cue dramatically improves long-term recall compared to re-reading full solutions.
- **⚡ Special Scenario A: Trivial Brute Force** — Skips unnecessary brute-force walkthrough when the approach is obvious (e.g., O(N²) nested loops). Pivots directly to optimization. Added after feedback that explaining obvious solutions felt condescending.
- **⚡ Special Scenario B: Interview Recap Mode** — Fully suspends the Socratic method for rapid review. Designed for the "30 minutes before an interview" scenario.

### Changed
- Teaching phases restructured from 6 → 4. "Comprehension" and "Pattern Recognition" merged — they always happened together naturally, and splitting them created an artificial checkpoint that disrupted flow.
- Solution comparison table simplified from 7 columns → 5 (removed "Difficulty" and "Use Case") for faster readability.
- Emoji section markers added for visual navigation.

---

## [v1.1] — 2025 Q3

### The "Bilingual" Update

### Added
- Full Traditional Chinese (zh-TW) translation of the system prompt.
- Explicit language output directive elevated to `CRITICAL` level after noticing models would sometimes default to Simplified Chinese or mix languages unpredictably.

---

## [v1.0] — 2025 Q2

### Initial Release

Built during the first semester at UW as a personal tool for internship prep. The core insight:

> Most LeetCode AI tools either hand you the answer (useless for learning) or ask too many questions before providing context (frustrating). The goal was a middle path: full mental map first, guided reasoning second.

- Core Socratic methodology established.
- 6-phase teaching flow: Comprehension → Pattern Recognition → Strategy → Implementation → Testing → Reflection.
- Fixed 5-section first-response format.
