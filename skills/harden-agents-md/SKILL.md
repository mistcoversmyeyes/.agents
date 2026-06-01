---
name: harden-agents-md
description: |
  审计已有的 AGENTS.md（或 CLAUDE.md），将其中可被机械化执行的内容替换为
  实际的 harness 实现（git hooks、lint 配置、CI 等）。仅处理已有文件，如需
  从零创建 AGENTS.md，请使用 /initialize-agents-md。
disable-model-invocation: true
---

# Harden AGENTS.md

> 本 skill 处理**已有**的 AGENTS.md 文件。如需从零创建，请使用 `/initialize-agents-md`。

Apply the **不可替代原则** (Irreplaceability Principle): if a constraint or convention
in an existing AGENTS.md can be enforced mechanically, it should be — freeing the document
to focus on what only prose can convey (design intent, context, principles).

## Overview

This skill performs a two-phase process:

1. **Audit phase**: Scan the given AGENTS.md and produce a report of replaceable
   constraints, each with a recommended harness type and implementation plan.
   **No files are modified** in this phase.
2. **Implementation phase**: For each user-confirmed item, create the harness files
   and update AGENTS.md to reference the harness instead of the prose constraint.

## Phase 1: Audit

### Step 1: Read the target file

Ask the user which file to scan. If they don't specify, check for:
- `.agents/AGENTS.md`
- `.claude/CLAUDE.md`
- `CLAUDE.md`
- `AGENTS.md`

### Step 2: Scan section by section

Read the file and identify every section that describes a constraint, convention, or
rule that could be enforced by tooling. For each candidate, classify it against the
harness catalog in `references/harness-catalog.md`. Read that file now before proceeding.

A constraint is "replaceable" when:
- It describes a **format** that can be validated (commit messages, file names, frontmatter)
- It describes a **process** that can be scripted (build steps, test commands, deploy flows)
- It describes a **check** that can be automated (lint rules, type checks, schema validation)
- It describes a **template** that can be pre-filled (PR descriptions, issue forms, commit bodies)
- It describes a **convention** that has existing tooling (code style, branch naming, versioning)
- It describes a **setup** sequence that belongs in scripts or config (install steps, env vars)

A constraint is NOT replaceable when:
- It conveys **design intent** or rationale ("we chose X because...")
- It describes **project context** that's unique to this repo
- It captures **author perspective** or style preferences
- It explains **architectural decisions** and trade-offs
- It provides **background knowledge** the agent can't derive from code

### Step 3: Produce the audit report

For each replaceable constraint found, present it to the user one at a time:

```
## 发现可替换约束 #N

**AGENTS.md 原文**:
> <quoted text from the file>

**约束类型**: <commit format | code style | branch rule | file layout | checklist | ...>
**推荐 harness**: <具体方案，如 `.githooks/commit-msg`>
**实现方式**: <简要描述如何实现>
```

Then ask the user to confirm or skip this item before moving to the next.

## Phase 2: Implement

For each confirmed item:

### Step 1: Create the harness

Implement the mechanical enforcement. Refer to `references/harness-catalog.md` for
templates and implementation patterns for each harness type.

Key principles:
- Create the harness in the appropriate location for the project
- Ensure the harness is self-documenting (comments explain what it enforces and why)
- For git hooks, configure `core.hooksPath` if needed
- For CI configs, use the project's existing CI provider
- For package.json scripts, add under a recognizable key

### Step 2: Update AGENTS.md

Replace the prose constraint with a concise reference to the harness:

```markdown
<!-- Before -->
### 提交命名规范
- `blog(posts/draft): ...`
- `blog(posts/publish): ...`

<!-- After -->
### 提交命名规范
提交信息格式由 `.githooks/commit-msg` 自动校验，无需手动记忆。
```

The replacement should:
- Be shorter than the original
- Point to the harness that now enforces the rule
- Optionally keep a one-line summary of the rule for human readers
- Never duplicate the enforcement logic (that's in the harness now)

### Step 3: Confirm completion

After implementing an item, show the user:
1. What files were created/modified
2. The before/after in AGENTS.md
3. How to test that the harness works

## Post-implementation summary

After all confirmed items are processed, produce a summary table:

| 约束 | 原形式 | 新形式 | 文件 |
|------|--------|--------|------|
| 提交信息格式 | AGENTS.md 文字 | commit-msg hook | `.githooks/commit-msg` |
| ... | ... | ... | ... |

## Edge cases

- **Existing harness conflicts**: If a harness file already exists (e.g., `.githooks/commit-msg`),
  ask whether to merge, replace, or skip
- **CI provider unknown**: Ask which CI system the project uses before creating configs
- **Multi-file projects**: Some constraints span multiple directories; ask about scope
- **Partial replacement**: Some constraints can only be partially mechanized (e.g., "one article
  per commit" is hard to enforce fully). Flag these clearly and only implement the mechanizable portion
- **Mature vs immature constraints**: Per the "无法替代原则" lifecycle, a constraint that's
  still evolving should stay in AGENTS.md. Ask the user if each constraint has "settled" before
  implementing
