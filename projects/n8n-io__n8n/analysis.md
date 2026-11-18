## 它是什么
n8n是一个fair-code（公平代码）许可的工作流自动化平台，支持构建AI agents。它结合可视化画布和自定义代码（JavaScript/Python），可自托管或云部署，提供1500+集成和9000+模板。定位是“AI automation you can trust with real work, from prototype to production.”

## 为什么火
Star数21万+，说明极高关注。原因：AI-native自动化需求爆发，n8n允许开发者用自己的数据、模型和工具构建multi-step agents，无供应商锁定；自托管满足隐私和合规；低代码降低门槛同时保留代码能力。

## 技术栈
TypeScript编写，核心平台。前端编辑器、后端服务、集成节点。支持Docker部署，提供CLI。公平代码许可，非完全开源（Sustainable Use License + Enterprise License）。

## 核心能力
- AI-Native：构建multi-step agents，使用自己的数据/模型/工具
- 模型灵活性：对接OpenAI, Anthropic, Google, 开源模型，可切换
- 从原型到生产：逻辑、工具使用、人工审批、全面可观测性
- 代码当需：JS/Python/npm包
- 企业就绪：RBAC、审计、敏感数据支持
- 大量集成和模板

## 适用场景
- 需要自动化业务流程的个人/团队
- AI工作流（如RAG、agent工具调用、审批流）
- 自托管环境（数据敏感、合规要求）
- 开发者想要低代码但保留自定义代码能力

## 同类对比
与Zapier/Make相比，n8n自托管能力、代码扩展性和公平代码更受开发者欢迎；与Node-RED相比，n8n更注重商业工作流和AI集成，UI更现代；与GitHub Actions等CICD工具不同，n8n侧重业务API集成和AI orchestration。但未进行详细benchmark，需自行评估。

## 版本动态
最近版本2.48.5（2026-11-18）修复了AI Agent Node工具调用历史、流式文本换行、fresh installs随机instance ID、表达式引擎处理等。表明持续高活跃维护，关注AI模块和核心稳定性。
---

## ℹ️ 置信度与信息盲区

- 置信度：**medium**
- 信息盲区：未提供详细的本地开发环境依赖（Node.js版本等）；没有benchmark数据或性能指标；许可模型的具体限制（Sustainable Use License和Enterprise License区别）未在README中详述；未说明系统资源要求