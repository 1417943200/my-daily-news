## 它是什么

dsh-video-storyboard 是一个针对 DeepSeek Harness 的视频理解插件，核心思路是把视频抽成一帧或多帧拼接的宫格图，并附带按时间对齐的文本清单（每格起止时间、台词、切刀数）。模型看图+读清单，就能回答“第3分钟发生了什么”“这句话对应哪一格”等问题。它包含六个工具：video_probe、video_storyboard、video_zoom、video_locate、video_subtitles、video_help。

## 为什么火

因为它直接解决多模态模型看视频的两个痛点：逐帧抽图 token 爆炸，只喂字幕丢失画面信息。它通过“一格=一个镜头、格子大小=切点密度”的自适应布局，把关键信息压缩到一张约 222 token 的图里，同时保留节奏。Star 561，说明社区认可。

## 技术栈

JavaScript，依赖 ffmpeg/ffprobe 做视频处理和抽帧，yt-dlp 处理链接下载，ASR 服务生成转写。算法涉及图像差异检测、卷积切点概率、DP 排布等。

## 核心能力

- 六个工具覆盖探测、分镜、放大、定位、硬字幕提取、帮助。
- 档位系统：8 档格子大小根据切点密度自适应，长镜头大格，快闪小格。
- 策略：auto（默认，按时长定预算并挑最省档）、full、standard、compact、skim、brief，可精确映射 tierMap。
- dryRun 扫描预先评估成本。
- 本地文件和链接（yt-dlp 支持）均可处理。
- 输出：一张图+文本清单，透明标注 token 消耗和 coverage/largest gap。

## 适用场景

适合需要在多模态 LLM 中低成本理解长视频的开发者、极客，尤其是需要定位视频片段、生成摘要、回答时间相关问题的场景。对 B 站/YouTube 等链接可通过 cookies 处理登录高清。

## 同类对比

与直接抽帧对比，单图成本固定约 222 token，比逐帧抽图节省数倍到数十倍；与只喂字幕对比，保留了画面构图、动作和节奏信息。与旧版固定宫格相比，0.6 后的密度布局避免长镜头浪费面积、快闪被压成色块。

## 版本动态

最新 v0.7.6（2026-11-16），修复了 video_locate 缓存未调用、跨平台路径测试、yt-dlp 全局配置干扰等问题，并新增清单头最大空档提示。0.6.0 有过大改，协议从 MIT 改为 Apache-2.0。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：未提供与其他视频理解工具（如 VideoIndex、VideoCaptioning 等）的直接横向 benchmark 数据。；ASR 服务的具体配置步骤未在 README 展开，需查阅 docs/FAQ.zh.md。；对 DeepSeek Harness 之外的其他 LLM Agent 框架的兼容性未明确说明。；未说明多语言 ASR 的支持范围和准确率。