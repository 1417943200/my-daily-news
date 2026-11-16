## 安装
选择你的 coding agent：

**Antigravity CLI**
```sh
agy plugin install https://github.com/google/elephant-goldfish-model
```

**Claude Code**
```sh
claude plugin marketplace add google/elephant-goldfish-model
claude plugin install egm@egm
```

**Codex CLI**
```sh
codex plugin marketplace add google/elephant-goldfish-model
codex plugin add egm@egm
```

ChatGPT/Codex 桌面端通过插件商店安装；Antigravity App/IDE 运行 `/plugin`。

安装后启动新会话。依赖前提：已安装对应的 coding agent（Claude Code、Codex CLI、Antigravity CLI 等），并需要 agent 能创建 fresh subagents（金鱼评审必需）。

## 最小可用示例

**评审现有设计文档**
```text
/egm:egm-review docs/designs/webhooks.md
```
（Antigravity 和 Claude Code 使用 `/egm:` 前缀；Codex 从 skill picker 选择。）

**60 秒漂移检查**
```text
/egm:egm-drift-report docs/designs/
```

**完整设计流程**
1. 头脑风暴并生成概念简报
```text
/egm-brainstorm Add webhook delivery to this project.
```
2. 起草规范
```text
/egm-draft
```
3. 评审草稿
```text
/egm-review design_draft.md
```
4. 批准后让 agent 实现。

注意：brainstorm 和 review 需要会话能创建 fresh subagents。