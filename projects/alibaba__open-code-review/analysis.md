## 它是什么
OpenCodeReview（命令名 `ocr`）是阿里内部 AI 代码评审助手开源版。它不是一个单纯的 prompt 包装，而是 CLI 工具：读取 Git diff，通过带工具调用能力的 agent 把变更文件交给可配置 LLM，产出结构化、行级精准的评审评论。除 diff 评审外，`ocr scan` 还支持对无有意义 diff 的目录做全文件审计。

## 为什么火
项目源自阿里集团内部官方工具，号称两年服务数万开发者、识别数百万缺陷。开源后 Star 达 54158。发布的 AACR-Bench 用 50 个开源仓库、200 个真实 PR、10 种语言、1505 条专家标注 ground truth 做评测：相同底层模型下，OpenCodeReview 相比 Claude Code 类通用 agent，Precision 和 F1 更高，token 消耗约 1/9，耗时更短；代价是 Recall 更低，即故意用召回换精准，减少噪音。这切中了用通用 agent 做评审的常见痛点：大变更集覆盖不全、行号漂移、质量不稳定。

## 技术栈
- 语言：Go（README 主题标注），CLI 通过 npm 全局安装。
- 平台：Windows、macOS、Linux。
- 模型兼容：OpenAI 与 Anthropic 兼容端点。
- Agent 技能：支持 Claude Code、Codex、Cursor、Kimi Code。
- 依赖：Git >= 2.41。
- 规则集：内置 NPE、线程安全、XSS、SQL 注入等多语言规则。

## 核心能力
- **混合架构**：确定性工程负责必须正确的步骤——文件选择、智能文件打包（如把多语言 properties 文件打包为一个评审单元）、细粒度规则匹配、外部定位与反思模块；LLM Agent 负责动态决策和动态上下文检索。
- **行级精准评论**：独立定位和反思模块，减少行号/文件漂移。
- **双层评审模式**：原生模式使用 `ocr` 自己的 provider 配置走完整管线；Delegation 模式复用宿主 agent（如 Claude Code/Cursor）的模型和鉴权，由 `ocr` 提供管线、护栏和结构化报告。
- **全文件审计**：`ocr scan` 可审计没有 diff 的未知代码库或目录。
- **CI 友好**：examples 目录含 GitHub Actions、GitLab CI、Gerrit、Bitbucket Pipelines、Codeup CI 等示例。

## 适用场景
- 团队希望在 CI/CD 里加上自动代码评审、降低人工 review 压力。
- 大仓或大变更集，要求稳定覆盖所有文件、且评论位置准确。
- 对 token 开销和误报率敏感，愿意用一定召回换取高精度。
- 不想单独申请模型 key，已有 Claude/Cursor 等订阅，可采用 delegation 模式。

## 同类对比
- **对比通用 Agent + Skills（Claude Code、Codex、Cursor 等）**：通用方案靠自然语言 prompt 约束，大 changeset 容易漏文件、行号漂移、质量波动；OpenCodeReview 用工程化硬约束替代纯语言约束，benchmark 显示精度更高、token 更省。
- **对比传统静态分析工具**：`ocr` 不是纯规则静态分析，能结合仓库级上下文做语义审查；但内置规则匹配部分带有模板引擎特征，比纯 LLM 更稳定。
- **对比其他 AI 评审工具（如 CodeRabbit 等）**：README 未给出对比数据，无法判断。

## 版本动态
最新 release 为 v1.13.12（2026-11-18），与仓库最近推送同日。该版本内容以 bugfix 和小改进为主：修复 session identity 字段、telemetry 惰性指标、file_read 结果字节数限制、Windows teardown、WaitDelay 等。`docs/task-runtime-phase-one.md` 暗示任务运行时仍在迭代。仓库创建于 2026-05-18，约 6 个月冲到 5w+ Star，热度高但需观察后续功能演进。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：README 未列出内置规则集完整语言覆盖范围；未说明 Go 核心与 npm 包的关系（是否 npm 包装 Go 二进制）；AACR-Bench 未给出具体 Recall/Precision/F1 数值和对比模型版本；未列出所有内置 provider 及自定义 provider 配置字段；examples/ 目录存在但未展示各 CI 配置具体内容