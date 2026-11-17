## 它是什么

Open Code Review（CLI 命令 `ocr`）是阿里巴巴把内部官方 AI 代码审查助手开源出来的项目。它读取 Git diff，通过带工具调用能力的 Agent 把变更文件交给可配置 LLM，产出结构化、行级精准的 review 评论；也支持 `ocr scan` 对无 diff 的整个文件/目录做审查。README 强调内部已用两年、服务数万开发者、识别数百万缺陷。

## 为什么火

- 阿里内部两年、数万开发者、数百万缺陷的真实规模验证后开源；
- GitHub 页面 Star 53.6k，项目创建约 6 个月即获得较高关注；
- 针对通用 Agent 做代码审查的三大痛点：文件覆盖不全、行号/位置漂移、质量不稳定；
- 核心设计是“确定性工程 × Agent”混合架构：文件选择、智能打包、规则匹配、评论定位/反思由工程逻辑硬约束，Agent 只负责动态决策和上下文检索；
- 基准测试称相比 Claude Code 通用 Agent，同样模型下 Precision/F1 显著更高，token 仅约 1/9，速度更快；Recall 较低是刻意取舍，减少噪音；
- 内置多语言规则集，举例涵盖 NPE、线程安全、XSS、SQL 注入等。

## 技术栈

- 语言：Go
- 分发：npm 包 `@alibaba-group/open-code-review`，全局安装后提供 `ocr` 命令
- 依赖：Git >= 2.41
- 模型兼容：OpenAI 与 Anthropic 兼容接口；支持内置/自定义 provider
- Agent Skills：支持 Claude Code、Codex、Cursor、Kimi Code
- CI 示例：GitHub Actions、GitLab CI、Bitbucket Pipelines、Gerrit CI、Codeup CI、GitFlic CI
- 基准数据集：HuggingFace 上的 `AACR-Bench`

## 核心能力

- **确定性管线**：精确文件过滤/选择、智能文件打包（相关文件组成 sub-agent、隔离上下文、支持大变更集和并发）、基于模板引擎的细粒度规则匹配、独立评论定位和反思模块；
- **Agent 层**：场景微调的 prompt 与工具集，Agent 可读完整文件、搜索仓库、查看其他变更文件，产出深层 review；
- **双模式**：Native 模式使用 OCR 自己的 provider 和完整 pipeline；Delegation 模式借用宿主导 Agent 的模型/认证，但由 OCR 提供 pipeline 与 guardrails；
- **行级评论**：结构化输出，CI 中可用；
- **内置安全/质量规则**：NPE、线程安全、XSS、SQL 注入等（README 只举例，未给全量清单）。

## 适用场景

- 团队在 PR/MR 阶段接 CI 做自动代码审查；
- 个人开发者在 Claude Code、Cursor 等宿主导 Agent 中通过 Skills 使用；
- 没有 diff 的历史代码或陌生目录审计（`ocr scan`）；
- 希望用同样底层模型但比通用 Agent 更低 token、更少误报的审查场景。

## 同类对比

README 仅与“通用 Agent（Claude Code）”对比：OCR 在相同模型下 Precision/F1 更高、token 约 1/9、耗时更低，但 Recall 更低——适合追求少误报、控制成本的 CI 场景。未看到与专用代码审查工具的直接对比数据。

## 版本动态

最新 Release `v1.13.11`（2026-11-17）仍在高频迭代：新增 session 按分支过滤、Move review 规则；修复不同路径拼写比较、多字节文件路径 rune 边界、MCP server 名称含点号、VSCode 上报失败状态、ACP 输入限制提示等问题；文档优化 onboarding 和多语言截图。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：README 未列出具体支持语言完整清单（benchmark 提到 10 种语言，但未逐个说明）；未提供与专用代码审查工具（如 CodeRabbit 等）的直接对比，仅对比通用 Claude Code Agent；内置规则集只举例 NPE/线程安全/XSS/SQL 注入，未给全量规则列表；未说明不同 provider 的认证/配置细节，需到官网 docs 查看；Star 数和趋势图来自页面 badge，建议核实统计口径