## 它是什么
PaperOrchestra 是 Google Cloud AI Research 推出的多 Agent 论文写作框架，Apache-2.0。输入是未组织的想法和实验日志，输出是符合会议模板的 LaTeX 手稿，包含文献综述和生成图表。

## 为什么火
仓库 Star 4.1k（截至 2026-11），发布时间较短有热度。解决研究者从原始材料到论文初稿链路长、模板适配繁琐的痛点，提供 CLI 和 Streamlit demo。注意：官方声明不是 Google 正式支持产品。

## 技术栈
Python 3.11 + Conda。LLM 支持 Gemini（Vertex AI 或 API Key）和 OpenAI；文献检索接 Semantic Scholar；生成 LaTeX 需准备会议模板；可视化可选 plotting agent。项目结构：methods 核心逻辑、templates 模板、utils API/PDF 工具、autoraters 自动评估。

## 核心能力
- 多代理流水线：Outline / Literature Review / Section Writing / Content Refinement / Plotting 五个专职代理。
- 文献合成：自动检索、按优先级整合引用。
- 图表生成：从代码生成 plot，支持概念图。
- LaTeX 自动化：适配目标会议模板输出投稿级手稿。
- 命令行参数可指定 writer 和 reflection 模型。

## 适用场景
需要把原始研究材料快速转成论文初稿的个人研究者或小团队；有会议模板和实验日志、希望自动生成文献综述和基础图表的场景。也适合研究多智能体写作流程的人。

## 同类对比
与 AutoGen/ MetaGPT 等通用多智能体框架相比，PaperOrchestra 更垂直，专注论文写作 pipeline；与 ChatPaper 类文献总结工具相比，它覆盖从大纲到 LaTeX 输出。但目前缺少公开 benchmark 或端到端效果数据，且数据集尚未发布，实际生成质量需自行评估。

## 版本动态
创建于 2026-05-01，最近推送 2026-11-15，仍活跃。README 提到数据集将另行发布，尚未包含在仓库。arXiv:2604.05018。未提供 Roadmap 或 release 版本号。
---

## ℹ️ 置信度与信息盲区

- 置信度：**medium**
- 信息盲区：未提供基准/评估数据（autoraters 仅有目录，未说明具体指标）；数据集未开源，需等待后续发布；未说明各 LLM 模型具体版本或 token 成本；未提供详细架构图或论文正文链接（仅 arXiv 编号）