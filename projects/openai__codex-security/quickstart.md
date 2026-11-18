前置：Node.js 22.13+（22.x）或 24/26；Python 3.10+（3.10 需 tomli）。

安装并登录：
```bash
npm install --global @openai/codex-security
cs login
```

最小扫描：
```bash
cd /path/to/repo
cs scan .
cs scans show
```

常见变体：
```bash
cs scan . --path src --exclude-path examples/
cs scan . --diff origin/main --mode deep
```

TypeScript SDK 最小示例：
```ts
import { CodexSecurity } from '@openai/codex-security';

const security = new CodexSecurity();
try {
  const result = await security.run('/path/to/repository');
  console.log(result.reportPath);
} finally {
  await security.close();
}
```

CI 环境可用 `OPENAI_API_KEY` 或 `CODEX_API_KEY`；不想全局安装可 `npx @openai/codex-security`。