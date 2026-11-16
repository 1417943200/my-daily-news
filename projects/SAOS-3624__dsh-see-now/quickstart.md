## 安装

```bash
dsh plugin --profile web add dsh-see-now
```
桌面版换 `--profile desktop`。装完重启 DSH。卸载/升级：`remove` / `update`。

## 最小可用

重启后会话里让模型调：

```js
see_now({ action: "watch" })
see_now({ action: "watch", say: "..." })
```
也可以用斜杠命令：`/seenow`（开窗+起采集）、`/seenow off`、`/seenow status`。

## 当普通 Node 库

```js
import { spawnFrames } from 'dsh-see-now/capture';
import { createPipeline } from 'dsh-see-now/pipeline';

const p = createPipeline({ width: 800, height: 450, fps: 12, queueDepth: 0 });
const run = spawnFrames({
  source: { kind: 'screen' },
  width: 800, height: 450, fps: 12,
  onFrame: (f) => p.push(f),
});

setInterval(() => {
  const sheet = p.take();
  if (sheet) fs.writeFileSync(`sheet-${sheet.at}.png`, sheet.png);
}, 200);
```

## 依赖前提

- 平台：macOS 需在隐私设置给屏幕录制权限；Linux 需要 xdg-desktop-portal、PipeWire、gst 插件；Windows 自动探 ddagrab/gdigrab
- Python ≥ 3.8 且带 _tkinter 才能起悬浮窗；Linux 额外需要 python3-tk、Pillow、mss、numpy
- ffmpeg 只在 source:file/rtmp 时需要，插件会按 `DSH_FFMPEG_PATH` 等顺序找
- 转写：DSH 桌面版自带 speechToText；命令行宿主需配 `~/.dsh/asr.json`
- TTS：`~/.dsh/voice.json` 指定适配器模块，如 `examples/voice-say-mac.mjs`