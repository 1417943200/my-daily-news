## 它是什么

Claude-BugHunter 是一个针对 Claude Code Agent Skills 系统的技能包，用于漏洞赏金狩猎和外部红队工作。包含 83 个技能、15 个 slash 命令、681 个从 HackerOne 披露报告提炼的攻击模式（24 类漏洞），以及企业身份与基础设施攻击矩阵。

四层结构：
- **Think**：方法论与红队思维（bb-methodology、redteam-mindset）
- **Hunt webapps**：58 个 hunt-* 技能，覆盖 OWASP 类别及具体技术栈
- **Hit the perimeter**：企业平台攻击链，如 M365/Entra、Okta、vCenter、SSL-VPN 等
- **Ship it**：验证、报告、证据卫生，含 7-Question Gate 与 VRT 映射

技能通过主题自动触发，不需要按名称调用。

## 为什么火

AI 编码助手在安全测试中的自动化需求激增，但多数人不知道如何把漏洞挖掘经验转化为可执行提示。该仓库将大量实战漏洞报告提炼为结构化技能，直接嵌入 Claude Code 工作流，大幅降低整理成本。同时它支持多 harness，一次安装可通用于 Claude Code、OpenCode、Codex CLI 等。

## 技术栈

- Python（cbh CLI、脚本）
- Agent Skills 格式（SKILL.md）
- Claude Code 插件系统
- Burp MCP 集成
- GitHub Actions CI（skill-linter、star-history 自动刷新）

## 核心能力

- 58 个 hunt-* 技能覆盖 XSS、SQLi、SSRF、IDOR、LFI、SSTI、XXE、CORS、OAuth 等
- 企业平台攻击矩阵：M365/Entra、Okta、云 IAM、vCenter、企业 VPN、APK/iOS 红队
- 7-Question Gate 验证流程，强制检查范围、影响接受度、重复项
- 报告模板适配 HackerOne、Bugcrowd（VRT）、Intigriti、Immunefi 及红队交付格式
- /hunt 脚手架生成 engagement 文件夹结构，cbh CLI 提供终端原生 runner
- 多 harness 支持：Claude Code、OpenCode、OpenAI Codex CLI、Hermes Agent、Google AntiGravity

## 适用场景

- 漏洞赏金（HackerOne、Bugcrowd 等）
- 外部 Web 应用/API 渗透测试
- 授权红队初始访问（互联网暴露面）
- 云配置错误与后凭证提权（公共 S3、IMDS、STS AssumeRole）
- 侦察与 OSINT（子域名、证书透明度、JS 分析、密钥扫描）
- 安全报告撰写与证据卫生

明确排除：内部 Active Directory 攻击、C2 框架、后渗透/持久化/横向移动、规避技术、iOS/二进制/内核漏洞。

## 同类对比

与手动收集方法论笔记或 Burp 插件不同，它直接集成到 Claude Code 的 Agent 工作流，按主题自动加载，覆盖广且带验证门。相比其他通用安全提示库，它有明确的攻击模式引用（433 条可审计），并支持多 harness，但需要 Claude Code 或兼容 Agent 环境。其价值在于知识层而非工具层，仍需配合实际扫描器/代理使用。

## 版本动态

最新 Release v2.1（2026-06-05）。
- 新增 20 个 hunt-* 技能（hunt-lfi、hunt-nosqli、hunt-deserialization 等），总数从 71 提升至 83（描述处写 82，存在不一致）
- 增加 CI skill-linter，校验 SKILL.md 并阻断泄露密钥与客户标识
- 新增文档站点与可搜索技能目录
- 修复自身代码路径遍历、任意文件写入、Shell 注入等安全漏洞
- 新增 Azure App Service 接管指纹、function-level access control 部分
- Sponsor 为 APISMART 等，但核心功能与赞助无关

版本数字在不同位置有出入（82 vs 83，51→71 可能为中间版本），建议以仓库实际文件为准。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：README 描述中技能数量 83，仓库简介写 82，Release 说明从 51→71 提升，数字不一致，无法确定准确总数；Anthropic runtime cyber safeguards 部分被截断，具体限制未说明；未提供 benchmark 或实际效果数据（如漏洞发现率、节省时间等）；Sponsor APISMART 与 ThreatWatch360 对项目的影响未明确；多 harness 支持中 slash commands 和 /hunt 引擎仅限 Claude Code，其他 harness 只加载知识层，具体行为差异未详细测试