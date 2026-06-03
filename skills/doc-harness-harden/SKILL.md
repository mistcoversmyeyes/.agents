---
name: doc-harness-harden
description: |
  审计已有的文档类 Harness（AGENTS.md 及 companion 文件），将其中可被机械化
  执行的约束迁移到 git hooks、lint 配置、CI 等 harness 实现。仅处理已有文件。
  如文档结构混乱或冗余，请先运行 /doc-harness-refactor 再硬化。如需新增约束
  请用 /doc-harness-append，从零创建请用 /doc-harness-init。
disable-model-invocation: true
---

# doc-harness-harden

> 本 skill 处理**已有**的文档类 Harness。如需从零创建，使用 `/doc-harness-init`。

将文档中的约束迁移到机械化 harness——体现**无法替代原则**。
约束有生命周期：模糊时文字，稳定后 hook/lint/CI。

## 理论基础

在开始之前，阅读 `references/doc-harness-theory.md`，其中定义了三个原则、三个功能、
地图角色和生命周期模型。后续所有步骤基于这些理论。

## Phase 1: 审计

### Step 1: 先读地图

读取 AGENTS.md 获取文档地图。地图可能引用 companion 文件，这些文件中也可能有可硬化的约束。询问用户扫描范围：
- 仅 AGENTS.md
- AGENTS.md + 所有引用的 companion 文件
- 用户指定的文件

### Step 2: 逐节扫描

对每个文件，找出描述约束/约定/规则的段落。对照 `references/harness-catalog.md` 分类。

可替换的约束（6 类）：
- 可验证的**格式**（提交信息、文件名、frontmatter）
- 可脚本化的**流程**（构建、测试、部署命令序列）
- 可自动化的**检查**（lint 规则、类型检查、schema 校验）
- 可预填的**模板**（PR 描述、Issue 表单、commit body）
- 有现有工具的**约定**（代码风格、分支命名、版本管理）
- 属于脚本/配置的**设置序列**（安装步骤、环境变量）

不可替换的内容（5 类）：
- 设计意图或理由
- 项目特有上下文
- 作者视角或风格偏好
- 架构决策与权衡
- Agent 无法从代码推导的背景知识

### Step 3: 评估成熟度

对每个可替换约束，判断成熟度：
- **稳定**（已知格式已固定）→ 可以硬化
- **演变中**（还在调整）→ 暂不硬化，建议标注 `TODO(harden)`
- **不确定** → 询问用户

### Step 4: 生成审计报告

逐条展示（每次一条，等用户确认）：

```
## 可替换约束 #N

**原文**:
> <引用>

**约束类型**: <commit format | code style | branch rule | file layout | checklist | ...>
**推荐 harness**: <.githooks/commit-msg | lint 配置 | CI workflow | ...>
**成熟度**: <稳定 | 演变中>
**实现方式**: <简要描述>
```

### Step 5: 重构检查

审计完成后，如果发现以下信号，建议先重构再硬化：
- 多个文件包含可合并的同类约束
- 文档结构不清晰（约束散落、职责不明）
- AGENTS.md 行数 > 150

→ "建议先运行 `/doc-harness-refactor` 整理文档结构，再硬化会更高效。是否继续当前硬化？"

## Phase 2: 实施

对每个用户确认的项目：

### Step 1: 创建 harness

参考 `references/harness-catalog.md` 选择合适的实现方式。

原则：
- 放在项目适当位置（`.githooks/`、`.github/workflows/` 等）
- 自文档化（注释解释约束内容和原因）
- git hooks 需配置 `core.hooksPath`
- CI 配置使用项目已有的 CI 系统
- package.json scripts 加在可识别的 key 下

### Step 2: 更新文档

将文字约束替换为简洁引用：

```
前：### 提交命名规范
    - blog(posts/draft): ...
    - blog(posts/publish): ...

后：提交信息格式由 .githooks/commit-msg 自动校验，无需手动记忆。
```

替换原则：比原来短、指向 harness、可保留一行摘要给人类读者、不重复执行逻辑。

### Step 3: 确认完成

展示：创建/修改的文件、AGENTS.md before/after、如何测试 harness。

## 汇总表

| 约束 | 原形式 | 新形式 | 文件 |
|------|--------|--------|------|
| ... | ... | ... | ... |

## 生命周期提示

硬化完成后：
- 新约束 → `/doc-harness-append`
- 结构问题 → `/doc-harness-refactor`

## Edge cases

- **已有同名 harness 文件**：合并/替换/跳过？
- **CI provider 未知**：先询问 CI 系统再创建配置
- **多文件项目**：约束可能跨多个目录，询问 scope
- **只能部分机械化**：明确标注可实现和不可实现的部分
- **未成熟约束**：标注 `TODO(harden)` 保留在文档中
