## 它是什么
SoduWork 是面向团队及 AI agent 的引擎，定位为“多harness、多agent、自托管”。它把一次 AI 交互定义为一个“请求”（request），强调“请求结束于请求者签收”，而非聊天得到答案即结束。核心是把 agent 工作纳入带有验收标准、AI 审查和人工签署的流程，并支持将成功经验保存为可复用插件。

## 为什么火
- 解决AI输出信任问题：设置验收标准、独立AI审查、人工签收，避免“快输出慢信任”。
- 团队知识沉淀：将一次成功的协作保存为插件，团队复用并持续改进。
- 多harness支持：可与 Pi、OpenCode、DeepSeek Harness、Qwen Code、Kimi Code、Codex Harness、Codex 等协同，切换harness保留历史与工作目录。
- 自托管、MIT许可，适合对数据主权有要求的团队。

## 技术栈
从README和主题标签可推断：
- 客户端：Electron（桌面客户端）
- 后端：FastAPI（Python），搭配 PostgreSQL（Docker部署）
- 运行时依赖：Python 3.12+、Node.js 22.19+、Git
- 协议/集成：Agent Client Protocol (ACP)、MCP 主题；支持多harness适配器
- 部署：源码启动或 Docker Compose（ops/self-host/deploy.py）

## 核心能力
- 请求与验收闭环：每个请求携带验收标准，独立 AI 审查，最终由请求者签收。
- 多harness编排：同一工作流中可切换不同 agent 运行时和模型，插件横跨harness执行。
- 插件系统：将成功的方法保存为插件，经审核后授权给团队或个人，可撤销。
- 治理与审计：角色、用量、成本和审计日志。
- 团队协作：人员与 AI 协作，可分配给同事或 agent，全程记录“谁做了什么”。
- 并行执行：不同 issue 可在不同 agent 上并行运行，包括云 runner。

## 适用场景
- 需要自托管、数据不出内网的团队使用 AI agent。
- 希望把 AI 输出纳入验收流程（如软件开发、内容生成）并留存可复用方法。
- 团队内部统一 AI 工具标准、治理插件分享和权限管理。
- 个人开发者也可用它管理多harness、多模型的工作。

## 同类对比
README 未直接列出竞品名称。从定位看，它对比“单一聊天界面/单一agent框架”：
- 相比通用聊天工具，它强调请求-审查-签收闭环和团队治理。
- 相比纯 agent 编排框架，它附带桌面客户端、管理控制台、插件市场和审计能力。
- 具体与 LangChain、AutoGPT、CrewAI 等工具的差异未在 README 中给出，需进一步核实。

## 版本动态
- 项目创建于 2026-10-29，最近推送 2026-11-18，最新 Release v1.13.18（2026-11-18）。
- Release 说明提到 Client + Hub release，附有 release-manifest.json 提供校验和与验收范围。
- 当前处于 public beta，README 建议评估后再用于生产。
---

## ℹ️ 置信度与信息盲区

- 置信度：**medium**
- 信息盲区：README 未提供与其他具体竞品（LangChain、AutoGPT、CrewAI 等）的对比。；未提供 benchmark、性能或准确率数据。；Hub 与客户端、各 harness 之间的详细通信协议未在 README 中展开。；插件系统、权限和审计的具体实现细节未说明。；Docker 部署中反向代理的具体配置（如 Nginx/Caddy 示例）未提供。