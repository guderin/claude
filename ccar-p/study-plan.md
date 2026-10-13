# CCAR-P — 4-week study plan

| | |
|---|---|
| **Start** | Tue 13 Oct 2026 |
| **Last study day** | Mon 9 Nov 2026 |
| **Exam window opens** | Tue 10 Nov 2026 |
| **Budget** | ~18 h over 28 days — roughly 40 min on weekdays, 1.5 h on weekend days |
| **Reference point** | The source article: ~15 h over 24 days, passed first attempt |

> [!IMPORTANT]
> **Domain priority is not yet set.** It comes from the cold test, which has not been taken yet.
> Sit [`cold-test-01-questions.md`](./cold-test-01-questions.md) first; the priority table below
> gets filled from the result.

---

## How priority is decided

Not by raw score. By **exam weight × gap**, because a 10-point gap in Integration (19% of the exam)
costs nearly three times what the same gap costs in Developer Productivity (7%).

| Domain | Weight | Cold-test score | Gap to 90% | Weight × gap | Rank |
|---|:-:|:-:|:-:|:-:|:-:|
| 3 — Integration | 19% | — | — | — | — |
| 1 — Solution Design & Architecture | 17% | — | — | — | — |
| 4 — Evaluation, Testing & Optimisation | 16% | — | — | — | — |
| 5 — Governance, Safety & Risk | 14% | — | — | — | — |
| 6 — Stakeholder Communication & Lifecycle | 14% | — | — | — | — |
| 2 — Models, Prompting & Context | 13% | — | — | — | — |
| 7 — Developer Productivity & Enablement | 7% | — | — | — | — |

With only 3–4 items per domain, a single cold-test result is a noisy signal. Treat the ranking as a
starting hypothesis and let the daily quizzes correct it — a domain that keeps generating flashcards
is weak regardless of what it scored on day one.

---

## Weekly structure

### Week 1 · Tue 13 – Mon 19 Oct — close the two biggest gaps

The two top-ranked domains only. Resist breadth this week.

- Sit the cold test, grade it, fill in the priority table.
- Work through the prep course covering rank-1 domain, then rank-2.
- Daily quiz from day two onward.
- **Exit criterion:** both domains at 85%+ on their own topic quizzes.

### Week 2 · Tue 20 – Mon 26 Oct — ranks 3–4, then measure

- Prep material for rank-3 and rank-4 domains.
- **Milestone: Practice Exam 02**, full 63 items, 120 min, timed, closed book. Saturday 24 Oct.
- Re-rank the priority table from Practice Exam 02 — this result is far more reliable than the cold
  test, since each domain gets 8–12 items instead of 3.
- **Exit criterion:** Practice Exam 02 above the cold-test total, no domain under 70%.

### Week 3 · Tue 27 Oct – Mon 2 Nov — remaining domains and flashcard burn-down

- Cover the remaining domains, including Developer Productivity (small weight, cheap to close).
- Shift emphasis to the flashcard deck: open cards are now the best map of what you don't know.
- **Milestone: Practice Exam 03**, harder than 02 — ambiguous scenarios where two options are
  defensible and you must pick the best.
- **Exit criterion:** fewer than 8 open flashcards, Practice Exam 03 at 90%+.

### Week 4 · Tue 3 – Mon 9 Nov — train above exam difficulty, then taper

The article's sixth lesson: the real exam was harder than every practice run at 84/92/100/97%.
So this week runs deliberately harder than the target.

- **Milestone: Practice Exam 04**, hardest set, strict timing, no pauses. Early in the week.
- Close every remaining flashcard. A card still open 72 h before the exam gets a dedicated session.
- Logistics, no later than Thu 5 Nov: run the proctoring system check on the exact machine and
  network you'll use — no VPN, not the corporate network. Confirm your ID matches the booking.
- Last two days: light review only. No new material.
- Exam morning: six easy warm-up questions in English before you log in.

---

## Daily cadence

Every day except exam day:

1. **10-question quiz**, in English, exam-style scenarios with decisions.
2. **30% of items drawn from open flashcards** — the deck decides what gets re-asked, not me.
3. Every mistake becomes a flashcard in [`flashcards.md`](./flashcards.md).
4. A card retires after **two consecutive correct answers**, not one.
5. Per-question review explains why each option is right or wrong, and ends with a rule to remember.

---

## Timing discipline

The exam gives you **114 seconds per item**, and the article flags running almost out of time. So
timing is trained, not assumed:

- Weeks 1–2: no clock on daily quizzes. Build accuracy first.
- Week 3 onward: 110 seconds per item on daily quizzes, hard stop.
- All practice exams: full 120 minutes, single sitting, no pauses.
- In-exam rule: answer, flag if unsure, move on. Return to flags at the end — never stall on one item.

---

## Official course material — verify before relying on this

The official exam guide lists the dedicated **Professional** prep track as *"coming soon"* and points
to the free **Claude Certified Architect (Foundations)** track as overlapping material. The source
article describes five courses totalling ~12 h in Anthropic Partner Academy as of September 2026.

These two accounts disagree, and I can't resolve it from outside Partner Academy. **Action for you,
in week 1:** log into Partner Academy, list what's actually published, and tell me. I'll map the real
courses onto the rank order. Until then the plan drives off the exam guide's domain outline, which
is current either way.

Note also: the exam is open to people at firms in the Claude Partner Network, $175 per attempt, pass
mark 720 on a 100–1000 scale, credential valid 12 months. Confirm your firm's eligibility and who
pays the fee in week 1 — not in week 4.
