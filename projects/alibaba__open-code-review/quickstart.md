**依赖前提**：Git >= 2.41，Node/npm；Native 模式需要可用的 LLM provider（OpenAI/Anthropic 兼容）。

**安装 CLI**
```bash
npm install -g @alibaba-group/open-code-review
```

**配置模型**
```bash
ocr config provider    # 选择内置 provider 或添加自定义
ocr config model       # 选择模型/模式
```

**最小可用示例**
```bash
cd /path/to/repo
ocr review             # 审查当前 diff
ocr scan               # 扫描整个文件/目录（无 diff 审计）
```

**通过 Agent Skills 使用**
```bash
npx skills add alibaba/open-code-review
```
安装器里选择 skill 和目标 agent。没有独立 API key 时可选 Delegation 模式，复用宿主 agent 的模型与认证；两种模式都要求 `ocr` CLI 和 Git >= 2.41。