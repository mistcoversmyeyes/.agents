# 个人编码偏好

## 通信风格
- **语言**：用中文表达想法，代码注释用英文
- **表达**：直接、犀利，不绕弯子。先给结论，如果用户需要解释，再提供原因
- **代码引用**：使用 `file_path:line_number` 格式

## 编码习惯
- 编写过程的时候预判一些长的过程，将其写为辅助函数，并且在主函数中调用它们
- 超过3层缩进就重构
- 消除特殊情况，而不是增加条件判断
- 优先简化数据结构，而不是优化代码

## 安全习惯
- 禁止硬编码密钥、密码、Token
- 敏感操作前必须确认（rm -rf、git reset --hard 等）
- git 提交前检查是否有敏感信息

## 常用 Agent
- **linus-reviewer**：需要代码审查或技术决策分析时使用
  - 触发方式："用 linus-reviewer 分析" 或 "用 Linus 的视角"

## 常用工具

### 搜索网页
- **webSearch-Tongyi**: 使用统一搜索引擎（如 Google、Bing）进行网页搜索

### 查看官方文档
1. **resolve-library-id** - 解析库名到 Context7 ID
2. **get-library-docs** - 获取最新官方文档

### 搜索真实代码
- **searchGitHub** - 搜索 GitHub 上的实际使用案例

### Codex 编码任务自动化

使用 `codex-caller` skill 规范化 Codex 调用。

**触发条件**（满足任一即触发）：
1. 用户显式提及 "codex" 或 "编写代码"
2. 用户使用 `/codex` 斜杠命令
3. 用户请求明确编码任务（"实现"、"添加"、"重构"等）

**默认参数**：
- cwd: 当前项目根目录
- approval-policy: on-failure
- sandbox: workspace-write

**参数覆盖**：
用户可显式指定参数覆盖默认值，例如：
- "在 /tmp/other-项目 中用 codex" → 覆盖 cwd
- "用 untrusted 模式" → 覆盖 approval-policy

**工作流**：
1. 检测到编码意图
2. 使用默认参数或用户指定参数
3. 调用 Codex 处理
4. 返回 Codex 结果给用户



## 注意事项
- gh cli 已经 auth 并且可以使用
