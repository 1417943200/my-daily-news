### 安装
```bash
git clone https://github.com/Tencent/LoopForge.git
cd LoopForge
./start.sh
```
依赖：Git、Docker、Compose、Python 3、curl；macOS 需要 Docker Desktop。默认监听 `0.0.0.0:8090`。如果 ghcr.io 拉取慢，可设置：`MIRROR=ghcr.nju.edu.cn ./start.sh`。

### 无 API Key 最小示例
1. 启动后创建账号，第一个账号自动成为管理员。
2. 进入内置 LoopForge demo 项目，打开 Templates → Platform check · script & approval。
3. 点击 Run SOP：脚本会产出报告并停在审批节点，批准后继续到最终产物。

### 真实工作配置
在个人设置中配置模型 key，连接 GitHub 仓库，选择执行器和 SOP；需要改现有仓库并开 PR 时，绑定 GitHub 授权后即可通过聊天或 SOP 提交 PR/MR。