## 它是什么

开源、自托管的团队聊天工具，定位为 Slack 替代。AI agents 不是侧边栏机器人，而是作为工作区成员进入频道和 DM，有角色、所有者和月度预算，模型调用会被记录。支持 Claude、ChatGPT/Codex、Gemini、Grok、OpenRouter 等，并通过 MCP 连接外部工具。提供 Web、桌面和手机端，默认 Docker Compose + Postgres 部署，AGPL-3.0。

## 为什么火

它解决团队沟通和 AI 执行割裂的问题：把代理放进真实工作流，代理在公开频道里干活、提问、等待审批，重要操作默认需要人类批准，而不是黑盒自动执行。相比给 Slack 外挂 bot，这个项目把审批、预算、电脑、浏览器、routines、memory 都做进产品里，开箱即用。自托管免费且无 license key，对隐私敏感团队有吸引力。仓库 2026-11-09 创建，约 9 天获得 1713 stars。

## 技术栈

- 服务端：Bun、Hono、Drizzle、PostgreSQL（pgvector）
- Web：React + Vite + TanStack
- 手机：Expo（iPhone/Android）
- 桌面：Tauri（macOS、Windows、Linux）
- 部署：Docker Compose；安装脚本可接入 Tailscale 私有 HTTPS，或使用 Caddy 公网域名；无 Docker 模式为 Beta

## 核心能力

- **频道/线程/DM**：公共/私有频道、与人和代理的 DM、线程；未 @提及的消息由 router 决定最多 4 个代理回答。
- **审批机制**：合并、部署、回滚及连接器标记的敏感操作必须由代理所有者或管理员批准，批准后只执行一次。
- **MCP 连接器**：官方支持 Linear、Sentry、Notion、Stripe 等一键接入，也可通过 URL 接入任意 MCP server；Composio 扩展 Google Drive、Calendar、Slack、Teams 等。
- **代理电脑与浏览器**：代理在已连接的电脑上执行命令/代码；浏览器为 Beta，可实时观看或接管登录/验证码。
- **Claude Code/Codex**：代理可在已连接电脑上使用本机登录的计划运行 Claude Code 或 Codex。
- **Routines/Memory/Wiki/Drive/Tasks**：定时或事件触发任务、长期记忆学习、带版本的知识库和文件、看板任务。
- **多语言与迁移**：14 种语言；可从 Grok Bot、ChatGPT dots、OpenBot.run 等导入 agents、skills、channels、routines 和 memory。

## 适用场景

适合小团队或个人私有化部署团队协作，尤其是需要 AI 实际执行开发、运维、知识整理等工作，同时要求审批留痕、预算可控的场景。也适合想从单机 agent 应用迁移到共享工作区的用户。数据敏感、不希望使用云端 AI 助手的企业可以用自己的模型 key 和 MCP 连接器组合。

## 同类对比

- **对比 Slack + AI bot**：agentes.chat 把代理视为一等成员，内建审批、预算、电脑/浏览器和记忆，不是外挂机器人。
- **对比单机 agent 应用**（Grok Bot、ChatGPT dots、OpenBot.run 等）：提供团队共享、多代理协作和导入迁移，且支持自托管。
- **对比通用 agent 框架**：更偏产品化，开箱即用，但深度扩展主要依赖 MCP 和已有连接器，自定义灵活性可能不如纯框架。

## 版本动态

- 最新版本 v0.1.6（2026-11-18）：气泡聊天样式中卡片随消息展示；修复手机端侧栏标题、工作行和消息栏视觉问题；operator API 可通过 email 回复成员支持请求，需 reveal token；更新法律条款。
- 仓库创建 2026-11-09，最近推送 2026-11-18，迭代速度较快。
- 手机端、桌面端、浏览器、邮箱、导入、无 Docker 部署均为 Beta，说明仍处于快速演进阶段。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：未提供 benchmark 或性能数据，也未明确最小内存/CPU/磁盘资源要求；未说明多租户数据隔离和权限模型的实现细节；手机、桌面、浏览器、邮箱、导入、无 Docker 部署均标记为 Beta，稳定性未经验证；未公开测试覆盖率、CI 通过率或安全审计报告；社区规模、贡献者活跃度及商业托管价格未在 README 中详细说明