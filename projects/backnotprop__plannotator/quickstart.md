## 安装
```bash
curl -fsSL https://plannotator.ai/install.sh | bash
# 或 Windows PowerShell:
# irm https://plannotator.ai/install.ps1 | iex
```

## 最小可用示例
```bash
# 1. 启动 Inbox（多 agent 收件箱）
plannotator inbox
# 2. 在支持的 agent（如 Claude Code）中使用斜杠命令
/plannotator-annotate README.md
/plannotator-review
# 3. 审查远程 PR
/plannotator-review <github-pr-url>
```

## 依赖前提
- macOS / Linux / WSL 或 Windows（原生 Windows 上 Codex hooks 实验性）
- 至少一个支持的 AI 编码 agent（如 Claude Code、Codex、Gemini CLI 等）
- 安装脚本需要网络下载二进制，可选从 GitHub/npm 获取资源
- 想仅安装二进制可用 `--minimal`