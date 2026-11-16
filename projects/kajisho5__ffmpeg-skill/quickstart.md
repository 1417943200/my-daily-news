## 安装

前提：`ffmpeg` 和 `python3` 已在 PATH 中。Ubuntu/Debian 示例：`sudo apt install ffmpeg`。安装技能：

```bash
npx ffmpeg-skill          # 安装到 Claude Code；--cursor / --codex / --all 可指定其他客户端
npx ffmpeg-skill doctor   # 检查 FFmpeg、ffprobe 和各工具所需组件
```

## 最小可用示例

1. 查看契约：

```bash
npx ffmpeg-skill contract --json | head -40
```

2. 对代理说一句话任务：

> “Take `interview.mp4`, keep 0:45–3:10 and 5:00–6:30, and make it exactly 60 seconds for Reels.”

代理会依次运行 `probe.py`、`cut.py --segments ...`、`fit.py --duration 60 --aspect 9:16 --fit crop`、`export.py --preset reels`、`check.py --platform reels`、`look.py`，然后报告 `final.mp4: 59.98 s, 1080×1920, 30 fps, AAC stereo`。

3. 平台交付模板：

```bash
python3 $S/render.py talk.mp4 --template tiktok --cues cues.txt
```

## MCP 使用

任意 MCP 客户端可连接；默认 `tools/list` 宣传核心 12 个（保持 context 小），全量 42 个需设置 `FFMPEG_SKILL_MCP_FULL=1`；按名称 `tools/call` 仍可到达全部工具。

## 可选语音识别

`caption.py --transcribe` / `silence.py --transcribe` 需要一个本地 ASR 引擎，例如 `pip install faster-whisper`；首次运行会下载模型，音频不离开本机。不装引擎不影响其他工具。