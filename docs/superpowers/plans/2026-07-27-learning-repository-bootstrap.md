# AI Agent Learning Repository Bootstrap Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Create the first publishable version of a principles-first AI Agent learning repository for five hours of study each week.

**Architecture:** Markdown-first repository: README is the dashboard, a roadmap defines the 36-week sequence, and a backlog turns the current phase into weekly commitments. No framework scaffold is introduced before model and agent fundamentals.

**Tech Stack:** Markdown, Git, GitHub SSH remote.

## Global Constraints

- Study budget: approximately five hours each week.
- Principles and hand-built implementations precede framework APIs.
- Python is the language for exercises.
- All initial content renders directly on GitHub without a build step.

---

## File Structure

- `README.md` — project dashboard and navigation.
- `docs/roadmap.md` — 36-week curriculum.
- `docs/backlog.md` — first eight issue-ready weekly tasks.
- `docs/superpowers/plans/2026-07-27-learning-repository-bootstrap.md` — this plan.

### Task 1: Create the dashboard and roadmap

**Files:**
- Create: `README.md`
- Create: `docs/roadmap.md`

**Interfaces:**
- Consumes: the five-hour weekly limit and the approved principles-first sequence.
- Produces: the GitHub entry point and a linked roadmap.

- [x] **Step 1:** Write the README with goal, 2h/2h/1h weekly rhythm, weeks 1–8 current phase, and links to roadmap/backlog.
- [x] **Step 2:** Write the roadmap: Python + LLM interface (1–8), single agent (9–16), RAG (17–24), workflows/framework mapping (25–28), multi-agent systems (29–32), production/portfolio (33–36).
- [x] **Step 3:** Run `rg "docs/(roadmap|backlog)\\.md" README.md`; expected: both links are returned.
- [x] **Step 4:** Commit:

```bash
git add README.md docs/roadmap.md
git commit -m "docs: add AI Agent learning roadmap"
```

### Task 2: Create the phase-one backlog and publish it

**Files:**
- Create: `docs/backlog.md`
- Modify: `README.md`

**Interfaces:**
- Consumes: phase-one outcomes in `docs/roadmap.md`.
- Produces: eight weekly tasks that can be converted to GitHub Issues or a Project board.

- [x] **Step 1:** Write eight weekly tasks, each with a two-hour reading target, two-hour implementation target, and one-hour review target.
- [x] **Step 2:** Cover Python environment, HTTP/JSON, LLM message semantics, token/cost observation, structured output, tool contracts, prompt-injection boundaries, and a small CLI assistant.
- [x] **Step 3:** Add a “This week” pointer to `docs/backlog.md` in README.
- [x] **Step 4:** Run `rg "^## Week [1-8]" docs/backlog.md | wc -l`; expected: `8`.
- [ ] **Step 5:** Commit and publish:

```bash
git add README.md docs/backlog.md
git commit -m "docs: add phase one weekly backlog"
git push -u origin main
```

## Self-Review

- Spec coverage: weekly capacity, principles-first sequence, Python choice, 36-week roadmap, and phase-one tasks are all covered.
- Placeholder scan: no `TBD` or `TODO` markers.
- Type consistency: not applicable to documentation-only bootstrap.
