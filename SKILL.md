---
name: product-research-workflow
description: >
  Trigger when user mentions: 竞品调研 / 产品调研 / 体验报告 / 竞品报告 /
  产品体验 / 调研报告 / good bad 分析 / 产品对比 / 写报告 / 整理发现 /
  给老板看 / 帮我整理今天的发现 / competitive analysis / product research /
  UX report / product review / research report.
  Also trigger when user has raw observations and needs to turn them into
  a structured deliverable for a boss, team, or stakeholder.
  Do NOT trigger for casual conversation, coding tasks, or general writing
  unrelated to PM research deliverables.
---

# Product Research Workflow

A four-phase workflow for PM research tasks that produces high-density, structured reports while respecting the user's natural exploration process.

## Core Philosophy

Three principles shape this entire workflow:

1. **Reports are not thinking diaries.** Thinking process stays with the author; conclusions go to the reader.
2. **Think from the bottom up, but present from the top down.** (Minto Pyramid Principle) Exploration is bottom-up — observe, feel, notice. Presentation is top-down — conclusion first, evidence after.
3. **Judgment earns value through evidence, not phrasing.** "Very clever design" without evidence is not judgment — it's decoration.

Every tool in this skill exists to serve one of these three principles.

## When to Use

Trigger this skill for any task involving:
- Competitive analysis / 竞品调研
- Product experience reports / 产品体验报告
- User research synthesis
- Product iteration planning
- Market scanning reports
- Any task where raw observations need to become a structured deliverable for stakeholders

Do **not** use for:
- Casual thinking aloud without intent to produce a report
- Personal learning notes
- Technical documentation (use docs skill)

## The Four-Phase Workflow

### Phase 0 · Task Contract (目标对齐)

**Before any exploration begins**, produce a Task Contract together with the user. This is the anchor that prevents goal drift.

The contract has 7 sections — read `references/task-contract.md` for the full template. The essentials:

1. **Verbatim quote** of the boss's / stakeholder's request. Paste the exact words.
2. **MECE breakdown** into specific deliverables (D1, D2, D3...) with priority (P0/P1/P2).
3. **Definition of Done** — 3-5 checkable success criteria that a stranger could use to judge completion.
4. **Implicit constraints** — audience, context, time budget, downstream use.
5. **Drift guards** — warning signals to watch for during exploration.
6. **Phase checkpoints** — what to verify at the end of each phase.
7. **Contract boundaries** — when extending the contract is OK, when it isn't.

**Output of Phase 0**: A written contract file (markdown). Save it and refer back to it at every phase transition.

### Phase 1 · Felt Exploration (感受式探索)

**Role split**: User explores freely; Claude records and guards boundaries.

**Claude MUST**:
- Record observations faithfully, using the user's own words
- **NOT interrupt** the user's natural exploration rhythm
- **NOT add judgments** — only capture what the user says and sees
- Offer structured format for each observation:
  ```
  Time | Scene | Fact observed | Feeling | Question it raises
  ```
- Only gently ask about dimensions from the contract that haven't been covered — do not push for comprehensiveness at the expense of depth
- Accept that observations will be rough, emotional, and low-density — this is normal and correct for Phase 1

**Claude MUST NOT**:
- Add conclusions, judgments, or "syntheses" proactively
- Say things like "this is an interesting pattern" or "this suggests X"
- Reframe the user's raw observations into prettier language
- Interrupt deep dives the user is engaged in

**Output of Phase 1**: A raw observation log. Low density is expected. This is a work-in-progress document, not a deliverable.

### Phase 2 · Classification & Verification (分类验证)

**Role split**: User is judge; Claude is lawyer + evidence investigator.

Present **every observation** from Phase 1 back to the user (complete, unmodified). Classify each into three buckets:

| Bucket | Criteria | Treatment |
|--------|----------|-----------|
| 🟢 Green · Fact | Observed personally + screenshot evidence exists | Keep as fact, no annotation needed |
| 🟡 Yellow · Personal Observation | User's feeling, reasoning, analogy, or inference | Keep but mark with 【个人观察】 |
| 🔴 Red · External Claim to Verify | Claim about external fact (funding, tech stack, industry practice, competitor internals) | **Must** web_search verify before keeping |

**Red bucket processing**:
- Claude actively runs web_search to verify
- Verified → upgrade to Green
- Not verified → downgrade to Yellow (【个人推测·未经核实】) or delete
- Contradicted → delete

**Critical rule**: Never let a Red claim into the report without verification. This was the main failure mode the skill was designed to fix.

**Output of Phase 2**: A classified, evidence-validated observation set.

### Phase 2.5 · Outline Preview (大纲预览)

**Do not skip this step.** Writing HTML directly from Phase 2 results causes massive rework.

Produce a **text-only outline** (not HTML) containing:
- Section titles
- What each section will say (1-2 sentences)
- Which user observations feed each section
- What figures/screenshots go where
- Approximate length per section
- Tone/voice for the section

Then:
1. **MECE self-check** — read `references/pyramid-principle.md` for the checklist
2. **Contract cross-check** — every D from the contract must have a corresponding section
3. **Distinction call** — for each observation, decide: does this go in the report, or in the self-archive?

**Get user approval on the outline before Phase 3.** Iterate if needed. It's 10× cheaper to fix structure at outline stage than HTML stage.

### Phase 3 · Drafting (成文)

Now write the report.

**Structure choice**: Select a template from `references/report-templates.md` based on task type:
- Competitive analysis → Template A
- User research → Template B
- Product iteration → Template C
- Market scanning → Template D
- Product experience → Template E

**Writing rules**: Read and apply all 10 rules from `references/writing-rules.md`. The critical ones:
- **Lead with conclusion** — first 3 lines of every section must be the conclusion
- **Structured language** — bullets and short phrases, not long sentences
- **Evidence mandatory** — every claim needs a screenshot, data point, or quote
- **Dual figures** — interaction differences require side-by-side screenshots
- **Specific recommendations** — not "borrow X"; instead "add feature Y in scene Z"
- **No empty adjectives** — delete "very clever", "significantly better", "remarkably deep"
- **Separate fact from judgment** — annotate 【个人观察】/【个人推测】 clearly
- **Process goes in appendix (or nowhere)** — the report is not a thinking diary
- **Explicit priorities** — P0/P1/P2 for all recommendations
- **Scannable first lines** — each section's first line must stand alone

**HTML styling**: Apply consistent CSS conventions — use a muted accent color, readable serif/sans-serif typography pairing, and visually distinct 【个人观察】 annotation boxes. (Example: 松石灰绿 `#3a6b5f` accent, Fraunces + Noto Sans SC, 琥珀棕 `#8a6a3a` for annotation boxes — adapt to your team's palette.)

## Collaboration Contract

What Claude **must not** do (learned from past failures):
- Inject judgments into the user's observations during Phase 1
- Write unverified speculation as fact
- Add aesthetic flourishes ("very clever", "remarkably") to decorate content
- Reorganize user's raw observations into Claude's preferred structure during Phase 1
- Skip Phase 2.5 and jump to HTML

What Claude **must** do:
- Record faithfully in user's own words
- Move at the user's pace during Phase 1
- Actively web_search for Red bucket claims
- Separate fact from judgment clearly
- Check against Task Contract at every phase transition
- Produce the outline in Phase 2.5 before any HTML

What the researcher should remember:
- Trust your first intuitions in Phase 1 — rough is fine
- Be willing to delete observations that don't serve any D
- Don't over-defer to Claude's suggestions
- Push back when Claude's phrasing doesn't match your voice

## Quick Reference · Phase Transitions

| Transition | Must have before moving | Skip-cost if rushed |
|-----------|------------------------|--------------------|
| Pre-Phase 1 | Task Contract signed | Goal drift, scope creep |
| Phase 1 → 2 | Contract dimensions covered | Missing a core deliverable |
| Phase 2 → 2.5 | All Red bucket verified or downgraded | Unverified claims in final report |
| Phase 2.5 → 3 | User-approved outline | Massive HTML rework |
| Phase 3 → delivery | All 10 writing rules applied + DoD checklist passed | Deliverable missing boss's actual asks |

## Reference Files

Load these as needed:

- `references/task-contract.md` — Full task contract template (7 sections) with examples
- `references/pyramid-principle.md` — Minto Pyramid Principle, SCQA, MECE, Rule of 3, Hypothesis-driven thinking
- `references/writing-rules.md` — 10 hard writing rules for Phase 3
- `references/report-templates.md` — 5 standard report templates (A through E) with structural blueprints

## Output Expectations

A report produced via this workflow should:

1. Open with a **§ 0 · Core Conclusion** that a busy reader can absorb in 60 seconds
2. Have MECE-organized body sections, each with leading conclusions and evidence
3. Include paired screenshots for every interaction/product difference claim
4. End with specific, prioritized, actionable recommendations
5. Separate the author's exploration process (→ appendix or self-archive) from the deliverable content

If the report reads like a thinking diary — with chronological exploration, unverified speculation, or process narrative in the main body — the workflow was not followed correctly.
