## 安装
- **macOS**：下载 `kwant_universal.dmg`，拖入 Applications，首次打开需在“系统设置 → 隐私与安全性”允许。
- **Linux**：下载 `.deb` 或 `.AppImage`（需 glibc 2.35+，如 Ubuntu 22.04+）。
- **Windows**：下载 beta 安装程序（64 位）。
- **服务器**：`curl -fsSL https://kwant.si/install.sh | sh` 或 `docker compose up -d`（使用 `ghcr.io/alexsergivan/kwnt` 镜像）。

## 依赖前提
- 需要可用的 AI 后端：Claude/Codex/Grok CLI 或自有 API key。
- 服务器部署需 glibc 2.35+（Ubuntu 22.04+ / Debian 12+）。
- 桌面应用：macOS 11+，Linux GTK 桌面，Windows 64 位。

## 最小可用
1. 安装并启动 kwant。服务器模式会打印一次性登录链接；桌面版直接打开应用。
2. 首次使用会得到默认的 `@helpers` 团队（Assistant, Researcher, Writer），在 `#general` 频道发送需求即可。
3. 在 Settings → Apps & accounts 连接 AI 账户或配置现有 CLI/API key。
4. 发送任务后，bot 自动处理并在 Mission board 显示；需要人工审批时去 Inbox 查看。

（更详细步骤见官方文档：https://kwant.si/docs/quickstart）