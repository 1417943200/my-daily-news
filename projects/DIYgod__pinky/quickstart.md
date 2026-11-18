## 安装

- macOS 13+：`brew install --cask diygod/tap/pinky`，或下载对应架构 `.dmg`（Apple silicon 选 arm64，Intel 选 amd64）。
- Windows 10/11 x64：运行 `pinky-setup-<版本>-amd64.exe`（未签名，SmartScreen 出现时选 More info → Run anyway）。
- Linux：Debian/Ubuntu 用 `sudo apt install ./pinky_<版本>_amd64.deb`；其他发行版解压 `.tar.gz` 后运行 `pinky`。

## 依赖前提

- Android：Android 10–17，USB 线；开启 USB 调试（设置 → 关于手机 → 连点 Build number → 开发者选项 → USB 调试）。Android 11+ 可无线配对。
- iPhone/iPad：iOS 17.4+，首次设置用 USB，之后可 Wi-Fi；iOS 17.4–26 需从 Mac/Xcode 安装一次 Pinky app。
- Linux：需 GTK 3，glibc ≥ 2.29；Windows 上部分手机需 USB 驱动。
- 任意支持 MCP 的 agent（Claude Code、Claude Desktop、Codex、Cursor 等）。

## 最小可用流程

1. 安装并打开 Pinky，选择 Add phone。
2. Android 插上 USB 并允许调试，Pinky 会提示安装手机端 app（Pinky），按提示完成。
3. 连接 agent：Claude Desktop 可打开 release 里的 `pinky-<版本>.mcpb` 添加扩展；Claude Code/Codex/Cursor 等在 Pinky 的 Settings › Agents 一键连接。
4. 对 agent 说：帮我在手机上给张三发一条“晚上聚餐吗”消息。
5. 观察 Pinky 窗口的镜像：默认发送操作会等待批准，点击 Allow 后消息发出；支付等操作默认也会等待。

> 若使用 iPhone，添加手机后 Pinky 会准备 Apple 开发者镜像；iOS 17.4–26 还需要从 Mac/Xcode 安装 Pinky app。