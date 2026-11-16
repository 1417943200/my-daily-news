## 安装

- **Mac**：`brew install --cask diygod/tap/pinky` 或下载对应架构 `.dmg`。
- **Windows**：下载 `pinky-setup-<version>-amd64.exe` 运行；安装器未签名，SmartScreen 需选择更多信息→仍要运行。绿色版可解压 zip 运行 `Pinky.exe`。
- **Linux**：Debian/Ubuntu 用 `sudo apt install ./pinky_<version>_amd64.deb`；其他系统解压 tar.gz 运行 `./pinky`。

## 连接手机

**Android**
1. 手机开启开发者选项（关于手机连续点 Build number 7 次），再开 USB 调试。
2. USB 连接电脑，手机上允许调试。Android 11+ 可在 Add phone 里无线配对；Android 10 插线后可切 Wi-Fi。
3. Pinky 会提示安装手机端 App（Pinky on the phone），装后大幅提升读屏和输入速度。
4. 品牌特定步骤（小米/OPPO/vivo/HONOR/HUAWEI/Samsung/Pixel）在 Add phone 里有具体说明；每台手机可通过 ··· 菜单 Checkup 检查。

**iPhone/iPad**
- iOS 17.4+，先 USB 连接设置；Pinky 会用 Xcode 的 developer disk image（或询问从第三方镜像下载）准备设备。
- iOS 17.4–26 还需要从 Mac 用 Xcode 安装一次 Pinky 的 iPhone App；iOS 27 及以上无需额外安装（也可选择用 App）。设置后可用 Wi-Fi。

## 接入 Agent

- Claude Desktop：安装 Pinky 后打开 `.mcpb` 文件添加扩展。
- Claude Code/Codex/Cursor：在 Pinky 的 Settings › Agents 一键连接。
- 任何支持 MCP 的 agent 可通过 stdio 或 HTTP 接入。

## 最小可用示例

1. 安装并连接一台 Android 手机（或 iOS 模拟器/Android 模拟器）。
2. 在 Pinky 中连接 Claude Code 或 Claude Desktop。
3. 让 agent 在手机上执行简单任务，例如发一条消息。Pinky 会弹出审批框，点击 Allow 后 agent 才会发送（若设置了发送审批）。
4. 观察 Pinky 窗口的实时镜像，必要时可点击接管或按 Ctrl+Alt+. 停止。

## 前提

- Android 10–17 + USB 线（Windows 某些手机需 USB 驱动；Linux 需配置 USB 访问）；iOS 17.4+。
- macOS 13+/Windows 10/11 x64/Linux x86-64 (glibc 2.29+，GTK 3)。
- 如使用手机独立运行，需要可选的模型 API 或本地模型服务（Ollama/LM Studio）。
- pre-alpha，部分特性仍待更多人验证，参考 docs/ACCEPTANCE.md。