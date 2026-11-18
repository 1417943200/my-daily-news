## 安装
- 依赖：Git >= 2.41，Node.js/npm。
- 全局安装 CLI：
```bash
npm install -g @alibaba-group/open-code-review
```
- 也可通过 Agent Skills 安装：
```bash
npx skills add alibaba/open-code-review
```
二选一即可；Skills 模式会引导安装 `ocr`。

## 最小可用示例
原生模式：
```bash
cd /path/to/your-git-repo
ocr config provider   # 选择内置 provider 或添加自定义 OpenAI/Anthropic 兼容端点
ocr config model      # 选择模型
ocr review            # 评审当前 Git 变更
```
全文件审计：
```bash
ocr scan src/
```
Delegation 模式（无独立 API key）：
在 Claude Code / Cursor 等支持 Skills 的 agent 中加载 `open-code-review-delegate` 技能，按提示运行，使用宿主 agent 现有模型，不需要配置 `ocr` provider。

注意：具体命令参数和 CI 配置细节建议查看官网文档及 `examples/` 目录。