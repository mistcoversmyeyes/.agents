---
name: doc-harness-init
description: |
  从零开始交互式创建文档类 Harness（AGENTS.md、CLAUDE.md 及 companion 文件），
  贯彻信息增量、最小编码、无法替代三个原则。适用于全新项目或重新设计文档架构。
  创建完成后，追加内容请用 /doc-harness-append，重构请用 /doc-harness-refactor，
  硬化约束请用 /doc-harness-harden。
disable-model-invocation: true
---

# doc-harness-init

从零创建文档类 Harness。AGENTS.md 是地图，深层内容分流到 companion 文件。

## 理论基础

在开始之前，阅读 `references/doc-harness-theory.md`，其中定义了三个原则、三个功能、
地图角色和生命周期模型。后续所有步骤基于这些理论。

## 工作流

### Phase 1: 了解项目

逐个询问（每次一个问题，不一次性抛出）：

1. **项目是什么**：一句话描述
2. **技术栈**：主要语言、框架、工具。只需名字，不需要版本号（package.json 里有）
3. **非标准约定**：和同类项目不同的做法？特殊的目录结构、非典型模块组织
4. **关键决策**："为什么选了 A 而不是 B"——决策上下文不在代码里
5. **已有项目文件**：README、CONTRIBUTING、package.json 等。引导 Agent 读这些文件，不在 AGENTS.md 中重复

### Phase 2: 逐节构建

每节写完后展示给用户确认。

#### 2.1 项目上下文（增量信息）

Agent 无法从代码推导什么：非标准约定、历史决策及原因、项目"潜规则"。

**每写一行追问**：Agent 能从代码/package.json/README 中得到吗？能 → 删除或改为引用。

#### 2.2 技术栈与工具（最小编码 + Cache）

只包含：
- 主要语言和框架名（一行）
- 非标准工具选择
- 指向配置文件（package.json 等）的引用

排除：版本号、lockfile 可推导的依赖、标准命令。

#### 2.3 约束与约定（无法替代原则）

对每个约束做三问：
1. 稳定了吗？→ 演变中则标注 `<!-- TODO(harden): 稳定后迁移 -->`
2. 能被机械化吗？→ 提交格式 → commit-msg hook；代码风格 → lint 配置
3. 都不能替代 → 以最小编码写入

#### 2.4 命令与工作流（最小编码）

不列出标准命令（`pnpm dev` 等）——让 Agent 读 package.json。
仅包含非标准工作流和多步骤流程。

#### 2.5 地图 vs 深度文档决策

构建完成后审视 AGENTS.md 初稿：
- 某节超过 50 行且自包含 → 建议拆出为独立 companion 文件
- 某节是多个不相关内容的混合 → 建议拆分后分别归入不同 companion
- AGENTS.md 总行数 > 150 → 必须拆分

### Phase 3: 原则审查

逐节审阅：
1. **信息增量检查**：每行问"Agent 能从别处得到吗？"
2. **最小编码检查**：每行问"能用人话更简短表达吗？"
3. **无法替代检查**：每段约束问"能被 hook/lint/CI 强制执行吗？"

审查发现的问题直接修改并告知用户。

### Phase 4: 写入文件

1. 写入 `.agents/AGENTS.md`（地图，~100 行）
2. 创建 `.claude/CLAUDE.md` 软链接 → `.agents/AGENTS.md`
3. Phase 2.5 确认的 companion 文件一并创建，在地图中加入引用
4. 如有 `TODO(harden)` 标注，提醒后续可用 `/doc-harness-harden`
5. 展示文件清单和统计

## 风格指南

写出的文档应体现：
- **密度高但不晦涩**：不给废话，每句人一眼能看懂
- **引用而非重复**：指向已有文件，只写路径不复制内容
- **标注迁移意图**：模糊约束标 TODO(harden)
- **中文为主**

## 反模式提醒

- 列出所有 npm scripts → 引导读 package.json
- 大段编码规范 → 建议创建 lint 配置
- 详细安装/构建步骤 → 这些属于 README
- 技术栈版本号列表 → package.json 已包含

## 生命周期提示

创建完成后：
- 新内容 → `/doc-harness-append`
- 结构重构 → `/doc-harness-refactor`
- 约束硬化 → `/doc-harness-harden`

## Edge cases

- **已有 AGENTS.md**：覆盖或合并？合并则先做快速审计，只加增量
- **无 package.json 的项目**：命令和工作流可适当多写
- **Monorepo**：询问为根还是子包创建
- **用户想跳过某节**：允许。空文档比废话文档好
