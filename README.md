# product-research-workflow

A Claude Skill for structured PM research reports — competitive analysis, product experience reports, user research, and more.

中文 PM 调研工作流 · 帮你把原始观察变成高密度、可交付的结构化报告。

---

## What it does · 做什么

This skill gives Claude a **four-phase workflow** for any PM research task:

| Phase | Name | What happens |
|-------|------|-------------|
| 0 | Task Contract | Lock in deliverables before exploring — prevents goal drift |
| 1 | Felt Exploration | Free-form observation, Claude records faithfully without adding judgment |
| 2 | Classification & Verification | Sort observations into facts / personal notes / claims to verify |
| 2.5 | Outline Preview | Agree on structure before writing — 10× cheaper to fix than HTML |
| 3 | Final Report | High-density, structured deliverable with evidence and dual screenshots |

Built on **Barbara Minto's Pyramid Principle**: think bottom-up, present top-down.

---

## Trigger keywords · 触发关键词

The skill activates automatically when you mention:

```
竞品调研 · 产品调研 · 体验报告 · 竞品报告 · 产品体验 · 调研报告
good bad 分析 · 产品对比 · 写报告 · 整理发现 · 给老板看
competitive analysis · product research · UX report · product review
```

No slash commands needed — just talk naturally.

---

## Install · 安装

### Option A · Claude.ai (web)

1. Download [`product-research-workflow.zip`](../../releases/latest) from Releases
2. Go to **claude.ai → Settings → Capabilities** → enable **Code execution and file creation**
3. Go to **Customize → Skills → Upload** → upload the ZIP
4. Toggle the skill **on**

Done. The skill will activate automatically on relevant requests.

### Option B · Claude Code (terminal)

```bash
# Personal install (works across all projects)
cp -r product-research-workflow ~/.claude/skills/
```

---

## File structure · 文件结构

```
product-research-workflow/
├── SKILL.md                    ← Main skill file (Claude reads this)
└── references/
    ├── task-contract.md        ← Full task contract template (7 sections)
    ├── pyramid-principle.md    ← Minto Pyramid, SCQA, MECE, Rule of 3
    ├── writing-rules.md        ← 10 hard writing rules for Phase 3
    └── report-templates.md     ← 5 report templates (A–E)
```

---

## Core principles · 核心原则

1. **Reports are not thinking diaries** · 报告不是思考日记
   Thinking process stays with the author. Conclusions go to the reader.

2. **Think bottom-up, present top-down** · 自下而上思考，自上而下呈现
   Explore freely first. Structure only when you know what you've found.

3. **Judgment earns value through evidence** · 判断的价值来自证据
   "Very clever design" without evidence is decoration, not analysis.

---

## What the final report looks like · 产出报告长什么样

- **§ 0 · Core Insight** — conclusions visible within 60 seconds of opening
- **MECE-organized body sections** — each with leading conclusions + evidence
- **Paired screenshots** for every product/interaction difference
- **Specific, prioritized, actionable recommendations**
- Separation of exploration process (→ self-archive) from deliverable content

---

## Author · 作者

Made by **Sage** · PM intern at Noiz AI  
Built during Day 1–2 of onboarding, refined through real competitive analysis work.

---

## License

MIT — use freely, attribution appreciated.
