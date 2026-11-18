## 依赖前提
- Docker（推荐）
- 或手动部署需Node.js环境（README未明确版本）

## 安装
使用安装脚本（需要Docker）：
```sh
curl -fsSL https://get.n8n.io | sh
```

或手动Docker部署：
```sh
docker volume create n8n_data
docker run -it --rm --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n
```

访问编辑器：http://localhost:5678

## 最小可用示例
1. 打开编辑器，创建新workflow。
2. 添加一个Trigger节点（如Webhook）作为入口。
3. 添加Action节点（如HTTP Request或AI Agent节点）。
4. 连接节点，配置参数，保存并执行。

详细教程和模板参考：https://n8n.io/workflows 和 https://docs.n8n.io