## 安装
- macOS：下载 `kwant_universal.dmg`，拖入 Applications。首次打开因未公证，需到「系统设置 → 隐私与安全性」点击“仍要打开”。
- Linux：`.deb` 适用于 Ubuntu 22.04+/Debian 12+，`sudo apt install ./kwant_amd64.deb`；或 `AppImage` 加执行权限运行。
- 服务器：`curl -fsSL https://kwant.si/install.sh | sh`（无 sudo，自动注册为服务并输出登录链接）；或克隆仓库后 `docker compose up -d`（镜像 `ghcr.io/alexsergivan/kwnt:0.9.25`）。
- Windows（beta）：运行 `kwant_0.9.25_windows_x64_beta_setup.exe`，仅安装给当前用户。

## 最小可用示例
启动后，一个全新安装会自动创建 `@helpers` 团队（Assistant、Researcher、Writer），`#general` 频道会问“What do you want done?”，直接回复任务即可看到 bot 分工执行。也可以新建 space、@mention 其他 bot 进行 handoff。

## 依赖前提
- macOS 11+（Intel 或 Apple silicon）；Linux x86_64 需要 glibc 2.35+，或 arm64 服务器；Windows 64 位（beta）。
- 需要自己提供 AI 账号或 API key：可连接 Claude/Codex/Grok CLI，或在设置中填入自己的 API key。
- 浏览器自动化等功能可能需要额外服务或配置，具体参考 `docs/bot-browser.md`、`docs/connections.md`。
- 本地数据存放在 `~/.kwnt`（Mac app 也使用同一文件夹）。