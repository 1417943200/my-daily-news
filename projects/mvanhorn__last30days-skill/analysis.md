## 它是什么
一个AI agent技能/插件，让Claude Code等agent能够并行搜索Reddit、X、YouTube、TikTok、Hacker News、Polymarket等20多个平台，根据真实用户参与度（upvotes、likes、真实资金）评分，而非编辑或SEO。核心是“search people, not editors”。

## 为什么火
Star 68905，GitHub Trending #1，最近活跃。聚合多个平台解决单一AI无法访问全部社交数据的问题，用户自己带key和浏览器会话，agent桥接这些平台。对做研究、会议准备、趋势发现的人很有用，尤其AI领域从业者。

## 技术栈
Python（仓库语言）。作为Claude Code插件和npx skills安装，支持50+ Agent Skills hosts。具体依赖和实现未在README截断部分详细说明。

## 核心能力
- 多源并行搜索：Reddit、X、YouTube、TikTok、Instagram Reels、HN、Polymarket、GitHub、Digg、arXiv、Techmemo、Yahoo Finance、LinkedIn、Meta Ads、StockTwits、Threads、Pinterest、小红书、Bluesky、Perplexity、DEV、Truth Social、Telegram、Trustpilot、Amazon、DripStack、Jobs/careers pages、Patents、Local corpus、Web。
- 参与度评分：upvotes、likes、views、odds等。
- AI代理合成摘要。
- 发现模式：寻找爆发话题。
- 针对公司：招聘信号、专利信号、股价表现等。

## 适用场景
- 会议前调研人物或公司最近30天动态。
- 公司产品开发前的信号挖掘（招聘/专利）。
- 趋势发现（AI领域等）。
- 事件爆发后快速了解舆论（如Kanye West）。

## 同类对比
对比Google等编辑/SEO驱动搜索；单一AI如ChatGPT/Claude/Gemini各自有平台合作限制，无法覆盖全部社交平台。last30days利用用户自己的凭据和浏览器会话，让agent访问所有平台，并进行参与度加权。

## 版本动态
v4.3.2 (2026-11-17) 最新，主要包括文档波斯语翻译、修复X浏览器cookies、Reddit archive部分报告、移除无效transcription key、Windows CLI解析、Exa功能增强等。仓库活跃，贡献者多。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：具体实现架构（如agent调用方式、Python库依赖）未在README截断部分展示。；X、YouTube、TikTok等源的具体认证配置细节不完全明确。；性能、可靠性、响应时间等未提及。；未提供与传统搜索对比的量化benchmark数据。；本地语料库、Amazon等源的具体使用方法可能需查阅CONFIGURATION.md或SKILL.md。