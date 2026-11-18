## 依赖前提
- Python 3.12+
- Node.js 22.19+
- Git
- Docker（若使用 Docker 部署）

## 安装与启动（源码）
```bash
git clone https://github.com/mdiri-ai/SoduWork
cd SoduWork
# macOS / Linux
sh start.sh --desktop
# Windows PowerShell
.\start.cmd --desktop
# Windows Command Prompt
start.cmd --desktop
```
首次运行会安装依赖，启动 Hub、管理控制台和桌面客户端，并提示设置 admin 密码（12–128 字符）。

## 最小可用示例
1. 在管理控制台添加模型 provider，然后在 Capabilities → Model catalog 中选择该服务，点击 Add model，输入 provider 的准确 model ID，选择 Chat model 保存。
2. 打开桌面客户端并登录到同一个 Hub（注意 Connection 地址指向同一 Hub）。
3. 选择 New conversation，选择 Pi 和刚添加的模型。
4. 发送第一个任务，例如：Turn these fictional meeting notes into an action table with owner and due date. Mark missing information as unconfirmed: Alex will organize the requirements by Friday; Sam will check the quotation.
5. 如需分配与验收，创建 requirement，描述目标、输入和验收标准，打开 Arrange execution 选择 Agent 和模型，检查交付后接受。

## Docker 部署
```bash
python3 ops/self-host/deploy.py up
python3 ops/self-host/deploy.py credentials   # 显示初始 admin 密码
```
将在单服务器启动 Hub、管理控制台和 PostgreSQL，前方建议放置 HTTPS 反向代理。