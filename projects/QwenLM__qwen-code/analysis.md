## 它是什么

QwenLM/qwen-code 是一个开源 AI 编码代理，主要运行在终端，由 TypeScript 编写，Apache-2.0 许可。README 宣称覆盖终端、编辑器、桌面、浏览器、聊天和 SDK 等入口，不只是单一 CLI。

## 为什么火

30k+ Star、2025 年 6 月创建后持续更新。核心卖点是开箱即用的 Agentic 能力（Auto-Memory、Skills、SubAgents、MCP），同时支持 OpenAI、Anthropic、Gemini、Qwen 以及 Ollama/vLLM 本地模型，减少供应商锁定。对想用 Qwen 开源模型或混合多模型的开发者有吸引力。

## 技术栈

- 语言：TypeScript，要求 Node.js >=22（npm 安装方式）
- 分发：独立安装脚本（Linux/macOS/Windows）、npm、Homebrew
- 协议：多模型 API（OpenAI/Anthropic/Gemini/Qwen），MCP，HTTP+SSE（ACP daemon）
- SDK：TypeScript、Python、Java

## 核心能力

- Agentic 默认可用：Auto-Memory、Skills、SubAgents、MCP 首会话即可用；Agent Teams、Agent Arena、Dynamic Workflows 实验或 opt-in
- 多协议/本地模型：运行时可切换，支持 Ollama/vLLM
- 多界面：终端 `qwen`、桌面应用、Web UI（`qwen serve --open`，实验）、VS Code/Zed/JetBrains 插件、聊天集成（Telegram/DingTalk/WeChat/WeCom/Feishu 等）
- 自动化：headless `qwen -p` 用于脚本/CI；SDK 构建自定义集成；daemon 模式

## 适用场景

- 在终端里快速理解/修改代码库
- 需要无供应商锁定、可接入本地模型或多家云模型的团队
- 想从 CLI 扩展到 IDE/聊天/CI 自动化的开发者
- 基于 Qwen 开源模型做定制 coding agent

## 同类对比

对比 Claude Code / OpenAI Codex CLI / Gemini CLI：qwen-code 强调模型无关和全开源（框架与模型），且多界面开箱即用；但 README 未提供 benchmark，实际代码生成质量需自行测试。对比 Aider：qwen-code 有更完整的 GUI/聊天入口和 MCP 集成，但 CLI 复杂度可能更高。

## 版本动态

最新 Release 为 sdk-typescript-v0.1.34（2026-11-15），捆绑 CLI 0.27.4；仓库最近推送 2026-11-16。存在 `v1.0.0-preview` 分支，结合 Qoder 的 agent harness 与 Qwen Code。注意 README 中的日期可能包含未来/测试数据，需以仓库实际提交为准。
---

## ℹ️ 置信度与信息盲区

- 置信度：**medium**
- 信息盲区：README 未提供具体 benchmark/evaluation 数据，仅提到 docs/evaluation.md 存在；未说明默认模型上下文长度、token 成本或本地模型资源要求；桌面应用是否为开源、具体分发方式未在 README 详述（仅链接 Releases）；Qwen 账号订阅费用与可用模型列表需查阅外部文档