## 它是什么
Superpowers 是一套面向 AI 编码代理的技能框架和软件开发方法论，由 Prime Radiant 的 Jesse Vincent 等人构建。它由一组可组合技能（brainstorming、writing-plans、test-driven-development 等）和启动指令组成，让代理在写代码前先澄清需求、制定计划、用 TDD 实现、子代理执行并评审。项目通过插件/扩展方式安装到多个编码 harness，如 Claude Code、Codex、Cursor、Gemini CLI 等。

## 为什么火
Star 数约 31.9 万，跨 15+ 编码 harness 支持。核心是强制改变编码代理的行为模式：代理不再“直接跳进写代码”，而是先退一步问你要什么、为什么，把需求写成可读 spec，批准后才制定计划，再进入子代理驱动开发和测试。v7.0.2 自述的盲测中，无意义提问从 41 降到 23，33/33 场景先挖出“为什么”，且批准前不构建。

## 技术栈
主要语言 Shell；以技能文件和脚本形式分发，通过各 harness 的插件市场或仓库安装，利用原生 skills 或兼容层加载。MIT 许可。

## 核心能力
- **brainstorming**：构建前先追问意图，只问会改变构建结果的必要问题，给出可选项和推荐；小改动在聊天里确认，大项目输出设计文档。
- **writing-plans**：把批准的设计拆成 2-5 分钟的小任务，每个任务包含精确文件路径、完整代码和验证步骤。
- **subagent-driven-development / executing-plans**：前者每个任务派新子代理并逐个评审（最彻底）；后者在当前会话内联执行全部任务，最后做一次整分支评审（最便宜）。
- **test-driven-development**：强制红-绿-重构，删除写在测试之前的代码。
- **requesting-code-review**：在任务之间按计划评审，严重问题阻断进度。
- **finishing-a-development-branch**：验证测试，提供合并/PR/保留/丢弃选项并清理 worktree。
- **using-git-worktrees**：设计批准后创建隔离工作区，跑项目 setup，确认干净测试基线。
- **diagnosing-superpowers**：会话异常时读取 transcript 并用行级证据报告问题，可导出脱敏 bundle。

## 适用场景
- 希望编码代理长时间自主工作却不偏离计划的团队和个人；
- 要求强制 TDD、代码评审和明确设计批准的工程流程；
- 同时使用多个编码 harness，希望用同一套方法论统一行为。

## 同类对比
相比在 Claude Code 里手动开 plan mode 或拼提示词，Superpowers 提供跨 harness 一致的强制技能触发和从需求到合并的完整生命周期；相比绑定单一后端的代理框架，它更偏方法论和插件化，不绑定模型供应商。README 提供了 v7.0.2 与自己旧版和 6.4.2 的盲测对比，但没有与 Aider/OpenHands 等第三方工具的量化对比。

## 版本动态
最新 Release v7.0.2（2026-11-03）主要调优 brainstorming：问题更少、先问 why、有选择时给出带推荐的选项；修复六个 harness 的 bootstrap 问题；强化 SDD 和 executing-plans 脚本防止指向错误仓库或任务；修复 `start-server.sh --project-dir .` 相对路径问题。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：README 未提供与 Aider/OpenHands 等第三方代理框架的量化对比；未说明各 harness 插件的具体版本兼容范围和安装失败排障步骤；盲测数据来自项目自述，未见独立可复现的公开基准；未列出所有技能文件的完整清单和触发条件细节