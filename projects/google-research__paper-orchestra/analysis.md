## 它是什么
PaperOrchestra 是 Google Cloud AI Research 推出的多智能体框架，目标是把未整理的写作前材料（想法、实验日志）转成投稿级 LaTeX 手稿。它编排多个专用智能体完成大纲、文献综述、分节写作、内容润色和图表生成。注意：README 声明它不是 Google 官方支持产品。

## 为什么火
仓库 Star 2818，创建于 2026-05-01，最近推送 2026-11-15，约半年时间获得关注。主要吸引力在于：瞄准科研写作的高成本环节，提供从原始材料到 LaTeX 的自动化流水线，并且来自 Google Cloud AI Research 团队。但 README 没有给出生成质量或评估数据，是否真能投稿仍需人工验证。

## 技术栈
- Python 3.11 + Conda 环境
- 支持 Gemini（Vertex AI 或 API Key）和 OpenAI 模型
- Semantic Scholar API 用于文献检索
- LaTeX 模板（如 cvpr2025）
- Streamlit 交互式 demo
- 可选 SMTP 邮件通知
- 具体依赖未在 README 展示，需查看 requirements.txt

## 核心能力
- 多智能体流水线：Outline、Literature Review、Section Writing、Content Refinement、Plotting 五类智能体协作
- 文献综合：自动搜索、排序并整合文献
- 图表生成：可生成 plot 和支持概念图
- LaTeX 自动化：生成符合会议模板的投稿级手稿
- 自定义模板：可在 templates/ 下添加新的会议模板

## 适用场景
适合已有实验日志和初步想法、希望快速得到论文初稿的研究者；适合需要统一会议 LaTeX 模板的投稿准备；适合想减少文献综述和配图工作量的场景。不适合没有原始材料、或需要严格事实核查与创新性论证的正式投稿——生成结果必须人工审校。

## 同类对比
README 未与同类工具做直接对比，也未提供 benchmark。从功能定位看，它接近自动论文写作/科研助手类工具，但多智能体编排和 LaTeX 模板自动化是主要差异点。由于缺少对比数据，无法判断是否优于其他方案。

## 版本动态
创建于 2026-05-01，最近推送 2026-11-15，近半年有活跃迹象。但 README 未提供 release/changelog。关键限制：数据集尚未发布，将稍后单独发布；这会影响复现和评估。
---

## ℹ️ 置信度与信息盲区

- 置信度：**medium**
- 信息盲区：数据集未发布，无法复现或评估生成质量；README 未提供 benchmark、生成质量或人工评估结果；未列出 requirements.txt 的具体依赖；未说明是否依赖本地 LaTeX 编译环境；未提供与同类工具的直接对比