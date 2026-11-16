## 它是什么

mcp-for-blender-pro 是 Blender 4.2+ 的 AI 助手与 MCP 服务端插件。它把自然语言聊天、21 个场景工具、视口截图/审批、多代理任务板和本地 Streamable HTTP MCP 端点放进 Blender 的 Studio 窗口。

## 为什么火

对厌倦重复 bpy 脚本的技术美术和 AI 工具集成者，它把“能看场景、能改场景、能接外部 MCP 客户端、能跑多代理审批链”集中在一个安装包；尤其适合已经用 OpenCode/Claude/GPT 等，希望直接操作 Blender 而不自己写胶水代码的场景。

## 技术栈

- Blender 4.2+ 插件，基于 bpy Python API。
- Windows x64 便携 Python 3.13 runtime 随发布包提供。
- MCP 服务通过 authenticated Streamable HTTP 开放；Studio 本地运行并认证到 Blender。
- 模型协议：OpenAI Chat Completions、Anthropic Messages、Ollama 自定义端点；支持 OpenAI/Claude/Gemini/OpenRouter/OpenCode Zen/Ollama。
- 资产集成：Poly Haven、Sketchfab、Poly Pizza。
- 多语言 UI：英/德/法/西/中。

## 核心能力

- 场景检查：get_scene_info、list_objects、get_object_info。
- 创建对象：add_cube、add_sphere、add_cylinder、add_plane、add_light、add_camera。
- 编辑：move_object、duplicate_object、delete_object、parent_objects、set_material。
- 视觉/脚本：viewport_screenshot、execute_code。
- Blender API/导出：bpy_api_lookup、describe_node_type、export_scene。
- 资产工作流：search_assets、import_asset。
- 单助手或 Team chain：Manager/Workers/Reviewers 顺序执行；失败一次修正，二次失败停止。
- 审批、当前步骤后取消、命名 undo；Python 校验非安全沙箱。

## 适用场景

- Blender 技术美术/自动化：自然语言批量创建/修改/导出场景。
- 多代理结构化任务：需求拆解、执行、审查。
- 外部 AI 客户端接入：OpenCode 或其他支持 Streamable HTTP 的 MCP 客户端操作 Blender。
- 多模型切换：工作与个人连接分离，本地 Ollama/OpenCode 与云端模型混用。

## 同类对比

README 未给出直接竞品名。相较单一“Blender MCP 工具暴露 bpy 函数”的插件，它多了可视化 Studio、任务审批/undo、多代理链、多 provider 连接管理和资产 API。代价是首次使用需要学习 Studio 配置，且当前仅覆盖 Windows x64 + Blender 4.2+，跨平台能力不如部分纯 Python 方案。

## 版本动态

v1.0.0 为第一个公开版本，与仓库创建/推送同日；无历史版本或迁移说明。项目为 MIT，Star 2146，发布时间尚短，维护与社区反馈需要继续观察；README 未提供测试覆盖率、性能基准或兼容性矩阵。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：未提供 benchmark、性能或测试覆盖率数据；多代理 Team chain 的失败重试、审查返回格式等实现细节较概括；21 个场景工具的具体参数/JSON schema 未在 README 完整列出；MCP 服务器的认证机制和安全边界细节需查阅 docs/CONNECTIONS.md；仅声明 Windows x64 + Blender 4.2+，未说明 macOS/Linux 支持计划或兼容性