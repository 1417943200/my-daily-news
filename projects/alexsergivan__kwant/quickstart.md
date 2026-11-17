### 安装

- **macOS**：下载 `kwant_universal.dmg`，拖入 Applications。首次打开因未公证需在 系统设置 → 隐私与安全性 → Open Anyway 允许。
- **Linux 桌面**：`kwant_amd64.deb`（Ubuntu 22.04+ / Debian 12，`sudo apt install ./kwant_amd64.deb`）或 `kwant_x86_64.AppImage`（其他 GTK 发行版，`chmod +x` 后运行）。
- **自托管服务器**：一键脚本 `curl -fsSL https://kwant.si/install.sh | sh`（需 glibc 2.35+，无 sudo，作为用户服务运行并打印一次性登录链接）；或 `docker compose up -d`（镜像 `ghcr.io/alexsergivan/kwnt:0.9.21`）。
- **Windows (beta)**：`kwant_0.9.21_windows_x64_beta_setup.exe` 用户级安装。

### 最小可用示例

1. 启动 kwant（桌面应用或服务器脚本输出的一次性链接）。
2. 在 Web UI 中连接你的 AI 账户（Claude/Codex/Grok CLI）或填入自己的 API keys。
3. 创建 space（如工作/生活隔离），添加 bot；新安装预置 @helpers（Assistant、Researcher、Writer）。
4. 在 #general 输入任务或用 @提及 指定 bot；任务以卡片流转，关键产出需通过验证或审批。

> 依赖前提：macOS 11+ 或 Linux glibc 2.35+；需要能访问所选 AI 服务。完整配置步骤以官方 quickstart 为准：https://kwant.si/docs/quickstart （README 截断未包含全部细节）。