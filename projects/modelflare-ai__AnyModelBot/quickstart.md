## 安装

- 从 Releases 下载对应平台安装包：Windows x64/arm64 exe；macOS Apple 芯片/Intel dmg；Linux x64/arm64 AppImage。
- Docker 部署：`docker run -d --name amb -p 3600:3600 -v amb-data:/data ghcr.io/modelflare-ai/anymodel-bot`
- 获取 UI token：`docker exec amb cat /data/ui-token`，打开 `http://<主机>:3600/?token=<令牌>`，不要将 3600 端口暴露公网。
- 源码运行：`git clone` 后 `npm install && npm run setup && npm start`，本地管理界面为 `http://127.0.0.1:3600/`。

## 最小可用示例

1. 首次启动应用，按引导登录 Modelflare 或配置官方 API Key。
2. 选择默认模型，创建第一个机器人，设置人设和工作区。
3. 在聊天中发任务，例如「整理这个文件夹」或「每天早上 8 点查看 X 价格，低于 200 告诉我」。
4. 涉及工作区外的文件操作会弹出审批卡片，点击批准后继续。
5. 在设置中接入微信/飞书等渠道，机器人后台执行并只推送结果。

## 依赖前提

桌面安装包基本免依赖；Docker 部署免本地 Node/Go。源码运行需要 Node.js 22.13+ 和 Go 1.26.8+。影视创作室 Bot 额外需要本机 Python 3.10+ 和 FFmpeg（含 ffprobe）。模型调用需要 Modelflare 账户余额或直连厂商的官方 API Key。