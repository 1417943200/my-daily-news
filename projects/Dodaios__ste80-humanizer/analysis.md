## 它是什么
一个可安装到编码 agent（Claude Code、Codex、Cursor 等）的技能，用两遍重写让 AI 生成的文本更像人写的：第一遍移除 26 种 AI 常见套路（tells），第二遍按 ASD-STE100 简化技术英语的 80% 规则重建句子结构。目标不是通过 AI 检测，而是提高可读性。

## 为什么火
直接原因是 Karpathy 在 2026 年 10 月分享的 STE80 方法，该方法建议用 80% 的 ASD-STE100 让 LLM 输出更易读。这个仓库把方法做成了可复用的 agent 技能，且结合了已有的 AI-tell 移除库，短期获得 846 星。痛点真实：LLM 文本虽通顺但读着累，需要系统化改造而非零散替换。

## 技术栈
本质是声明式技能包：SKILL.md 定义规则，references 存放详细条目，通过 Vercel 的 skills CLI 或插件机制安装到 agent。仓库标注 Python，但用户侧不直接依赖 Python，主要运行在支持 skills 的编码 agent 上（Claude Code、Codex、Cursor 等）。有 CI 验证（validate workflow）。

## 核心能力
- **Pass 1**：清除 26 种 AI tells，按 A-F 六类组织（如 "Not X but Y"、口号式结尾、堆砌修饰、装饰性加粗等），保留事实。
- **Pass 2**：应用 15 条 STE80 结构规则，控制句子长度、每句一个想法、主动语态、简单时态、一个段落一个主题等；支持 80% 和 Strict（100%）两种强度。
- **三种模式**：Humanize（默认，Pass1 + Pass2 80%）、Light（仅 Pass1 + 最严重句子）、Strict STE（Pass1 + Pass2 100%）。
- **保真优先**：不改变事实、不添加内容、保留 "may"/"40+" 等原表达，标记源矛盾。
- **声音匹配**：可提供个人写作样本，让输出匹配你的句长、用词和标点。
- **透明报告**：编辑按编号报告（如 "§1, §8, S2"），便于对照规则核查。

## 适用场景
- 改写 AI 生成的文档、README、邮件、技术说明，让阅读更顺畅。
- 需要遵循受控语言（如航空、安全相关）的初稿起草，可切换 Strict 模式。
- 不适合试图绕过 AI 检测器的场景（项目明确否定该目标）。

## 同类对比
相比纯移除 AI 短语的工具（如 blader/humanizer），它多了结构级重写；相比直接给 LLM 下 prompt，它把规则固化成了可复用、可审计的技能，且报告编辑编号，方便回溯。README 提到在测试中与普通 prompt 的差异在保真度上最明显，但未给出定量基准。

## 版本动态
项目创建于 2026-11-09，最近推送 2026-11-18，非常新；当前 846 星，MIT 许可。由 Dodaios 团队（开源助手项目）维护，有 Trendshift 趋势徽章，说明近期热度上升。
---

## ℹ️ 置信度与信息盲区

- 置信度：**medium**
- 信息盲区：Pass 2 的 15 条 STE80 规则（S1-S15）细节在 README 截断部分未展示，需查看 SKILL.md 或 references/ste80-rules.md；未提供与其他 humanizer 或普通 prompt 的量化对比数据（README 仅提及 Tests，未展示结果）；未说明 Python 在此项目中的具体用途（仓库标注 Python，但技能主要靠声明式指令）；未说明安装 skills CLI 所需的 Node.js 具体版本要求