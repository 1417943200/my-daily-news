## 它是什么
kwant 是一个自托管的多 AI bot 团队平台，允许用户创建多个 bot 分工协作，通过 @mention 交接任务，自动完成任务或按日程运行。它在单个二进制内提供 Rust 后端和 React 前端，可运行在桌面或服务器上，兼容 Claude/Codex/Grok CLI 或自带 API key。

## 为什么火
项目处于 AI agent 自托管赛道，迎合数据私有化需求；功能覆盖多代理路由、人工审核、浏览器自动化、CI 集成等，且发布节奏极快（0.9 系列一个月内 19 个小版本）。作为开源产品，它直接对标 Grok Bot、Claude Duet、OpenAI dots 等商业服务，无订阅费用。不过 Star 尚只有 640，仍属早期。

## 技术栈
- 后端：Rust（Tokio, Axum, SQLite）
- 前端：React，编译后嵌入二进制
- 部署：桌面应用（macOS/Linux/Windows beta）、服务器二进制、Docker（ghcr.io/alexsergivan/kwnt）
- 桌面技术细节未明确（README 仅说明 Rust + React 嵌入二进制，未提及 Tauri/Electron）

## 核心能力
- **多代理协作**：bots 共享聊天，@mention 可多轮交接，自动路由到最合适的 bot。
- **任务验证**：Mission board 上的任务只有在 kwant 自己运行检查（如运行测试）通过后才会标记 Verified，不轻信 bot 自述。
- **人工审核**：Inbox 集中展示需要审批的工作，支持 Pass/Fail/Needs you 判定，可批量批准，高风险项由另一模型复查。
- **浏览器自动化**：bot 可操作浏览器完成登录、CAPTCHA、点击元素等，每个 bot job 独立页面且共享登录。
- **开发集成**：支持 worktree、PR 审查、CI 反馈、diff 行注释，适合辅助代码工作流。
- **空间与连接管理**：工作/家庭等独立空间，管理多 AI 账户、Composio、MCP 工具，支持月度预算。
- **运行灵活**：桌面、服务器、Docker、手机 PWA 均可使用。

## 适用场景
- 希望自托管 AI 代理、保持数据私有的个人或小团队。
- 需要自动化重复任务（研究、内容生成、回复）且要求人工审核的开发/运营人员。
- 希望多 AI 模型协作、交叉验证输出质量的复杂工作流。
- 已在用 Claude/Codex/Grok CLI 但需要统一编排和审批的用户。

## 同类对比
与 Grok Bot、Claude Duet、OpenAI dots 相比，kwant 的主要差异是开源、自托管、数据可控，不锁定单一 AI 供应商。其“验证靠运行检查”而非模型自报的机制更严格；但社区规模和生态完善度不如商业产品，且发布时间短，功能迭代中可能存在不稳定。

## 版本动态
0.9 系列更新非常密集（0.9.0～0.9.19），最新版本 mac-v0.9.19（2026-11-16）。关键演进包括：Inbox 审核、二次检查、浏览器自动化增强、CI 集成、worktree、连接管理、团队建议、预算控制、手机体验优化。提供 Mac universal、Linux deb/AppImage、Windows beta 和服务器安装方式。
---

## ℹ️ 置信度与信息盲区

- 置信度：**medium**
- 信息盲区：桌面应用具体技术栈未说明（是否 Tauri/Electron 不明）；未提供支持的 AI API 格式和模型提供者完整列表（仅提到 Claude/Codex/Grok CLI/自有 API key）；未提供性能数据或资源占用基准；多用户权限模型和团队规模限制未说明（可能面向个人）；未提供测试覆盖率或代码质量指标