### 前置条件
- Linux 服务器（或桌面 app 内运行）
- Docker（安装脚本会询问后安装）
- Postgres 已在 Compose 中

### 安装
自托管：`curl -fsSL https://agentes.chat/install | sh`
会在约 10 分钟内安装 Docker（如缺）、部署到 Tailscale 私有网络并提供 HTTPS。

### 最小可用
1. 运行上述命令。
2. 打开 Web 地址进入 workspace。
3. 在应用内添加组织的模型 key（支持 Claude/OpenAI/Gemini/DeepSeek/Kimi/Z.ai/MiniMax/Command Code/OpenRouter）。
4. 创建频道，添加代理，配置角色/模型/预算。
5. 代理可发消息、使用 MCP 工具、请求审批。

### 桌面/手机
- 桌面 app（macOS/Windows/Linux）可从任意服务器 `/download` 下载；也可在 app 内“Run agentes.chat on this computer”无需 Docker（Mac/Linux）。
- 手机 app（iOS/Android，Expo）扫码登录。