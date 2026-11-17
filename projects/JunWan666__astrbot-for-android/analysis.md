## 它是什么
AstrBot for Android 是一个 Android 应用，以单个 APK 内置 PRoot Ubuntu 运行环境，在手机上本地部署和管理 AstrBot 聊天机器人框架。用户通过 Kotlin + Jetpack Compose 原生界面完成环境初始化、服务启停、日志查看、备份恢复，并可内嵌 WebUI 配置模型/插件/人设。支持 QQ 官方机器人和微信官方 ClawBot 授权接入，无需 Root。

## 为什么火
需求明确：不少用户想在低功耗设备上常驻个人 AI 聊天机器人，但搭建和维护 Ubuntu + Python + AstrBot 门槛不低。该项目把整套环境打包进 APK，并提供官方机器人扫码授权和原生管理界面，将“手机当服务器”的门槛降到安装一个应用。405 star 反映了小众但刚需的自托管群体。

## 技术栈
- 客户端：Kotlin、Jetpack Compose
- 运行环境：PRoot（用户空间 chroot）运行 Ubuntu
- 机器人框架：AstrBot（通过官方 GitHub Release 更新）
- 集成：QQ 官方机器人 API、微信官方 ClawBot（openclaw-weixin / iLink）、WebView、终端、cpolar、SSH
- 打包：单个 APK 包含 Ubuntu、AstrBot、离线桌面资源；管理器与后端分离更新

## 核心能力
- 一键初始化和启停 AstrBot，显示真实就绪状态
- 首页配置 QQ/微信官方机器人，扫码授权、自动连接、启停/重绑
- 内置 WebUI，支持固定缩放和外部浏览器访问
- 通用 Ubuntu 任务管理：自定义目录/命令、运行时长、日志清理
- 备份与恢复：本机快照、ZIP 导入导出、更新失败回退
- 诊断与日志：自动跟随、脱敏导出、系统分享
- 扩展：SSH、cpolar 内网穿透、Linux QQ、DeepSeek Harness
- 权限引导：后台运行、Shizuku、无障碍、省电白名单

## 适用场景
- 无服务器、希望用旧 Android 手机 24h 运行 QQ/微信聊天机器人
- 个人或小社群使用官方机器人接口，规避第三方协议封号风险
- 需要移动管理 AstrBot 模型、插件、人设，并随时查看日志
- 想在 Android 上运行自定义 Ubuntu 程序（不只限于 AstrBot）

## 同类对比
- vs Termux 手动安装：本项目提供打包好的 Ubuntu 环境和原生管理 UI，免去大量配置；缺点是 APK 体积巨大（729 MiB），更新依赖项目方。
- vs 服务器部署 AstrBot：移动端便携、低成本，但受 Android 后台机制和厂商省电策略影响，稳定性不如 VPS。
- vs 非官方 QQ 机器人（NapCat 等）：官方机器人接口更合规，但功能限制较多（如无法用个人账号）。v1.5.0 已移除内置 NapCat/SnowLuma。

## 版本动态
v1.5.0（2026-11-17）移除 NapCat 和 SnowLuma，专注官方机器人接入，新增通用 Ubuntu 任务管理和环境修复，APK 从约 1GB 缩减到 729 MiB。升级保留用户数据和手动安装软件，旧版第三方接入停止自动启动。项目维护方向清晰：稳定官方渠道，降低法律与维护风险。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：未提供实际性能/资源占用基准（如内存、CPU 均值）；Android 后台运行在不同厂商 ROM 上的实际稳定性未量化；微信官方 ClawBot 的授权细节和限制未详细说明；移除 NapCat/SnowLuma 后，官方机器人接口是否满足原有个人号需求未对比；PRoot 在部分 Android 设备上的兼容性仅有例证，无系统测试矩阵