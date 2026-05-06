# product-research-workflow
A Claude Skill that turns messy product observations into structured, deliverable PM reports.

## The Problem

Product research has two distinct modes that are easy to confuse.

**Exploration** needs freedom — rough notes, intuitions, rabbit holes.  
**Delivery** needs discipline — evidence, structure, conclusions first.

When you mix the two, reports end up reading like thinking diaries: chronological, full of unverified speculation, personal reflections tangled with facts. AI assistants make it worse by adding judgment ("very clever design") without evidence, and inferring things on your behalf that you never actually observed.

This skill exists to separate the two modes — so your exploration stays messy and free, and your deliverable comes out structured and credible.

## The Approach
Three principles, borrowed from Barbara Minto's Pyramid Principle and refined through real project work:

- **Reports are not thinking diaries.** Your exploration process stays with you. Only conclusions and evidence reach the reader.
- **Think bottom-up, present top-down.** Explore freely and gather observations first. When it's time to write, flip the order — lead with conclusions, support with evidence.
- **Judgment earns value through evidence.** "Great design" without a screenshot is decoration. Every claim needs a fact, a data point, or a source.


## The Workflow
The skill guides Claude through four phases:

**Phase 0 · Task Contract**  
Before any exploration begins, lock in what you need to deliver. Write down the exact request, break it into checkable deliverables, define what "done" looks like. This prevents goal drift — the tendency to chase interesting tangents while forgetting what was actually asked for.

**Phase 1 · Felt Exploration**  
Explore the product freely. Claude acts as a faithful recorder — capturing your observations in your own words, without adding judgment or restructuring your thoughts. Low density is expected. Rough is fine.

**Phase 2 · Classification & Verification**  
Sort every observation into three buckets: facts you saw firsthand (green), your personal inferences (yellow), and claims about external things that need verification (red). Red claims get web-searched before they can enter the report.

**Phase 2.5 · Outline Preview**  
Produce a text-only outline before writing any HTML. Decide what goes into the report and what stays in your personal archive. Fixing structure at outline stage is 10× cheaper than fixing it in a finished document.

**Phase 3 · Final Report**  
Write the deliverable. Conclusions first in every section. Evidence for every claim. Paired screenshots for every product comparison. Specific, actionable recommendations — not "consider improving X" but "add feature Y in scenario Z."

## File Structure
```
product-research-workflow/
├── SKILL.md                    — Main skill file (Claude reads this)
└── references/
    ├── task-contract.md        — Task contract template with 7 sections
    ├── pyramid-principle.md    — Minto Pyramid, SCQA, MECE, Rule of 3
    ├── writing-rules.md        — 10 hard writing rules for the final report
    └── report-templates.md     — 5 report templates for different task types
```

## Install
**Claude.ai (web/app)**

1. Download the ZIP from Releases
2. Go to claude.ai → Settings → Customize → Skills → Upload
3. Toggle the skill on

The skill activates automatically when you mention things like "competitive analysis", "product research", "write a report", or "help me organize my findings."

**Claude Code (terminal)**
```bash
cp -r product-research-workflow ~/.claude/skills/
```

## Author
Built by Sage.

## License
MIT
