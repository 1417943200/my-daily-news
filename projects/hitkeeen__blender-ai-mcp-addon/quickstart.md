## 安装

1. 从 GitHub Releases 下载 `blender-ai-mcp-addon-v1.0.0.zip`。
2. Blender 4.2+ 中：Edit → Preferences → Get Extensions → 菜单 → Install from Disk。
3. 选择 ZIP，启用 addon。
4. 打开 3D Viewport → N → MCP Pro，按需点击 Open Studio Window。

## 最小可用示例

- 在 MCP Pro/Studio 中添加连接：选择 provider（如 OpenAI、Claude、Gemini、OpenRouter、OpenCode Zen、Ollama 或自定义端点），填入 key/配置。
- 选择支持 tool-calling 的模型；如需截图理解，选择 vision 模型。
- 发送：“Inspect this scene and explain its object structure before making any changes.”
- 或发送创建任务：“Create a simple product-display scene with a pedestal, a camera and three lights. Give the pedestal a matte blue material.”
- 在 Studio 任务板/审批中跟踪操作。

## 依赖前提

- Windows x64。
- Blender 4.2+。
- 至少一个受支持模型的连接，本地 Ollama/OpenCode 或云端 key。
- 使用 Poly Haven/Sketchfab/Poly Pizza 资产时按需配置服务 key，并遵守各资产许可。
- 外部 MCP 客户端接入需要阅读 docs/CONNECTIONS.md 获取认证端点与协议细节。