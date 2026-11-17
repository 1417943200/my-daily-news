## 安装

macOS / Linux / WSL：
```
curl -fsSL https://plannotator.ai/install.sh | bash
```

Windows PowerShell：
```
irm https://plannotator.ai/install.ps1 | iex
```

安装器会下载二进制并自动检测已安装的 agent，配置 hooks、slash commands 和 skills。只想装二进制可用：
```
curl -fsSL https://plannotator.ai/install.sh | bash -s -- --minimal
```

## 最小可用示例

1. 启动收件箱：
```
plannotator inbox
```

2. 在 Claude Code 中注释本地文档：
```
/plannotator-annotate README.md
```

3. 审查未提交改动：
```
/plannotator-review
```

4. 查看或重开会话：
```
plannotator sessions
plannotator sessions --open 1
```

## 依赖前提

- 至少安装一个受支持的编码 agent：Claude Code、Codex、Gemini CLI、OpenCode、Copilot CLI、Amp、Droid、Kiro、Pi 等
- 系统：macOS、Linux、WSL 或 Windows PowerShell
- 代码审查依赖本地 Git 仓库；远端 PR/MR 需要 GitHub/GitLab；GitButler/Perforce/jj 用户需装对应工具
- 完整安装会访问 GitHub Releases，可能联系 GitHub API 与 npm；介意网络边界可先走 --minimal