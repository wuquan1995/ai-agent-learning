# 24-Week Roadmap Migration Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the repository’s 36-week, five-hours-per-week learning plan with the approved 24-week, ten-hours-per-week roadmap.

**Architecture:** Update the dashboard, canonical roadmap, and active backlog together so every public entry point agrees on the time budget, phase boundaries, and first milestone. The backlog is deliberately reduced from eight to four weeks because Phase 1 is compressed while retaining all foundational concepts.

**Tech Stack:** Markdown, Git, GitHub SSH remote.

## Global Constraints

- Study budget: approximately 10 hours each week; total approximately 240 hours.
- The curriculum remains principles-first and hand-built before framework use.
- Python remains the Agent runtime and service language.
- LangGraph is introduced only in Weeks 17–19, after hand-built Agent and RAG work.
- The Week 4 milestone is an observable Python CLI assistant.

---

## File Structure

- `README.md` — public dashboard: duration, weekly rhythm, phase status, and milestones.
- `docs/roadmap.md` — canonical six-phase, 24-week curriculum.
- `docs/backlog.md` — active four-week Phase 1 task board.
- `docs/superpowers/plans/2026-07-27-migrate-to-24-week-roadmap.md` — implementation checklist.

### Task 1: Update the dashboard and canonical roadmap

**Files:**
- Modify: `README.md`
- Modify: `docs/roadmap.md`

**Interfaces:**
- Consumes: `docs/superpowers/specs/2026-07-27-24-week-learning-roadmap-design.md`.
- Produces: consistent public statements of 24 weeks, 10 hours/week, and six phase ranges.

- [x] **Step 1:** Change README’s learning commitment to 24 weeks, 10 hours/week, and 240 hours total.
- [x] **Step 2:** Replace the 2h/2h/1h table with 3h principles, 5h implementation/testing, 1h evaluation, and 1h review.
- [x] **Step 3:** Replace README milestone ranges with 1–4, 5–10, 11–16, 17–19, 20–21, and 22–24.
- [x] **Step 4:** Rewrite the roadmap’s six headings and outputs using those same ranges; make Week 4 the observable CLI assistant milestone.
- [x] **Step 5:** Run:

```bash
rg -n "36 周|5 小时|180 小时|Weeks (25|29|33)" README.md docs/roadmap.md
```

Expected: no output.

### Task 2: Replace the Phase 1 board and verify consistency

**Files:**
- Modify: `docs/backlog.md`
- Modify: `docs/superpowers/plans/2026-07-27-migrate-to-24-week-roadmap.md`

**Interfaces:**
- Consumes: the 3h/5h/1h/1h weekly rhythm and Week 4 CLI milestone.
- Produces: four weekly tasks covering all phase-one foundations.

- [x] **Step 1:** Replace the eight weekly sections with four sections: Python + HTTP boundary, message/context + observation, structured output + tools + injection boundary, and observable CLI assistant.
- [x] **Step 2:** Give every week exact 3h reading, 5h implementation/testing, 1h evaluation, and 1h review work.
- [x] **Step 3:** Set Week 4’s completion standard to a reproducible CLI assistant that records inputs, outputs, latency, token/cost estimates, tool events, and a failure trace.
- [x] **Step 4:** Run:

```bash
test "$(rg -c "^## Week [1-4]" docs/backlog.md)" -eq 4
! rg -n "^## Week [5-9]" docs/backlog.md
rg -n "3 小时|5 小时|1 小时" docs/backlog.md
git diff --check
```

Expected: exit status 0.

- [x] **Step 5:** Mark completed checklist items in this plan, commit, and push:

```bash
git add README.md docs/roadmap.md docs/backlog.md docs/superpowers/plans/2026-07-27-migrate-to-24-week-roadmap.md
git commit -m "docs: migrate learning roadmap to 24 weeks"
git push
```

## Self-Review

- Spec coverage: Tasks 1–2 update every document named in the design’s repository-change scope and preserve all six approved phases.
- Placeholder scan: no TBD/TODO text or unspecified week ranges.
- Consistency: README, roadmap, and backlog use the same 10-hour weekly budget; roadmap and README use matching phase ranges.
