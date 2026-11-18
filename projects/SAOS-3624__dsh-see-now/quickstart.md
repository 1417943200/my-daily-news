## 安装
需要Node.js环境和DSH（或独立Node使用）。安装：
```bash
dsh plugin --profile web add dsh-see-now
```
桌面版换 `--profile desktop`。装完重启DSH。卸载/升级类似。

## 最小可用
在DSH会话中让模型调用：
```js
see_now({ action: "watch" })
```
第一次约1秒返回当前屏幕；之后每次返回这段时间变化。可用 `/seenow` 斜杠命令开窗/关窗。

## 依赖前提
- ffmpeg自动查找或通过 `DSH_FFMPEG_PATH` 指定
- 平台屏幕采集：Windows自动；macOS需屏幕录制权限；Linux需 xdg-desktop-portal + PipeWire + python3-gi + GStreamer等
- 悬浮窗需Python ≥3.8带tkinter（macOS需brew install python-tk；Linux需python3-tk等）
- 可选声音：pyaudiowpatch+numpy用于听声音，TTS适配器配置 `~/.dsh/voice.json`
- 独立Node库用法：`import { spawnFrames } from 'dsh-see-now/capture'` 和 `createPipeline` 等。