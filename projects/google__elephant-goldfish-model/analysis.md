## 它是什么
Elephant-Goldfish Model（EGM）是一个开源插件，面向 AI 编码助手，用于规范驱动的软件设计评审。核心思想：大象（Elephant）负责持有项目上下文和起草规范文档；金鱼（Goldfish）评审者脱离先前对话，用全新视角审查文档和源码，暴露未说出的假设和盲点；用户做架构权衡和最终批准。提供七个技能：brainstorm、draft、resolve、bootstrap、review、review-loop、drift-report。

## 为什么火
Star 2 万+，Google 出品（非官方支持），解决 AI 编码助手在长上下文设计评审中容易「自说自话」的问题。金鱼评审强制新开 subagent，模拟 fresh eyes，对 spec-driven development 有直接帮助，且跨多个主流 coding agent（Claude Code、Codex、Antigravity、Cursor 等）可安装，降低切换成本。

## 技术栈
仓库语言标为 Python，但作为插件，核心是 AI 助手的 skill 定义（Markdown+提示词+可能少量脚本）。支持 Claude、OpenAI/Codex、Antigravity、Cursor、OpenCode、GitHub Copilot 等运行环境适配器。具体 Python 代码未在 README 展开，可能用于插件打包或自动化验证。

## 核心能力
- 双角色工作流：大象吃上下文、起草，金鱼脱离上下文评审。
- 内置五阶段设计评审（review 技能）和可配置 reviewer 组（review-loop）。
- 漂移报告：对比文档与当前源码，发现文档过时。
- 引导式文档生成：从现有代码库 bootstrap 文档。
- 多 agent 插件生态：Claude Code、Codex、Antigravity 等。

## 适用场景
- 需要在实现前写好设计文档，并希望用 AI 辅助评审的团队。
- 用 Claude Code / Codex 等编码代理做 spec-driven development 的个人或团队。
- 已有设计文档随代码演进，需要检查漂移的项目。
- 对 AI 评审机制感兴趣，想研究 multi-agent 提示词工程的人。

## 同类对比
与直接让 Claude/ChatGPT 审查代码或设计不同，EGM 强制评审者不继承对话历史，减少确认偏误。相比一些仅提供 prompt 的仓库，EGM 是完整插件，有 skill 文件、文档标准、安装命令，跨 agent 适配。与 GitHub Copilot 自带评审不同，EGM 是开源可定制，且不锁定单一厂商。

## 版本动态
最新 v0.1.1（2026-11-06）更新插件清单，新增三个 OpenAI 插件起始提示，分离发布政策目的地；新增 TRIZ 创造性催化剂 reviewer，改进评审上下文处理和严重度保留；实验性支持 Cursor、OpenCode V1、GitHub Copilot 适配器。Release 校验通过 GitHub Actions，但端到端验证仍开放（issue #60）。
---

## ℹ️ 置信度与信息盲区

- 置信度：**medium**
- 信息盲区：无 benchmark 数据或效果评估指标；未说明 Python 代码具体作用（插件打包/验证脚本？）；端到端发布 ZIP 验证仍在 open（issue #60）；未提供支持的具体模型列表或 API 要求；未说明金鱼 reviewer 的具体提示词实现细节