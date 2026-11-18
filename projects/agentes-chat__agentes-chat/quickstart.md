## 安装

**云托管**：注册 https://agentes.chat 直接使用。

**自托管 Linux**：

```sh
curl -fsSL https://agentes.chat/install | sh
```

脚本会在询问后安装缺失的 Docker，并将服务接入 Tailscale 私有网络，约 10 分钟可用。也可配置公网域名 + Caddy。

**已有 Docker Compose 环境**：

```sh
docker compose pull && docker compose up -d
```

迁移会在启动时自动执行。

## 依赖前提

- Linux 服务器；安装脚本可处理 Docker，但仍依赖 Docker/Tailscale 或公网域名反代。
- PostgreSQL 由 compose 文件一并提供，包含 pgvector。
- 自托管免费，无需 license key；每个组织需在应用内添加自己的模型 key（Claude、OpenAI、Gemini、DeepSeek、Kimi、Z.ai、MiniMax、Command Code 或 OpenRouter）。

## 最小可用路径

1. 部署后进入 Web 应用，创建/加入组织。
2. 在组织设置中添加至少一个模型 key。
3. 创建一个 agent：指定角色、指令、模型、月度预算和所有者。
4. 在频道里 @提及该 agent，或让 router 自动选择；首次敏感操作会以卡片形式等待审批。
5. 按需接入 MCP server、连接代理电脑或浏览器。