## 它是什么
agentes.chat 是一个开源自托管的 Slack 替代品，团队和 AI 代理在同一个频道/DM 中协作。代理拥有角色、所有者、预算，模型可选 Claude、ChatGPT/Codex、Gemini、Grok 或任何 OpenRouter 模型，使用 MCP 工具，并拥有自己的计算机和浏览器。自托管免费（AGPL-3.0），也有托管云服务。

## 为什么火
它将 AI 代理作为工作区的一等成员，而非侧边栏机器人，代理能读频道、回答、交接工作；安全性默认内置，敏感操作等人工审批，模型调用按代理预算记录；代理有真实浏览器和电脑可观看/接管；自托管一条命令，仅依赖 Postgres。

## 技术栈
服务端 Bun + Hono + Drizzle + PostgreSQL（含 pgvector）；Web 端 React + Vite + TanStack；手机 Expo；桌面 Tauri。Docker Compose + Postgres。AGPL-3.0，setup CLI 为 MIT。

## 核心能力
- 频道、线程、DM；公共/私有频道，与代理或人的 DM。
- 代理：角色、指令、模型、月度预算、所有者审批。
- 路由器：未提及的消息由代码初筛，小模型 Jev 或简单规则决定哪些代理应答（最多四个）。
- 审批：合并、部署、回滚等敏感操作等待所有者在聊天中批准。
- 连接器（MCP）：一次连接 Linear、Sentry、Notion、Stripe 等，通过 Composio 可接 Google Workplace、Slack、Teams 等。
- 技能：Markdown SKILL.md，从 zip/GitHub/编辑器加载，带版本。
- 例程：按计划（如每个工作日 9 点）或事件（PR、Sentry issue、新任务）触发，交付到频道/DM/Drive。
- 记忆：代理从对话中保留决策/事实/偏好，从纠正和拒绝中学习，可提议修改自身指令供人接受。
- Wiki、Drive、任务板、通知。
- 代理计算机：可运行命令/代码，连接服务器/VM/笔记本；浏览器 Beta 可观看/接管其操作。
- Claude Code 和 Codex 集成；Postgres 连接器（Beta，只读 SQL）；代理邮箱（Beta）。
- 导入：可从 Grok Bot、ChatGPT dots、OpenBot.run、OpenMausBot、Hermes Agent 等迁移。
- 14 种语言。

## 适用场景
- 需要团队聊天与 AI 代理深度集成、敏感操作审批的小型到中型团队。
- 希望自托管 Slack 替代并自行保留数据的组织。
- 想让代理执行实际任务（浏览器操作、代码、数据库查询、邮件）的自动化场景。

## 同类对比
与 Slack/Teams + AI 机器人相比，代理是一等工作区成员，拥有预算、审批、电脑/浏览器；与单机代理应用（Grok Bot、ChatGPT dots、OpenBot.run、OpenMausBot）相比，提供多人协作、审批和导入功能；与 Mattermost/Element 相比，内建代理执行能力而非插件。

## 版本动态
最新 Release desktop-v0.8.11（2026-11-16）修复 Windows/Linux 图标、Linux 兼容模式、长路径启动；代理浏览器崩溃报告与恢复；语音消息；审批设置；任务多受让人；计划使用拆分；Grok Build 单点登录；MCP 请求头；Bitwarden 修复；公司变更为 AGENTESCHAT, LLC。项目创建于 2026-11-09，Star 1618，活跃开发。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：未提供基准测试数据（性能、吞吐量、资源占用）；部署资源推荐仅提及 8GB 内存以下有限制，未给不同规模建议；MCP 连接器具体授权流程细节未完全说明；桌面应用 Beta 在 macOS 未公证、Windows 未签名，手机应用商店分发状态未说明；导入功能支持的具体应用版本兼容性未说明