## 安装

- 必须：ffmpeg + ffprobe（winget install Gyan.FFmpeg 或对应包管理器）
- 可选：yt-dlp（pip install --user -U yt-dlp）用于链接下载；ASR 服务用于转写
- 安装插件：dsh plugin --profile web add dsh-video-storyboard，重启 DSH
- 桌面版需源码安装：git clone 后 node scripts/install-dev.mjs
- 自检：node bin/doctor.mjs 检查依赖

## 最小可用示例

```js
// 贴链接
video_storyboard({ input: "https://example.com/some-video" })
// 本地文件
node bin/storyboard.mjs film.mp4 --out film.png
// 干跑评估
video_storyboard({ input, dryRun: true })
```

## 依赖前提

ffmpeg/ffprobe 必需；yt-dlp 仅在处理 URL 时必需；ASR 服务可选，未配置则无台词。