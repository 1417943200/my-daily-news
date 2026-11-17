## 安装
- macOS 13+ (Apple silicon/Intel)：下载 `pinky-<version>-arm64.dmg` 或 `pinky-<version>-amd64.dmg`，或 `brew install --cask diygod/tap/pinky`。
- Windows 10/11 x64：下载 `pinky-setup-<version>-amd64.exe` 运行；未签名需点击“更多信息 > 仍要运行”。绿色版解压 `pinky-<version>-windows-amd64.zip` 运行 `Pinky.exe`。
- Linux x86-64：Ubuntu 20.04/Debian 11 或更新系统，需 GTK 3；下载 `.deb` 后 `sudo apt install ./pinky_<version>_amd64.deb`，或解压 `pinky-<version>-linux-amd64.tar.gz` 运行 `pinky`。

## 连接手机
- Android 10–17：设置 > 关于手机 > 连点 Build number 7 次开启开发者选项，开启 USB 调试；插入 USB，允许调试。Android 11+ 可 Wi-Fi 无线调试；Android 10 插线后可用 `Use Wi-Fi instead…` 切到 Wi-Fi。Pinky 会建议安装 Pinky 手机端应用加速读屏、支持多语言输入。
- iPhone/iPad：iOS 17.4+；iOS 27+ 无需安装额外应用；iOS 17.4–26 需用 Mac + Xcode 侧载 Pinky 应用。Pinky 会使用 Apple 开发者镜像自行准备，可下载第三方镜像（需用户确认）。

## 接入代理
- 安装并连接手机后，打开 Pinky，Settings › Agents 一键连接 Claude Code、Claude Desktop、Codex、Cursor 等；任何能用 MCP 的代理可通过 stdio 或 HTTP 接入。
- Claude Desktop：可直接打开 `pinky-<version>.mcpb` 添加扩展。

## 最小可用示例
1. 安装 Pinky 并连接真实 Android/iPhone 或模拟器。
2. 在 Settings › Agents 添加 Claude Code 或 Claude Desktop。
3. 对代理说：“在手机上打开 Messages，给某人发送你好”，在 Pinky 窗口中观察；按需在审批弹窗点击 Allow/Deny。
4. 查看任务报告：每步描述、截图与录像可导出 HTML。

## 依赖前提
- 桌面端：macOS 13+ / Windows 10+ x64 / Linux x86-64 + GTK 3。
- 手机端：Android 10–17 或 iOS 17.4+；iPhone 可能需要 USB 线首次设置，之后可 Wi-Fi。
- 代理：任意 MCP 客户端（Claude Code/Desktop、Codex、Cursor 等）。
- 可选：Xcode（iOS Simulator 或 iOS 17.4–26 侧载）、Android Studio（Android 模拟器）。