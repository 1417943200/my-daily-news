## 安装
**任意支持 skills 的 agent（推荐，需 Node.js 环境）**
```bash
npx skills add Dodaios/ste80-humanizer
```
或全局安装到指定 agent：
```bash
npx skills add Dodaios/ste80-humanizer --global --agent claude-code
```
**Claude Code 插件**
```
/plugin marketplace add Dodaios/ste80-humanizer
/plugin install ste80-humanizer@ste80-humanizer
```
**Claude.ai / Desktop**：下载仓库 ZIP，在 Settings → Capabilities → Skills 上传。

## 最小可用示例
在 agent 中调用：
```
/ste80-humanizer
This sounds like ChatGPT wrote it. Make it sound like a person.
```
或直接说：
```
Rewrite this README 80% of the way to ASD-STE100.
```
如需严格模式：
```
Convert docs/runbook.md to strict STE.
```

## 依赖前提
- 一个支持 skills 的编码 agent（Claude Code、Codex、Cursor、OpenCode 等）。
- 通过 npx 安装需要 Node.js 环境（README 未指定版本）。
- 无需单独安装 Python；技能在 agent 的 LLM 上运行。