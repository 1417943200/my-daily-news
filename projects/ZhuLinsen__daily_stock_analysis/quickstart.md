## 安装
方式一（推荐）：GitHub Actions
1. Fork 本仓库。
2. 在仓库 Settings → Secrets and variables → Actions 中添加 Secrets：
   - 至少一个 AI 模型 Key（如 MODELFLARE_KEY、LLM_X6AI_API_KEY、GEMINI_API_KEY 等）。
   - 至少一个通知渠道（如 WECHAT_WEBHOOK_URL、FEISHU_WEBHOOK_URL、TELEGRAM_BOT_TOKEN+TELEGRAM_CHAT_ID 等）。
   - 必填 STOCK_LIST，例如 `600519,hk00700,AAPL,7203.T,005930.KS,2330.TW`。
   - 推荐配置新闻源（如 SERPAPI_API_KEYS）；行情源可选，默认免费源可跑通。
3. Actions 标签启用 workflows，手动运行“每日股票分析”测试。
4. 默认工作日 18:00（北京时间）自动执行。

方式二：本地运行
```bash
git clone https://github.com/ZhuLinsen/daily_stock_analysis.git && cd daily_stock_analysis
pip install -r requirements.txt
cp .env.example .env && vim .env
python main.py
```
常用命令：
```bash
python main.py --debug
python main.py --dry-run
python main.py --stocks 600519,hk00700,AAPL,2330.TW
python main.py --market-review
python main.py --schedule
python main.py --serve-only
```
Web 界面：`python main.py --webui` 后访问 http://127.0.0.1:8000。

依赖前提：Python 3.10+；至少一个 AI API Key 和至少一个通知渠道；STOCK_LIST 必填。免费行情源（AkShare/Baostock/YFinance）零配置可用，但受上游限流影响，长期定时建议配置 token 型数据源。Docker 部署和桌面客户端打包另见文档。