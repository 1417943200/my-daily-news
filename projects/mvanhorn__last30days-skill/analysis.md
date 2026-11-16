## 它是什么
`/last30days` 是一个 AI agent 技能（skill），让 AI 助手能并行搜索 Reddit、X、YouTube、Hacker News、Polymarket、GitHub 等 50+ 平台的最近 30 天内容，按点赞、转发、观看、真实资金等参与度信号评分，并由 AI “法官” 综合成一份简报。它作为一个可安装的技能包运行在 Claude Code、Codex、Cursor、Copilot、Gemini CLI 等 50+ 个 agent 宿主上，安装后零配置即可使用 Reddit、HN、Polymarket、GitHub，运行一次向导可解锁更多源。

## 为什么火
该项目在 GitHub 上获得 68070 star，曾登上 Trending 第一。它切中的痛点是：Google 聚合的是编辑和 SEO 内容，ChatGPT 有 Reddit 协议但搜不到 X/TikTok，Gemini 有 YouTube 但缺 Reddit，每个平台都是数据孤岛。`/last30days` 把这些孤岛桥接起来，让 agent 能跨平台搜索并对比，用数百万用户每天的点赞和钱包投票作为排序信号，提供的是“人”在关注什么，而不是编辑在写什么。

## 技术栈
- 语言：Python
- 分发：作为 agent skill，通过 Claude Code 插件市场或 `npx skills add` 安装
- 核心规范：`skills/last30days/SKILL.md` 是运行时真相来源
- 扩展工具：部分数据源依赖本地 CLI（如 `arxiv-pp-cli`、`techmeme-pp-cli`），首次运行向导会安装
- 零配置源：Reddit、HN、Polymarket、GitHub 直接可用；其他需 API keys 或浏览器会话

## 核心能力
- 多源并行搜索：覆盖社交（Reddit/X/YouTube/TikTok/Instagram/LinkedIn/Bluesky 等）、技术（GitHub/HN/arXiv/Techmeme）、金融（Polymarket/Yahoo Finance/StockTwits）、商业信号（Meta Ads/Trustpilot/Amazon）等
- 参与度评分：用 upvotes、likes、views、odds 等真实互动排序，而非 SEO
- AI 综合：agent 对结果进行筛选和总结，输出简明的 `grounded summary`
- 专题模式：人物调研、公司招聘信号、专利分析、产品对比、趋势发现（`--hiring-signals`、`? what's exploding in AI agents?`）
- 可扩展性：50+ 宿主，提供插件机制，可新增源

## 适用场景
- 会议/销售前快速调研一个人或公司的近期动态
- 发现爆发中的话题（AI 领域变化快）
- 对比工具、产品或竞品
- 追踪热点事件（如名人、地缘政治）
- 分析公司的招聘和专利作为前瞻信号

## 同类对比
- vs Google 搜索：Google 基于编辑和 SEO 索引，缺少社交评论和实时热度；`/last30days` 直接以用户参与度排序
- vs ChatGPT 搜索：ChatGPT 有 Reddit 合作但无法搜索 X、TikTok 等；本技能可同时接入多个平台
- vs Gemini：拥有 YouTube 但缺乏 Reddit 原生数据；本技能桥接多个孤岛
- vs Perplexity：Perplexity 提供 AI 搜索，但本技能将其作为一个来源之一，并叠加了金融、社交等信号

## 版本动态
最新版本 v4.2.1（2026-11-16）主要是一轮修复：修正 YouTube 评论开关、Reddit 评论树读取、JSON 提取拒绝非对象、GitHub issue 评论按 reactions 排序、保存后缀清理等。多位新贡献者参与。项目迭代频繁，持续维护，反映了社区活跃度。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：README 未详细说明 Python 依赖清单和内部模块结构；未提供搜索质量评估或 benchmark 数据（docs/search-quality-eval.md 存在但未在 README 展示）；未说明各平台 API 调用的频率限制、重试和成本控制机制；未说明用户 API keys 的存储位置和安全处理方式；某些数据源的接入细节（如 Telegram、Truth Social、Amazon）需要查阅 CONFIGURATION.md，README 只做了概述