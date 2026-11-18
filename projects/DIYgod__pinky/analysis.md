## 它是什么

Pinky 是一个开源的手机自动化网关，让任意支持 MCP 的智能体（Claude Code、Claude Desktop、Codex、Cursor 等）操作真实的 iPhone 或 Android 手机，同时保持人在环：敏感操作必须经过人工批准，且批准权在 Pinky 网关而不是提示词层。它也可以脱离电脑，通过手机端 App 自主执行任务。

## 为什么火

- **填补 MCP 到真机操作的空白**：大多数 agent 只能跑在电脑上，Pinky 直接把手机变成可控设备。
- **安全设计不是事后补丁**：支付、交易、发送、删除、安装、外链、电话、设置变更等默认或可选触发审批；银行、钱包、密码管理器默认对 agent 不可见。
- **门槛极低**：单二进制/安装包，macOS/Windows/Linux 全平台，16–22 MB，空闲约 70 MB 内存。
- **真实可用**：README 展示 Claude Code 在 Android 16 模拟器上发消息的真实运行，支付默认询问，发送也可配置询问。

## 技术栈

- 主体语言：Go
- UI：MyGo（GPU 绘制，非 Electron/webview）
- 协议：MCP，支持 stdio 与 HTTP 连接
- Android：自带 adb（从 Android 源码构建），支持 Android 10–17
- iOS：通过 Apple 开发者镜像或 Pinky app（iOS 17.4–26 需从 Mac/Xcode 安装一次，iOS 27+ 无需额外安装）
- 桌面平台：macOS 13+（Apple silicon/Intel）、Windows 10/11 x64、Linux（glibc 2.29+，GTK 3）

## 核心能力

- **审批网关**：支付、交易、转账等默认停顿；可配置发送、订单、删除、电话、安装、外链、设置改变或每步都询问；agent 无法自我批准。
- **敏感区域默认隔离**：银行、钱包、密码管理器 app 不可见，密码/一次性验证码字段禁止输入；可按任务临时放行某个 app。
- **双屏/接管**：Android 13+ 支持隐藏第二屏，agent 在后台操作，用户可继续使用主屏；可随时接管暂停 agent，热键全局停止。
- **全记录**：每步含文字、截图、屏幕录制及步骤标记，可导出 HTML 报告，数据保留在本地。
- **手机端自主任务**：Pinky app 可直接使用 DeepSeek、Qwen、Kimi、GLM、Claude、GPT、Gemini、Ollama/LM Studio 等模型；支持打字/语音输入、Android 悬浮球询问屏幕、后台隐藏任务。
- **计划任务与记忆**：定时执行或条件提醒；任务后建议记忆内容，仅在你同意后保留。
- **解锁与配对安全**：PIN 可存一次，解锁需 Touch ID/Windows Hello/keyring 确认；Wi-Fi 配对用手机调试连接里的标记防止冒用。

## 适用场景

- 在 Mac/Win/Linux 上让 Claude Code 等 agent 操作实体手机完成真实任务：发消息、下订单、管理 app。
- 手机端个人自动化：定时任务、跨 app 操作、条件提醒，无电脑时也能跑。
- 测试/研究 iOS/Android 模拟器和真机上的 agent 行为。
- 注重隐私和审计的移动端自动化场景，每条操作有记录、可回溯。

## 同类对比

README 没有列出具体对标项目。从功能看，Pinky 比传统 Appium/UI 自动化更偏 agent 原生和人在环，比纯提示词约束更硬核：审批运行在网关上，不依赖模型听话。它同时覆盖 iOS 和 Android，并提供本机 agent 与手机端自托管两种模式。但目前还在 pre-alpha，生态和稳定性待观察。

## 版本动态

- 仓库创建：2026-11-06，最近推送：2026-11-18，最新 Release：v2026.1118.5（2026-11-18）。
- 最新版本改动较小：把“添加手机”里的 iPhone 卡片改名成“iPhone / iPad”，方便添加 iPad。
- 项目状态明确为 pre-alpha；README 称 Claude Code 已通过它端到端跑过 Android 真机、iOS 27 iPhone 和 iOS 18.7.11 iPhone XS Max，但部分功能（如计算机解锁、Android 后台、录制、导出、Wi-Fi 配对、手机文件）仍在等真人验证。
- docs/ 目录包含 DESIGN、WORKING、ACCEPTANCE、TELEMETRY、mcp 等文档，说明设计和验收有沉淀。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：README 在 Android tools 处截断，后半部分（FAQ、更多 iPhone/Wi-Fi/远控细节）未提供；无 benchmark 或屏幕识别准确率数据；手机端 App 的技术栈与具体交互细节未说明；部分功能仍处于 pre-alpha 且 README 自述等待真人验证；未列出具体同类项目对比