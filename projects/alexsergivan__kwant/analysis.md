## 它是什么

kwant 是一个开源自托管的多智能体 AI 助手平台，以单个二进制提供桌面应用或服务器。它让多个 AI bot 共享聊天空间，通过 @提及 进行任务交接，并引入“核对/验证”机制：任务卡片只有在 kwant 实际运行检查后才标记为 Verified，而不是仅凭 bot 声称完成。定位为 Grok Bot、Claude Duet、OpenAI dots 等云端 bot 的开源替代，数据与运行环境由用户自己掌控。

## 为什么火

截至报告时 Star 数为 691（仓库创建于 2026-10-22，不到一个月），版本已迭代至 0.9.21，更新非常频繁。对极客的吸引力在于：①自托管、无官方 token，账户与数据在自己机器/服务器上；②把“工作流”概念引入 AI bot：handoff、审批、例行任务、spaces 隔离；③强调可核实性，不是简单黑盒自动回复。注意 Star 数与宣传性更新较多，实际稳定性与生态仍需自行验证。

## 技术栈

- **后端/核心**：Rust（Tokio、Axum、SQLite），编译为单二进制，React Web UI 嵌入其中。
- **部署形态**：macOS universal app（Apple silicon + Intel，macOS 11+）、Linux x86_64（.deb、AppImage、自托管服务器脚本/Docker）、Windows beta。
- **AI 接入**：可使用已有的 Claude、Codex 或 Grok CLI，或自带 API keys；浏览器自动化、MCP、Composio 等工具集成存在。
- **存储**：SQLite，默认数据目录 `~/.kwnt`（桌面版）。

## 核心能力

- **多智能体协作**：bot 之间通过 @提及 交接工作，团队持续运行直到任务完成；支持 spaces 隔离工作/生活。
- **验证与审批**：任务卡片通过“检查”变为 Verified；0.9+ 引入二次检查（另一模型在 clean copy 上重跑）、Inbox 审查、Approve/Send back/Roll back、Failed CI 反馈给 bot、Fix-it 等。
- **例行任务与调度**：Routines，从侧边栏打开，支持按周/日触发。
- **浏览器控制**：bot 可操作页面，Watch live、Point 点击页面元素、每个 bot 独立 job page、自动处理登录弹窗。
- **预算与用量**：每个 bot 可设置月度 token/美元预算，达到 80% 提醒、100% 暂停；有 AI use 用量视图（7/30 天）。
- **工具生态**：docs 包含 bot-actions、bot-browser、home-assistant、mcp-api、teams-api、payments、saved-passwords 等，集成面较广。

## 适用场景

- 个人自动化：管理多账户、重复例行任务、跨平台信息处理。
- 小团队/开发：代码审查、PR 反馈、worktree 隔离、CI 状态跟踪。
- 自托管爱好者：需要数据本地存储、无第三方 token、可审计的工作流。
- 对 AI 操作有审批需求的场景：关键步骤需人工确认或二次检查。

## 同类对比

相对 Grok Bot、Claude Duet、OpenAI dots 等云端闭源产品，kwant 的核心差异在自托管、开源（AGPL-3.0）与验证机制。但 README 未提供与这些产品在功能完成度、模型支持范围、错误率等方面的定量对比；生态和成熟度可能还不如大厂产品。同类开源多智能体项目（如 OpenBot 等）未在 README 中详细比较，无法判断相对优势。

## 版本动态

最新 Release 为 mac-v0.9.21（2026-11-17），Mac/Linux 桌面与服务器均已提供，Windows 仍为 beta。0.9 系列功能密集：0.9.0 引入 Inbox 审查与二次检查；0.9.2 团队持续运行、0.9.3 bot 独立 job page、0.9.4 失败后自动重试/Blocked 反馈、0.9.5 预算与 Composio 三步接入、0.9.6 Suggest a team、0.9.7 打字状态与引擎标记、0.9.8 预置 @helpers、0.9.9 浏览器 panel 与 AI use、0.9.10 限额显示与 Approve 按钮、0.9.11 Fix-it 与文档引用、0.9.12 Dev mode 前置。如此高频发布说明作者活跃，但也可能意味着功能稳定性需用户自行评估。
---

## ℹ️ 置信度与信息盲区

- 置信度：**medium**
- 信息盲区：完整配置流程（添加 AI 账户/API key 具体步骤）未在 README 截断部分展示，需查官方 docs/quickstart；未列出所有支持的 AI 模型/提供商完整清单；未见性能基准、内存/CPU 占用数据；bot 执行代码或文件操作的安全沙盒/隔离机制未详细说明；手机端“添加到主屏幕”的 PWA 功能边界未展开