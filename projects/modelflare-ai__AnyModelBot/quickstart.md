## 安装
- 桌面：从 GitHub Releases 下载对应平台安装包：Windows x64/arm64、macOS Apple/Intel、Linux AppImage。macOS 已 Developer ID 签名并公证；Windows 首次运行若提示风险，点“更多信息 → 仍要运行”；Linux 需 `chmod +x` 后运行。
- Docker：`docker run -d --name amb -p 3600:3600 -v amb-data:/data ghcr.io/modelflare-ai/anymodel-bot`，然后 `docker exec amb cat /data/ui-token`，浏览器打开 `http://<主机>:3600/?token=<令牌>`。不要把 3600 暴露公网。
- 源码：需要 Node.js 22.13+ 和 Go 1.26.8+。`git clone` 后执行 `npm install`、`npm run setup`、`npm start`，访问 http://127.0.0.1:3600/。

## 最小可用示例
1. 首次打开应用，选择“登录 Modelflare”在浏览器授权，或配置自己的官方 API Key。
2. 在模型选择器里选一个模型（新账号建议选支持工具、花费低的默认模型）。
3. 对机器人说：“整理这个文件夹”或“帮我看下这个目录里有什么”，机器人会列出文件并在需要写工作区外时弹出审批卡。
4. 测试后台任务：说“每天早上8点看看X的价格，低于200告诉我”——会建成规则，到点执行并只在有结果时通知。

## 依赖前提
- 桌面版基本无需额外依赖；电脑操作在 macOS 首次使用时需授予“辅助功能”和“屏幕录制”权限。
- 现成 Bot「影视创作室」需要本机 Python 3.10+ 和 FFmpeg（含 ffprobe）。
- 直连官方模型需自备对应厂商 API Key；生图/生视频目前仅能通过 Modelflare 使用。