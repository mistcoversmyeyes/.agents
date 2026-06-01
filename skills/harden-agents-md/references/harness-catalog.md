# Harness Catalog

每一种 harness 类型对应 AGENTS.md 中哪类可替换内容，以及标准实现方式。

## 1. Git Hooks

存放位置: `.githooks/`，通过 `git config core.hooksPath .githooks` 激活。

### commit-msg — 提交信息格式

**替换对象**: 提交信息命名规范、格式约定、scope 限制

**模板**:
```bash
#!/bin/bash
COMMIT_MSG=$(cat "$1")
BRANCH=$(git rev-parse --abbrev-ref HEAD)

# Define allowed patterns per branch
# ...

if ! echo "$COMMIT_MSG" | grep -qE "$PATTERN"; then
    echo "ERROR: Commit message does not follow project convention" >&2
    exit 1
fi
```

### pre-commit — 提交前检查

**替换对象**: frontmatter 格式校验、draft 状态检查、禁止提交的文件类型、代码格式化

### pre-push — 推送前检查

**替换对象**: 测试要求、构建验证、分支命名规则、敏感信息检查

### prepare-commit-msg — 提交信息模板

**替换对象**: 提交信息模板、自动填充 scope/prefix

---

## 2. Lint/Format 配置

### ESLint (.eslintrc.* / eslint.config.*)

**替换对象**: JavaScript/TypeScript 代码风格规范、禁用 API、命名约定

### Prettier (.prettierrc)

**替换对象**: 格式化规范（缩进、引号、分号、行宽等）

### EditorConfig (.editorconfig)

**替换对象**: 编辑器级格式规范（缩进风格、字符编码、换行符）

### Vale / textlint

**替换对象**: 文档写作规范、术语表、中英文混排规则

---

## 3. CI/CD 配置

存放位置: `.github/workflows/`（GitHub Actions）或对应 CI 系统目录

**替换对象**:
- PR 检查清单 → PR workflow 中的自动化检查
- 构建/部署规范 → CI pipeline
- 测试要求 → CI 中的 test job
- 发布流程约束 → release workflow

---

## 4. package.json scripts

**替换对象**:
- 构建命令序列 → `pnpm build` script
- 测试命令 → `pnpm test` script
- 开发环境启动 → `pnpm dev` script
- 代码质量检查组合 → `pnpm check` script
- 部署命令 → `pnpm deploy` script

**原则**: AGENTS.md 中列出的命令速查（如 `pnpm dev`, `pnpm build`）应通过
`package.json` 的 `scripts` 字段自文档化，而不是在 AGENTS.md 中重复列出。

---

## 5. GitHub Templates

存放位置: `.github/`

### PULL_REQUEST_TEMPLATE.md

**替换对象**: PR 提交规范、review 检查清单、合并前自检项

### ISSUE_TEMPLATE/ 

**替换对象**: Issue 报告格式、bug report 模板、feature request 模板

---

## 6. Editor/IDE 配置

存放位置: `.vscode/`

### settings.json

**替换对象**: 编辑器格式化设置、默认缩进、文件编码

### extensions.json

**替换对象**: "推荐安装的 VS Code 扩展"列表

---

## 7. Runtime/Environment 约束

### .nvmrc / .node-version

**替换对象**: Node.js 版本要求（"本项目需要 Node 18+"）

### .tool-versions (asdf)

**替换对象**: 多语言运行时版本约束

### devcontainer.json

**替换对象**: 开发环境搭建步骤（"先装 X，再装 Y，然后配置 Z"）

---

## 8. 版本/分支管理

### Git hooks (pre-push / pre-commit)

**替换对象**: 分支命名规则（`feat/*`, `fix/*` 等）、禁止直接推送受保护分支

### GitHub Branch Protection Rules

**替换对象**: 合并策略、review 要求、status check 要求

---

## 判定辅助：何时不该替换

以下内容应保留在 AGENTS.md 中：
- **设计意图与历史决策**: "为什么选 Rust 而不是 C++" — 这类信息无法从代码推导
- **作者个人偏好**: "我偏好 CLI 而非 GUI" — 这影响 Agent 的交互方式选择
- **项目特定约束的 WHY**: "我们这个模块不写测试是因为硬件依赖" — 解释了反常规决策
- **领域知识**: "CMU 15-445 的 Lab 结构是..." — 外部知识，Agent 训练数据中可能有但不可靠
- **软约束 / 演进中的约束**: "暂时先用 X 模式，后续可能改为 Y" — 未稳定，不宜硬化
