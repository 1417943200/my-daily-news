## 它是什么

`ffmpeg-skill` 是一个面向 coding agent（Claude Code、Cursor、Codex、任意 MCP 客户端）的本地视频编辑器。仓库把 42 个 FFmpeg/ffprobe 工具封装成结构化脚本，并附带一份机器可读契约（`contract --json`）和 MCP server。核心卖点：不通过 shell 拼字符串、不接受外部 filter graph；每个操作由 typed arguments 驱动；执行后自动 probe/check/look 验证结果。发布为 npm 包，但底层是 Python 标准库 + FFmpeg，无云、无 API key、无 Python 第三方依赖（可选本地 ASR 除外）。仓库自身定位为生态中的 `hands`，只负责测量、剪切、导出和校验，不做创意决策。

## 为什么火

6587 star、创建于 2026-09、最近仍在推送。它击中一个真实痛点：让 LLM 代理直接写 FFmpeg 命令很容易产生“看起来对、实际错”的结果——猜错帧率、选了容器不支持的 codec、对只需 stream copy 的文件做了重编码、不检查输出就说 done。这个项目把 `probe → edit → check → verify` 固化为工作流，用契约约束每个工具，让代理能读、能验证、能复用。对需要离线处理敏感素材、不想上传云端的用户很友好。SPEC 机制（从 argparse 派生 input_schema，CI 防漂移）也让“工具定义与实现不一致”这个代理生态常见问题得到控制。

## 技术栈

- Python（标准库，无第三方依赖；可选 ASR：parakeet-mlx、faster-whisper、openai-whisper）
- FFmpeg / ffprobe（测试覆盖 FFmpeg 6.1、7.1、8、9）
- 通过 npm 分发和安装（`npx ffmpeg-skill`）
- MCP（Model Context Protocol）暴露工具；默认只列出核心 12 个以节省 context，`FFMPEG_SKILL_MCP_FULL=1` 可展开全部 42 个
- 文档/契约：`contract.md`、`design-decisions.md`、`roadmap.md`、`demos.md`

## 核心能力

42 个工具覆盖：剪切、拼接、静音移除、时长/画幅适配、字幕与卡拉OK动画、叠加与运动图形、HDR→SDR、LUT、音频清理与动态处理、带漂移校正的同步、多机位、响度标准化、交付检查、整片工程渲染、批量目录处理。每个工具同时是 CLI 脚本和 MCP 工具；`contract --json` 给出每个工具的输入 schema、输出、所需 FFmpeg 组件和验证方式。验证链包括探测结果、目标平台规格检查、以及画面变化后的 contact sheet 检查。示例中有大量 before/after，且由 `demos/build.py` 可复现。

## 适用场景

- 想让 Claude Code / Cursor / Codex 代理自动处理本地视频：裁剪、转比例、加字幕、做平台交付（Reels/TikTok 等）
- 批量处理或流水线化视频资产，不想手写 FFmpeg shell
- 需要离线处理敏感素材（访谈、样片等），不希望上传到云服务
- 作为更复杂视频生产 agent 的执行层（该生态中 `video-production-agent` 等会调用本仓库的工具）

## 同类对比

- 对比“直接让 agent 写 ffmpeg 命令”：本项目放弃灵活性换取可验证性和结构化，避免 shell 注入和不透明 filter graph。
- 对比同类 Agent 视频技能：`ffmpeg-skill` 更专注“执行与验证”，不替代上游决策（裁剪点、交付批准、字幕内容）；生态内通过 JSON 输出 / `doctor` 与其他技能单向依赖。
- 对比云视频处理 API：无需上传、无 API key、完全本地，适合隐私敏感或离线环境；但需要本机安装 FFmpeg 且计算资源受限。
- 对比 `remotion-ffmpeg-skill` 等：Remotion 用于运动图形合成，本仓库提供底层 probe/silence/scenes/overlay/render 等数据，属于不同层。

## 版本动态

最新 Release v3.10.1（2026-11-15）主要由 #539 修复构成：统一处理非音视频流（字幕、数据轨、timecode）在容器复制时的兼容性，避免因单个流失败拖累其他有效流；`metadata.py` 在 FFmpeg 运行前拒绝目标容器不支持的流复制；图片工具拒绝仅音频输出扩展名。这类修复显示项目在跨容器/跨 FFmpeg 版本的流级可靠性上持续投入。Star 6587，最近推送 2026-11-16，开发活跃。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：README 截断至 12000 字，未见完整 Install 表（Windows/macOS 细节）及 FAQ/Development 后半部分；未提供量化性能基准（转码速度、内存/CPU 占用）；MCP server 的传输、认证、生命周期细节未在截断内容中展开；与生态外同类工具（如云视频 API、其他 agent video skill）无直接对比数据