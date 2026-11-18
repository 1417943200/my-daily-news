## 它是什么
OpenAI 官方开源的 Codex Security CLI 与 TypeScript SDK，用于在代码库中发现、验证和修复安全漏洞。定位偏 AI 辅助应用安全，既能本地扫描，也能接入 Codex 工作流、CI 与容器化批量任务。

## 为什么火
Star 14k+，2026-07 创建，到 2026-11 已迭代到 npm-v0.10.1。它解决传统扫描只报漏洞、不负责验证/修复的链路问题；扫描、验证、补丁、策略生成和第三方结果导入都在一个 SDK/CLI 里完成。

## 技术栈
TypeScript 编写，CLI 名为 `cs` / `codex-security`，npm 包为 `@openai/codex-security`。要求 Node.js 22.13+（22.x）或 24.x/26.x，以及 Python 3.10+（3.10 另需 tomli）。模型侧支持 OpenAI、Amazon Bedrock、OpenRouter、Fireworks AI、Cheaper Inference。本地 findings 可持久化，也可对接自定义 findings-url。

## 核心能力
- 扫描模式：仓库全量、指定 `--path`、diff 基线扫描、Deep Scan（重复标准扫描并去重）。
- 结果处理：验证候选发现、生成补丁、验证已有修复；可按自己的严重度 rubic 评估，并从源码和 Git 历史建议 owner。
- 策略与威胁建模：生成/更新 `SECURITY.md`，保存并导出 threat model。
- 第三方导入：AWS Continuum、CrowdStrike Falcon Cloud Security IaC、ServiceNow、Tenable 等，可本地保存或发布到 Codex Security Cloud。
- 集成与导出：Linear/Jira/GitHub 追踪、GitHub Actions、Docker Compose 批量扫描；导出 SARIF/JSON/CSV。
- 配置：支持 `scan.exclude_paths` 排除路径；root/组件级 `SECURITY.md` 作为扫描指导。

## 适用场景
- 想在本地 CLI/CI 中持续做 AI 安全扫描的工程团队。
- 需要从发现问题走到验证、补丁、跟踪的 DevSecOps 流程。
- 多仓库应用，需要按系统跨仓库 review 或批量任务。
- 已用 Codex 或 ChatGPT Cyber，希望用插件在会话内发起扫描。

## 同类对比
对比传统规则型 SAST，它更偏 AI 判断与自然语言工作流，并内置验证、补丁生成和第三方导入。但 README 未给误报率/召回率 benchmark，无法做质量定量对比。相比需要自配模型的本地 agent，它自带 CLI/SDK/CI Action 和云导入生态，开箱门槛更低。

## 版本动态
`npm-v0.10.1`（2026-11-18）新增 exclude path；`cs import continuum` 可采集 AWS Continuum findings 并用于攻击路径分析；Deep Scan 在触发 misalignment policy refusal 时停止并报告；威胁建模会验证测试中或已删除行出现的路由是否仍被服务。升级注意：内置 `collect_continuum.py` 应改用 `cs import continuum ...` CLI。
---

## ℹ️ 置信度与信息盲区

- 置信度：**medium**
- 信息盲区：README 未提供漏洞检测准确率、召回率或第三方 benchmark 数据；未说明各扫描模式的 token/成本上限，仅提到可用 --max-time 和 GitHub Action 示例中约 $5 限制；未展开本地 findings 存储格式、数据库迁移与兼容性细节；Codex Security Cloud 的账号可用范围与资格条件未详细说明