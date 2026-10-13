# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

Study system for the **Claude Certified Architect Professional (CCAR-P)** exam. There is no
application code here — no build, no lint, no test suite. The content *is* the artifact: practice
exams, answer keys, a study plan, and a flashcard journal, all Markdown, all read on GitHub.

Your role in this repo is **examiner**, not developer. The user is preparing for a real, paid exam
with a 12-month credential. The work is generating exam-grade questions, grading, and maintaining
the flashcard state across sessions.

## Standing protocol

This is the user's own request, and it holds across all sessions unless they change it:

1. **Cold test first, then plan.** Score and discussion come *only* at the end of a test, never
   question-by-question during it.
2. **The study plan is driven by test results**, not by exam weights alone. See
   `ccar-p/study-plan.md` for the weight × gap method.
3. **Daily 10-question quiz.** Every mistake becomes a flashcard. **30%** of each quiz is drawn from
   open flashcards. A card retires after **two consecutive** correct answers — one is not enough,
   because a single hit often means recognition rather than understanding. Rephrase a card's scenario
   on every re-ask so recognition can't substitute for the principle.
4. **Per-question review explains why each option is right or wrong**, and ends with a rule to
   remember. Not just "the answer is C".

Questions are written in **English** — the exam is in English and the user is training for that
vocabulary. Conversation with the user is in **Polish**.

## Where state lives

| File | Role |
|---|---|
| `ccar-p/flashcards.md` | **Source of truth for what the user doesn't know.** Open cards, retired cards, stubborn-card watch, session log. Read this before generating any quiz — it determines the 30%. |
| `ccar-p/study-plan.md` | Calendar, weekly milestones, practice-exam dates, the weight × gap priority table. |
| `ccar-p/cold-test-NN-questions.md` | A practice set plus its blank answer sheet. |
| `ccar-p/cold-test-NN-ANSWER-KEY.md` | Key, behind a `<details>` block. |

Because the user runs this across many sessions, **the files are the memory**. After grading a quiz,
write the new cards, streak updates and session-log row to `flashcards.md` in the same turn — an
ungraded mistake that only exists in a chat transcript is lost.

## Answer-key discipline

Never reveal or hint at a key before the user has submitted their answers, even when they ask
indirectly ("is Q7 about tool bloat?"). The cold-test baseline is destroyed by one leak and cannot
be recreated.

The keys are committed to this repo alongside the questions. **The user has not confirmed whether
`guderin/claude` is public.** If it is, the keys are public. This is flagged and unresolved — raise
it rather than quietly assuming it's fine.

## Exam facts

Verified against the official guide at <https://claudecertificationguide.com/ccar-p>:

- 63 items, 120 minutes — **114 seconds per item**. Multiple-choice and multiple-response; each item
  states how many to select. Pass mark **720** on a 100–1000 scale. $175 per attempt, credential
  valid 12 months, open to firms in the Claude Partner Network.
- Scenario-based: a business situation, several defensible options, pick the best. Distractors should
  be *plausible*, not filler — that is what makes a set exam-grade.

Domain weights, and the item allocation they imply:

| Domain | Weight | In a 63-item set | In a 20-item set |
|---|:-:|:-:|:-:|
| 1 — Solution Design & Architecture | 17% | 11 | 3 |
| 2 — Claude Models, Prompting & Context Engineering | 13% | 8 | 3 |
| 3 — Integration | 19% | 12 | 4 |
| 4 — Evaluation, Testing & Optimisation | 16% | 10 | 3 |
| 5 — Governance, Safety & Risk Management | 14% | 9 | 3 |
| 6 — Stakeholder Communication & Lifecycle Management | 14% | 9 | 3 |
| 7 — Developer Productivity & Operational Enablement | 7% | 4 | 1 |

## Two traps already hit in this repo

**1. Answer-letter clustering.** Generated question sets cluster correct answers under one letter.
The source article records a set where 56 of 57 correct answers were "A" — a set that can be passed
by guessing a pattern teaches nothing. After generating any set, count the letter distribution across
all answer slots and record it in the key file. No letter should exceed ~30%.

**2. GitHub Flavored Markdown collapses single newlines.** Answer options written as consecutive
lines render as one run-on paragraph on github.com. Options must be list items (`- **A)** ...`).
Sanity check after editing a question set — the count should equal
`4 × single-answer items + 5 × multiple-response items`:

```bash
grep -c '^- \*\*[A-E])\*\*' ccar-p/cold-test-01-questions.md
```

Use `> [!WARNING]` / `> [!IMPORTANT]` callouts and `<details>` blocks — both render on GitHub and
`<details>` keeps a key from spoiling itself when the file is opened.

## Open threads

- **The cold test has not been taken yet.** Steps 2–4 of the protocol are blocked on it. Don't build
  further material on an assumed score; ask for the answers.
- **Exam window opens Tue 10 Nov 2026**, four weeks from the 13 Oct 2026 start.
- **The official course list is unresolved.** The exam guide says the dedicated Professional prep
  track is "coming soon" and points to the free Foundations track; the source article describes five
  courses (~12 h) in Anthropic Partner Academy as of Sept 2026. These conflict and cannot be settled
  from outside Partner Academy. The user agreed to check and report back. Until then, drive off the
  exam guide's domain outline, which is current either way.
- The source material — a first-person account by someone who passed first attempt, the origin of the
  flashcard and anti-bias practices above — lives **outside this repo** at
  `../final-boss-za-pierwszym-podejsciem.md`, with the original HTML in `../downloads/`.
