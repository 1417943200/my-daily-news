## 它是什么
Cursor 官方插件规范与插件集合仓库，每个插件以根目录下独立目录组织，通过 `.cursor-plugin/plugin.json` 声明清单。README 表格列出 70+ 插件，覆盖开发者工具、生产力、集成三大类，作者包括 Cursor 官方及 Eric Zakariasson、Lauren Tan、Dylan Gattey 等社区/个人作者。

## 为什么火
- 官方背书：由 Cursor 官方维护规范与一批官方插件，降低插件开发/使用门槛。
- 生态广度：一次性覆盖 Google Workspace、GitHub、Salesforce、HubSpot、X、Meta Ads、邮件营销、招聘等大量 SaaS。
- 面向 Agent 工作流：插件描述大量涉及搜索、读取、创建、查询、审计、并行子代理等，直接服务于编码代理执行真实任务。

## 技术栈
- 语言：TypeScript
- 清单：`.cursor-plugin/plugin.json`
- 目录结构：每插件一个根目录，独立 manifest
- README 未说明运行时、依赖安装、鉴权方式或 SDK 细节。

## 核心能力
- 开发者工具类插件：教学、持续学习、团队套件、安全/正确性审计（thermos）、PR 审查画布、文档画布、并行云代理编排、CLI 设计模式、SDK、Grok 语音等。
- 集成类插件：Google 全家桶、GitHub、Salesforce、HubSpot、Intercom、Zoom、X、Meta Ads、招聘/邮件营销/财务等，描述多为“搜索/读取/创建/更新/管理”型操作。
- 生产力类插件：Gmail、Drive、Calendar、Docs、Sheets、Slides、Teams、SharePoint 等。
- 插件开发辅助：`create-plugin` 用于脚手架和校验新插件；`agent-compatibility` 提供 CLI 兼容性扫描与审计。

## 适用场景
- 在 Cursor 中让 Agent 直接操作常用 SaaS（邮件、日历、CRM、广告、招聘等）。
- 代码审查、文档渲染、团队 CI/发布/本地自动化。
- 需要参考官方插件规范或脚手架开发自定义 Cursor 插件。

## 同类对比
- 相对于自己拼 MCP 或其他 Agent 插件生态，此仓库的差异点在于：Cursor 官方规范、插件清单标准化、一站式集成数量多。
- README 未提供与其他插件体系（如 MCP、Claude Skills/Plugins）的对比，无法量化优势。

## 版本动态
- 仓库创建于 2026-01-23，最近推送 2026-11-18，说明 10 个月内保持活跃。
- Star 17k+，社区关注度高。
- README 未提供具体版本号、发布节奏或路线图。
---

## ℹ️ 置信度与信息盲区

- 置信度：**medium**
- 信息盲区：README 截断于插件列表中间，可能缺少安装、鉴权、开发、发布等章节；未提供许可证信息（许可为 None），无法判断使用限制；未提供主页链接；未说明插件运行时依赖、部署方式、API 凭据配置；无 benchmark、性能或可靠性数据