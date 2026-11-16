### 依赖

- Node.js >=22（npm 安装方式）
- 可选：Qwen 账号订阅（Plus/Pro）或任意支持的 API key

### 安装

Linux/macOS：
```bash
curl -fsSL https://qwen-code-assets.oss-cn-hangzhou.aliyuncs.com/installation/install-qwen-standalone.sh | bash
```

Windows：
```powershell
irm https://qwen-code-assets.oss-cn-hangzhou.aliyuncs.com/installation/install-qwen-standalone.ps1 | iex
```

或 npm：
```bash
npm install -g @qwen-code/qwen-code@latest
```

### 最小可用示例

```bash
cd /path/to/your-project
qwen
```

会话内运行 `/auth` 选择 Qwen 订阅或配置 API key，然后输入：
```text
Explain this repository and show me where to start.
```

无交互模式：
```bash
qwen -p 'Summarize this repo'
```