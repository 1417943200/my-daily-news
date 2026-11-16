## 它是什么

Chrome DevTools MCP 是 Chrome DevTools 官方为编码代理准备的 MCP 服务器和 CLI。代理（Antigravity、Claude、Cursor、Copilot 等）可控制并检查实时 Chrome 浏览器，用于自动化、调试和性能分析。项目 TypeScript 编写，Apache-2.0 协议，Star 57k+，创建于 2025-09，迭代非常活跃。

## 为什么火

- 官方 Chrome DevTools 团队出品，直接调用 DevTools 能力录制 trace 并给出可执行性能洞察。
- 解决 AI 代理与真实浏览器之间的最后一段：可靠自动化、源映射堆栈、网络/控制台检查。
- 内置 skills 教代理调试无障碍、Cookie、LCP、内存泄漏，更贴近 agent 工作流。
- MCP 标准化，支持主流客户端；发布仅一年 Star 已超 57k。

## 技术栈

Node.js LTS + TypeScript。自动化层基于 Puppeteer；性能/调试层复用 Chrome DevTools 前端与协议。同时提供 MCP server 与独立 CLI，支持 headless、isolated、slim 及 WebSocket 连接等配置。

## 核心能力

- 性能：录制 trace、提取可行动性能洞察；可选接入 Chrome UX Report 真实用户数据。
- 调试：分析网络请求、截图、读取浏览器控制台消息（带 source map）。
- 自动化：Puppeteer 驱动 Chrome，自动等待操作结果。
- 最新 1.13.0 新增 logpoints（基于 DevTools BreakpointManager）、页面级网络 mock、支持上游 mock 响应。
- 可配置瘦身模式 --slim、禁用遥测/更新检查、自定义 executablePath、持久化用户目录、Android 调试。
- 安全/隐私：默认收集使用统计（可关闭）；性能工具可能向 Google CrUX API 发送 trace URL（--no-performance-crux 禁用）。

## 适用场景

- 基于 MCP 的 coding agent 做页面自动化、表单填写、导航验证。
- 前端性能排查，如 LCP、trace 和真实用户数据对比。
- 调试前端运行时错误、网络异常、cookie/session 问题。
- 作为浏览器子代理嵌入其他 agent 产品（可参考 Gemini CLI browser agent）。

## 同类对比

- vs Playwright MCP：Playwright 擅长跨浏览器自动化，但本项目更专注 Chrome + DevTools 深度调试与性能分析，且为官方 Chrome 团队维护。
- vs 直接使用 Puppeteer/Playwright 库：本项目原生适配 MCP 协议、自带 skills 和 CLI，降低代理接入成本。
- 局限：官方仅支持 Google Chrome 和 Chrome for Testing；其他 Chromium 不保证；默认会向 Google 上报使用数据（可退出）。

## 版本动态

最新 Release v1.13.0（2026-11-11）延续快速迭代。新增日志点、页面级网络 mock、上游网络 mock 支持；修复 UTF-8 BOM 配置读取、循环 Error.cause 链截断、--no-javascript-evaluation 下 logpoints 禁用、list_extensions 文案改进等。项目在 2026-11 仍持续推送，说明维护活跃。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：未提供完整工具清单，需查阅 docs/tool-reference.md 和 slim-tool-reference.md；无 benchmark 数据或稳定性/性能对比实验；Android 调试、持久化用户目录、并发会话等高级用法细节在 README 中仅提及，需读 docs/advanced-usage.md；使用统计具体字段未在 README 全部列出，仅说明包含成功率、延迟、环境信息