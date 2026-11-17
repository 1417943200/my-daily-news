## 安装
按你使用的 harness 选择安装方式：
- Claude Code：`/plugin install superpowers@claude-plugins-official`（或先添加 `obra/superpowers-marketplace` 再装）
- Codex CLI：输入 `/plugins`，搜索 superpowers，选择 Install Plugin
- Cursor：在 Agent chat 中输入 `/add-plugin superpowers`
- Gemini CLI：`gemini extensions install https://github.com/obra/superpowers`
- 其他如 Codex App、Devin CLI、OpenCode、Qwen Code、Pi、Muse 等见 README 的 Installation 章节。

## 最小可用示例
安装并重启对应 harness 会话后，直接说：`Let's make a react todo list`。一个正常工作的安装会自动触发 brainstorming，先追问你想做什么、为什么，而不是立刻写代码；批准设计后，会自动进入计划、TDD、子代理执行和评审流程。

## 依赖前提
需要已安装至少一个受支持的编码 harness；因为会用到 git worktree，环境中应有 git；具体 Node/Python 等依赖因 harness 和项目而异，README 未统一说明。