## 前提

- Node.js LTS
- Chrome 稳定版或更新（或 Chrome for Testing）
- npm

## 方式一：MCP 客户端接入

在 MCP client 配置中加入：

```json
{
  "mcpServers": {
    "chrome-devtools": {
      "command": "npx",
      "args": ["-y", "chrome-devtools-mcp@latest"]
    }
  }
}
```

然后对代理说：

```
Check the performance of https://developers.chrome.com
```

应会打开浏览器并录制性能 trace。注意：仅连接 MCP server 不会自动启动浏览器，需调用工具时才启动。

## 方式二：CLI

```sh
npm i chrome-devtools-mcp@latest -g
chrome-devtools navigate_page 1 --url "https://developers.chrome.com"
chrome-devtools take_screenshot 1 --filePath screenshot.png
chrome-devtools stop
```

详见 docs/cli.md 和 docs/configuration.md。