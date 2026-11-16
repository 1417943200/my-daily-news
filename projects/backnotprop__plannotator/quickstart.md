## 安装

macOS / Linux / WSL：
```bash
curl -fsSL https://plannotator.ai/install.sh | bash
```

Windows PowerShell：
```powershell
irm https://plannotator.ai/install.ps1 | iex
```

只想装二进制，不要任何 agent 配置：
```bash
curl -fsSL https://plannotator.ai/install.sh | bash -s -- --minimal
```

## 最小可用示例

```bash
plannotator inbox                               # 打开统一 Inbox
/plannotator-annotate README.md                 # 标注 markdown 文件
/plannotator-review                             # 审查未提交改动
plannotator review --patch-file reading.diff    # 审查静态 diff
plannotator sessions                            # 列出活动会话
```

Codex 用户把 slash command 换成 `!plannotator …`（如 `!plannotator review`）。

## 依赖前提

- 需要至少一个受支持的 agent：Claude Code、Codex、Copilot CLI、Gemini CLI、OpenCode、Kiro、Droid、Amp、DeepSeek Harness、Pi 等。
- Claude Code 安装后需额外执行 `/plugin marketplace add backnotprop/plannotator` 并安装插件，然后重启。
- Amp 需手动复制 `plannotator.ts` 到 `~/.config/amp/plugins/` 并 reload。
- README 未明确说明最低 OS 版本或是否需要额外安装 Node.js/Python 等运行时；以安装脚本实际输出为准。