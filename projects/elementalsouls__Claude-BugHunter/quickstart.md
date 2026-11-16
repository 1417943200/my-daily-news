## 安装

**方式 A：Claude Code 插件（推荐）**
```text
/plugin marketplace add elementalsouls/Claude-BugHunter
/plugin install claude-bughunter@elementalsouls
```

**方式 B：复制安装（克隆）**
```bash
git clone https://github.com/elementalsouls/Claude-BugHunter.git
cd Claude-BugHunter
bash scripts/install.sh   # macOS/Linux
pwsh ./scripts/install.ps1  # Windows
```

**可选：安装 cbh CLI（独立终端 runner）**
```bash
pipx install git+https://github.com/elementalsouls/Claude-BugHunter
```

## 最小可用示例

在 Claude Code 中直接用自然语言描述测试目标，相关技能自动加载：
```text
> Testing acme.com — an in-scope HackerOne target. Run recon and rank the surface.

  ⟳ loading skills: web2-recon, offensive-osint, bb-methodology …
    → subdomain enum (subfinder + crt.sh) … 47 hosts
    → live hosts (httpx) … 12 · tech fingerprint … 6 distinct stacks
    → ranked surface: api.acme.com (GraphQL, introspection ON)  ← start here
                      auth.acme.com (OAuth, SSO)               ← hunt-oauth
```

也可以使用 `/hunt` 脚手架生成 engagement 文件夹，或用 `cbh` CLI 进行侦察和报告。

## 依赖前提

- Claude Code 已安装（或兼容 harness：OpenCode、Codex CLI、Hermes、AntiGravity）
- 对于 `cbh` CLI：Python 3.x + pipx
- 如需 Burp MCP 集成：需要 Burp Suite 及 MCP 服务器
- 授权目标：仅限拥有或有书面授权的资产