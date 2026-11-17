## 它是什么

Plannotator 是一个本地优先的浏览器审查面板，通过插件、钩子和 slash commands 直接接入 Claude Code、Codex、Gemini CLI、OpenCode 等 AI 编码代理。代理产出计划、Markdown、HTML 或 diff 时，浏览器会打开审查界面；人工注释、评论后可一键把反馈发回代理，作为下一轮输入，不长时间占用 agent 会话。

## 为什么火

13k+ Star 且发版频繁（v0.28.x），说明 AI 编码代理用户在人工把关和异步协作上有明显需求。它把多 agent 场景下分散的审查入口收拢到一个本地 Inbox，解决反馈滞后和会话阻塞问题，同时也支持 Git、GitButler、Jujutsu、Perforce 等常见 VCS。

## 技术栈

- 项目类型：TypeScript，本地可执行，浏览器 UI + 本地服务
- 集成方式：插件 / hooks / slash commands；Claude Code 通过插件市场安装，Codex 走 Stop hook，Pi 和 OpenCode 用插件，其他 agent 可通过 MCP 接入
- VCS 与平台：Git、GitButler、Jujutsu（jj）、Perforce（p4）、GitHub、GitLab
- 终端：Herdr Annotate 或独立 Plannotator TUI
- 分享：小内容内嵌链接，大内容加密上传并 7 天过期
- README 未明确前端框架、本地服务端口和运行时依赖

## 核心能力

- 注释任意文档：本地 Markdown 文件或文件夹、URL、HTML 渲染、代理最后一条消息
- 代码审查：uncommitted diff、GitHub PR、GitLab MR、GitButler workspace、静态 patch file；支持 Guided review 把 diff 分成章节并按重要程度排序
- Inbox 统一收件箱：代理可留下消息、问题、文件和引导审查，用户异步回复；回复发回提问的 agent 会话
- Plan mode：通过 agent hooks 自动打开计划审查，不需要手动命令
- 终端审查：Herdr 插件或 TUI 可在终端审 Markdown 与代理回复，反馈直接作为下一条消息
- AI 内置：审查时可问 AI，也可发起 AI review 在 diff 上发评论

## 适用场景

- 同时使用多个 AI 编码 agent 的个人开发者，想要一个统一审查入口
- 需要人工批准计划或 spec 后再让 agent 继续执行的流程
- 对代码 diff、PR、MR 做带注释的人工 review 并回传 agent
- 重视本地优先、不希望把工作代码上传到第三方审查服务的团队或个人

## 同类对比

Plannotator 类似一个跨 agent 的 review 中间层：功能上兼顾文档注释、代码审查和异步收件箱。相比单个 agent 自带 review 或 GitHub PR review，它更通用、更本地化，且不阻塞 agent 会话。README 未提供与具体工具的对照数据或 benchmark，选型前建议确认自己的 agent 组合和 VCS 是否在支持列表内。

## 版本动态

最近 Release 为 v0.28.67（2026-11-17）。从 Release 列表看迭代非常密集，持续补齐多 agent 覆盖（Grok Bot、Hermes、OpenClaw、Muse Code 等）、Inbox 体验（批量归档、优先级、tag、Tailscale 账户限制）、跨机器 tag 以及 GitLab 全文件评论等。项目处于快速活跃期。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：README 未给出前端框架、本地服务端口、运行时依赖等实现细节；未提供性能、资源占用或 benchmark 数据；分享加密上传的具体服务端点与安全细节未说明；没有与同类工具的直接对比数据；README 被截断，可能缺少高级配置或自托管部署说明