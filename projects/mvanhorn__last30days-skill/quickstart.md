## 安装
- **Claude Code（推荐）**：
  ```
  /plugin marketplace add mvanhorn/last30days-skill
  /plugin install last30days
  ```
- **其他 50+ 宿主（Codex、Cursor、Copilot、Gemini CLI 等）**：
  ```
  npx skills add mvanhorn/last30days-skill -g
  ```
  （`-g` 全局安装，去掉则项目级）

## 最小可用示例
安装后直接输入：
```
/last30days Peter Steinberger
```
零配置下会搜索 Reddit、HN、Polymarket、GitHub 并给出摘要。运行一次向导可解锁 X、YouTube、TikTok、arXiv 等更多源。

## 依赖前提
- 基本无需额外依赖，Python 环境由 skill 自带管理
- 部分源需要对应 API keys（如 X、YouTube、TikTok）或本地工具（如 `arxiv-pp-cli`、`techmeme-pp-cli`），首次运行向导会引导安装
- 某些源（如 Telegram、Truth Social）需要显式 token 或自备服务