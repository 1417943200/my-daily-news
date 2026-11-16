## 它是什么

Plannotator 是本地、浏览器-based 的 AI 编程 agent 审查/注释层。通过插件、hooks、命令接入 Claude Code、Codex、Copilot CLI、Gemini CLI、OpenCode、Kiro、Droid、Amp、DeepSeek Harness、Pi 等；Inbox 还能接 Grok Bot、Muse、Hermes、OpenClaw 等个人助理。当 agent 提出决策、计划、HTML 或完成工作后，应用在浏览器打开，用户可标注、评论并把反馈发回 agent。另有终端版 Herdr Annotate / Plannotator TUI。

## 为什么火

Star 12489（给定数据），主要原因：多 agent 时代缺一个统一的人机审查界面；本地优先，不依赖 SaaS；支持主流 CLI agent 和 MCP；从计划、代码 review 到 Inbox 覆盖完整反馈闭环。对想“stay in the loop”的重度 agent 用户有直接价值。

## 技术栈

语言 TypeScript。形态为本地 CLI + 浏览器 UI，通过插件/hooks/slash commands/MCP 与各 agent 集成。安装脚本从 GitHub Releases 拉二进制，可 `--minimal` 只装二进制。README 未披露后端存储、渲染框架或数据库细节；只知道本地数据目录用于会话/标注，分享时小份内容存在链接内、大份加密上传 7 天过期。

## 核心能力

- Inbox：本地统一收件箱，agent 留消息/问题/文件/guided review，用户点选回答、注释文件、Send 回复，不阻塞 agent 会话。
- Annotate：标注 markdown/HTML/URL/文件夹，支持渲染本地站点和 hot reload。
- Code Review：审查未提交改动、GitHub PR、GitLab MR、GitButler 工作区、patch 文件；评论发回 agent；支持 Git、GitButler、Jujutsu、Perforce。
- Guided Review：AI 将大 diff 分章节，重要变更优先。
- Plan mode：通过 hooks 自动在 agent 创建计划时打开审查界面。
- 终端集成：Herdr Annotate 与 Plannotator TUI。

## 适用场景

- 同时管理多个 Claude Code/Codex/etc agent 会话，需要统一收件箱和决策留痕的个人开发者/小团队。
- 审查复杂 PR/MR 或本地改动，希望评论直接回流给 agent 执行。
- 让 agent 产出计划/HTML/文档后人工 review 再继续。
- 偏好本地运行、不想把代码和反馈传到第三方 SaaS 的用户。

## 同类对比

README 未直接点名竞争对手。相比单一 agent 内置的 plan mode 或 diff 工具，它的差异在跨 agent/跨 harness 的统一收件箱和注释回流；相比纯 Git review 工具，多了对计划、HTML、agent 消息等非 diff 内容的支持。因未提供 benchmark 或详细对标，具体优劣需自行验证。

## 版本动态

最新 Release v0.28.66（2026-11-16）。近期更新密集，包括：撤回 agent 未收到的回复、Tailscale 支持、T3 Code threads 的 Inbox 免配置、Artifacts 视频过滤器、GitLab 全文件评论、设置中配对 Grok Bot 等云 agent、Priority 和标签、Windows 上从 Inbox 启动 agent、规则、改善慢连接加载等。表明项目处于快速迭代期。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：README 未披露内部存储、数据库、渲染框架等实现细节；未说明除安装脚本外是否需要 Node.js 或其他运行时依赖；无 benchmark/性能数据，也未与同类工具做量化对比；大文件、多线程、多 agent 并发场景下的资源占用未给出参考