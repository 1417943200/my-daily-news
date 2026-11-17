## 安装
- Claude Code（推荐，自动更新）：
  ```
  /plugin marketplace add mvanhorn/last30days-skill
  /plugin install last30days
  ```
- Codex、Cursor、Copilot、Gemini CLI等：
  ```
  npx skills add mvanhorn/last30days-skill -g
  ```
  （`-g`全局安装；去掉则为当前项目）

## 最小可用示例
```
/last30days Peter Steinberger
```
或发现模式：
```
/last30days "what's exploding in AI agents?"
```

## 依赖前提
- 零配置：Reddit、HN、Polymarket、GitHub免费无需key。
- 设置向导解锁X、YouTube、TikTok等（需要自己的API key或浏览器会话）。
- 可选CLI工具：digg-pp-cli、arxiv-pp-cli、techmeme-pp-cli、yahoo-finance-pp-cli等可自动启用对应源。
- 部分源需明确opt-in，如Amazon需要Bright Data CLI，Telegram需要SCRAPECREATORS_API_KEY等。