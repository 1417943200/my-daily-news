## 它是什么
Plannotator 是一个本地、基于浏览器的 AI 编码代理审查界面，支持标注计划、规格、Markdown、HTML 等工件，审查本地/远程代码差异和 PR，并将反馈直接发送回代理。它通过插件、hooks 和命令与 Claude Code、Codex、Copilot CLI、Gemini CLI、OpenCode 等集成，也支持个人助理代理。新版 Plannotator Inbox 作为多 agent 的统一收件箱。

## 为什么火
- 13.4k star（截至数据），快速迭代（v0.28.63 到 v0.29.0 多个功能发布），解决真实痛点：多代理产出物需要人工审查和决策。
- 极客友好：本地优先、浏览器界面、终端版本（Herdr Annotate/TUI）、支持多种 VCS（Git, GitButler, Jujutsu, Perforce, GitHub, GitLab）。

## 技术栈
- 语言：TypeScript
- 安装：安装脚本自动检测已安装 agent，配置 hooks/skills/slash 命令
- 集成方式：插件（Amp）、Claude Code plugin marketplace、Codex hooks/skills、MCP（用于其他 agent 接入 Inbox）
- 本地代理：支持本地 proxy 打开 live site

## 核心能力
- 文档/HTML 标注：标注本地文件、文件夹、URL、渲染 HTML，支持 live site
- Code Review：审查 uncommitted changes、GitHub PR、GitLab MR、GitButler workspace、patch file；提供 guided review（agent 将 diff 分章节）
- Inbox：统一收件箱，支持消息、问题、文件、引导式审查，异步回复，支持多 agent
- AI built in：审查时问 AI 或启动 AI 审查
- 共享：链接分享，小分享内嵌，大分享加密上传7天过期
- 终端版本：Herdr Annotate 与 Plannotator TUI

## 适用场景
- 使用 AI coding agents 的开发者/团队，需要审查 plans、specs、代码变更，并与 agent 闭环沟通
- 多 agent 环境（Claude Code + Codex + Pi 等）统一收口审查与反馈
- 本地优先、隐私敏感的用户（支持 Tailscale 限制本机账户）
- 代码评审工作流，特别是 GitButler/Jujutsu 等现代 VCS 用户

## 同类对比
README 未直接列出竞品。从定位看，较接近的可能是 GitHub/GitLab 内置 review、JetBrains IDE 审查工具、以及 agent 对话界面；Plannotator 的差异在于：本地浏览器跨 agent、统一收件箱、注释直接回流给 agent、支持多种 VCS 和现代工具（GitButler, Jujutsu, Perforce）。但需注意没有基准数据，且 Workspaces 团队功能仍在 waitlist。

## 版本动态
- 最新 v0.29.0（2026-11-18），Release notes 展示高频迭代：线程拖拽、标签、批量操作、Tailscale 支持、撤回回复、更小更新包、GitLab 文件级线程等。
- 说明项目活跃，持续加入跨 agent 支持和移动端适配（iPhone/iPad 滑动手势）。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：未提供性能指标或资源占用数据；Workspaces（团队共享空间）尚未公开，仍在 waitlist，无定价/细节；未说明对大型 PR/diff 的性能表现；未说明对非 TypeScript 项目的特殊依赖（如是否要求 Node.js 等）；README 未提供与竞品的直接对比或 benchmark