## 它是什么
Pinky 是一个开源桌面网关（Go 编写），让 MCP 代理（Claude Code、Claude Desktop、Codex、Cursor 等）操作真实 iPhone 或 Android 手机。核心是“人在环中”：高风险操作（付款、转账、发送、删除、安装、修改设置等）默认需要用户点击批准，规则由 Pinky 网关强制执行，而非依赖模型自觉。

## 为什么火
Star 增长快，可能因为解决了一个真实痛点：用 MCP 代理控制真实手机，同时提供安全审批和操作留痕。支持 iOS 与 Android 双平台，且无需在 iOS 27+ 安装额外软件；对安卓 13+ 还支持隐藏第二屏，不打断用户使用。对极客、自动化测试、受控设备管理都有吸引力。

## 技术栈
- Go 编写，UI 使用 MyGo（GPU 绘制，无 Electron/webview），下载 16–22 MB，空闲约 70 MB 内存。
- 通过 MCP over stdio 或 HTTP 接入任意支持 MCP 的代理。
- Android 自带 adb（从 Android 源码构建），iOS 通过 Apple 开发者镜像和 Pinky Helper/Pinky 应用驱动。
- 跨 macOS（Intel/Apple Silicon）、Windows x64、Linux x86-64 (GTK 3)。

## 核心能力
- 真实手机操作：Android 10–17、iOS 17.4+；iOS 27+ 无需额外安装，17.4–26 需从 Xcode 侧载 Pinky 应用。
- 安全批准：付款/交易/转账/发送/删除/呼叫/安装/链接外跳/设置变更等可配置等待；识别 10 种语言按钮；代理不能自我批准。
- 默认禁区：银行、钱包、密码管理器应用对代理不可见，代理不能输入密码/一次性验证码字段；可按任务临时授权。
- 手机端自主模式：Pinky 应用可在 Android/iPhone 上直接使用 DeepSeek、Qwen、Kimi、GLM、Claude、GPT、Gemini 或本地 Ollama/LM Studio 模型，无需电脑。
- 记录与回放：每步自然语言描述、截图、屏幕录像、HTML 报告导出，数据存于本机。
- 隐藏第二屏（Android 13+）与随时接管；解锁手机可经 Touch ID/Windows Hello/keyring，PIN 不暴露给代理。
- 定时任务与记忆：按条件运行任务，任务后可建议备忘经用户同意才保存。

## 适用场景
- 用 AI 代理自动化真实手机操作：发消息、下单、调试 UI、回归测试。
- 受控设备/他人手机的安全自动化，审批与可审计记录。
- 在手机上直接跑模型执行任务（安卓/iPhone），尤其是无电脑环境。
- 多平台手机兼容性测试（Android 模拟器、iOS Simulator、真实设备）。

## 同类对比
相对于纯提示词“代理控制手机”的方案，Pinky 的差异是网关强制审批与默认禁区，而不是依赖模型指令遵循；相对 Electron 类桌面工具，原生 MyGo UI 更轻量；相对云端手机自动化服务，它是本地优先、开源、无账户。但仍处于 pre-alpha，部分能力等待更多测试。

## 版本动态
最近 Release v2026.1117.4（2026-11-17）修复 macOS 隐藏启动时审批窗口抢键盘、浮动面板应用列表显示、窄窗口任务按钮换行。项目创建于 2026-11-06，Star 2371，更新频繁。README 自述已用真实 Android 手机（USB）和 iPhone（iOS 27、iOS 18.7.11 via Pinky Helper）端到端跑通 Claude Code，手机端模型任务在 Mi 10 Pro（Android 17）和 iPhone 13 mini（iOS 27.0.1）完成；部分功能仍待用户实测。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：README 未提供延迟、吞吐量或资源占用的基准数据（仅提到内存约 70 MB/0% CPU）；Telemetry 的具体采集范围和关闭方式需要查看 docs/TELEMETRY.md，README 未展开；HTTP MCP 接入的认证/加密细节未在 README 中说明；iOS 17.4–26 侧载依赖 Xcode 和 Apple 开发者签名，README 未说明是否需要付费开发者账号；项目当前为 pre-alpha，部分功能（解锁、后台工作、Wi-Fi 配对、文件等）尚待用户实测，稳定性和兼容性数据有限