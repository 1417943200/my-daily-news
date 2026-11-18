## 它是什么
kwant 是一个开源（AGPL-3.0）自托管 AI bot 团队管理器，打包为单个 Rust 二进制，内嵌 React Web UI。可以在本地 Mac/Linux/Windows 或自有服务器运行，连接自己的 Claude/Codex/Grok CLI 或 API key，让多个 bot 在 spaces 中协作。

## 为什么火
GitHub 上 699 star，一个月内从 0.9.0 迭代到 0.9.25，说明作者非常活跃。它切中了对 AI 自动化有控制欲的极客：不像 Grok Bot/Claude Duet 把账号和任务交给云服务，kwant 让你自托管，保留账号与数据主权。此外它强调“验证”而非“相信”：任务只有在 kwant 自己运行检查后才标记 Verified，有二次检查机制，这对自动化可靠性有吸引力。

## 技术栈
- 后端：Rust（Tokio、Axum、SQLite）
- 前端：React Web 应用，嵌入在同一个二进制中
- 部署：macOS universal app、Linux .deb/AppImage、服务器二进制或 Docker、Windows beta
- 集成：Claude/Codex/Grok CLI 或自有 API key；浏览器自动化；MCP API；Composio 应用/工具目录

## 核心能力
- 多 bot 团队：一个空间里可创建多个 bot，@mention 交接工作；有 Assistant/Researcher/Writer 等预设。
- 验证与审批：Inbox 中的 To review 按风险排序，显示 Pass/Fail/Needs you 等结论和证据；高风险管理会触发另一模型的二次检查（在干净副本中重新运行检查）；支持 Approve/Send back/Roll back。
- 浏览器自动化：bot 可打开独立 job page 登录、操作网页，支持 Point 指向页面元素、处理验证码弹窗、后续版本中团队浏览器页隔离。
- 多空间与多账号：不同 spaces 分开工作/家庭，各自 bots 和连接；支持 Apps & accounts 连接多个 AI 账号，查看用量与限流。
- 开发辅助：Dev desk、worktree、PR 卡行内注释、CI 失败回传、Fix-it 消息等。
- Routines 与调度：例行任务、每周安排、Mission board 等。
- 自托管与隐私：单二进制，离线可运行（除外部 AI 调用），数据存本地 SQLite。

## 适用场景
- 想要个人 AI 助理团队自动化日常任务、网页操作、跨账号管理的极客/开发者。
- 需要审批工作流的自动化（设计、测试、开发任务）。
- 反感云服务抓取账号与数据、希望自己掌控的自托管爱好者。
- 已经使用 Claude/Codex/Grok CLI 的用户，想要一个统一的多 bot 调度层。

## 同类对比
相对于 Grok Bot、Claude Duet、OpenAI dots 等封闭/云托管机器人，kwant 的优势是：AGPL-3.0 开源、自托管、无官方 token（README 强调没有 token）、数据本地化、透明验证流程。劣势或风险是：需要自己搞定 API/账号和部署，macOS 应用未公证，Windows 版 beta，大量功能还在快速变化中，文档可能跟不上。同类项目中，它更接近“个人多 agent 编排器 + 浏览器自动化”的定位，而不是简单的聊天机器人。

## 版本动态
截至 2026-11-18，最新 release 为 v0.9.25（macOS/Linux/Windows）。0.9 系列在一个月内密集推出：0.9.0 引入 Inbox 审核与二次检查，0.9.1-0.9.12 先后加入 handoff 无限制、团队浏览器页面隔离、失败重试、预算、团队建议、打字状态、预设 @helpers、用量图表、PR 卡片路由等。但 README 截断至 0.9.12，0.9.13-0.9.25 的具体变更未在本次材料中展示；从 docs 目录（如 payments、saved-passwords、zombie-hunter、parallel-universe）可窥见功能还在向支付、密码、异常清理等方向扩展。建议关注 Changelog 和 Discussions。
---

## ℹ️ 置信度与信息盲区

- 置信度：**medium**
- 信息盲区：README 截断至 0.9.12，0.9.13-0.9.25 的具体变更未展示，版本动态可能有遗漏；docs 目录中大量功能（payments、saved-passwords、zombie-hunter、parallel-universe 等）仅见文件名，未在截断 README 中展开；未提供推荐硬件配置或资源占用数据；未列出全部可连接的 AI 账号/服务清单，只提到 Claude/Codex/Grok CLI 或自有 API key；无 benchmark 或性能指标