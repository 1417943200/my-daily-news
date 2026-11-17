## 它是什么
LoopForge 是腾讯开源的自托管工作流平台，用于把 coding agent（CodeBuddy、Codex、Claude Code 等）编排成可复用交付流程。两条核心路径：在聊天里让 Main Bot 开 Docker 沙箱、委托子代理完成需求；把验证过的流程保存为 SOP，由 Agent、Script、Human-gate、sub-SOP 节点串行执行。

## 为什么火
解决“让 coding agent 修 bug，结果每次不一样”的问题：同一 SOP 每次走相同阶段和检查；规划、实现、评审、测试角色分离；关键节点有人工审批；运行可暂停、重试或从任意节点重跑。对已有 CI/CD 但缺 agent 治理的团队比较实用。

## 技术栈
后端 Go；安装/运行依赖 Git、Docker、Compose、Python 3、curl；发布镜像托管在 GHCR；沙箱默认复用安装镜像，也支持自定义 Dockerfile；支持本地执行机。

## 核心能力
- 聊天驱动：Main Bot 创建 conversation workspace，@角色/技能/需求/SOP，选择执行器和模型。
- SOP 引擎：Agent、Script、Human-gate、sub-SOP 节点；人工门禁可退回指定步骤。
- 多执行器：CodeBuddy、Codex、Claude Code、OpenCode、Cursor CLI、Antigravity、Kimi Code、Pi、DeepSeek Harness、ZCode。
- 权限与凭证：个人 key/共享 key；内置 GitHub OAuth；支持 SSH 仓库与 per-host user keys；凭证不写入 clone URL。
- 可观测：节点状态、工具轨迹、日志、产出物，以及需求维度的交付与成本报告。

## 适用场景
已有代码库需要 PR/MR 交付的团队；产品文档或新项目生成；需要可审批、可审计的 agentic 工作流；希望在自己基础设施上跑多 agent 协作的开发者。

## 同类对比
比直接使用 Claude Code/Codex CLI 多出 SOP 编排、人工审批、角色隔离和执行历史；对比通用 workflow 引擎更聚焦 SDLC 与 coding agent；相比 LangGraph/AutoGen 等 Python 编排库，更偏自托管产品形态。

## 版本动态
最近发布 v0.4.0，包含聊天中自动补装缺失 CLI、SSH 仓库私钥支持、安全收紧、调度任务 prompt 长度修复、运行中编辑 workspace、强制清理执行历史等。项目迭代速度较快，当前 Star 3k+。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：许可证信息不一致：仓库元数据为 NOASSERTION，但 README badge 和正文称 MIT，需查 LICENSE 文件确认；未提供 benchmark 或量化效果数据；未详细说明 native deployment 的资源要求和兼容性矩阵；未看到完整的多租户/权限模型细节