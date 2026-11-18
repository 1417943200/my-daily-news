## 它是什么
SkillEvaluator 是 NVIDIA 开源的多层评估框架，针对 AI 代理技能和插件。它分三层：Tier1 静态验证（质量、安全、跨代理兼容），Tier2 语义去重，Tier3 实时代理评估（测量技能对任务结果的实际提升）。既可本地运行，也能通过 CI 模板集成到 GitHub/GitLab。

## 为什么火
代理技能生态缺乏统一标准，技能经常加载失败、内容重复、安全存疑或实际无效。SkillEvaluator 直接解决这些痛点：HarnessCheck 无需 API 密钥即可检测技能在 6 种主流代理（Claude Code、Codex、Copilot CLI 等）中的兼容性；CI 模板让团队零代码实现质量门禁。对多代理环境或维护技能库的团队非常实用。

## 技术栈
Python 3.12–3.14，CLI 工具，支持 pip/uv 安装。Tier1 集成多种扫描器：SkillSpector、Gitleaks、Bandit、Semgrep（可选）、pip-audit。Tier2/Tier3 需要 LLM（支持 NVIDIA Build 免费密钥或其他 provider），Tier3 还需要 Docker 沙箱。CI 模板支持 GitHub Actions 和 GitLab CI。

## 核心能力
- **Tier1 验证**：500+ 静态规则，覆盖质量、schema、版本、PII、许可证、Unicode、脚本 linting、安全扫描，多数检查无需 LLM 密钥。
- **HarnessCheck**：版本化配置，检查 6 种代理的发现路径、frontmatter、描述长度、调用设置、插件组件和冲突，并给出修复建议。
- **Tier2 去重**：使用嵌入和聊天模型检测技能内部及跨目录的语义重叠。
- **Tier3 实时评估**：对比有/无技能的任务结果，量化技能提升（lift），支持多个代理和后端（包括 NeMo Gym）。
- **CI 集成**：无需编写评估代码，复制模板即可在 PR 中自动运行质量与安全门禁，可选 PR 评论和报告发布。
- **质量配置**：可自定义 token 预算、描述限制、保留名术语、分数扣除等。

## 适用场景
- 开发或维护代理技能库的个人/团队，希望在合并前自动检查质量。
- 需要确保内部技能安全合规并兼容多种代理的企业。
- 研究或评估代理技能实际效果的学术/工业项目。
- 在 CI 流水线中持续监控技能变更，防止回归。

## 同类对比
相比简单的 SKILL.md lint 工具，SkillEvaluator 提供三层评估和跨代理兼容性，覆盖更全面。相比通用 LLM 评估框架，它专注于代理技能的静态特性和行为影响，HarnessCheck 是独特亮点。但 Tier2/Tier3 依赖 LLM 和 Docker，并非完全本地免费。目前未提供与其他同类工具的直接基准对比数据。

## 版本动态
v1.0.1 于 2026-11-18 发布，是 1.0 系列第一个完整发布。新增 HarnessCheck、NeMo Gym 集成、质量配置增强和报告刷新。项目 Star 3648，创建于 2026-06-24，更新活跃（最近推送同一天）。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：README 未提供 Tier2/Tier3 实际评估基准数据或精度对比；合成评估数据集生成的具体方法未在 README 中详细说明；安全扫描器的具体规则和覆盖率未列出；免费 NVIDIA Build 密钥的申请门槛和限额需查看官方条款；与类似工具（如单独使用 SkillSpector）的区分未详细对比