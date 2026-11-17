## 它是什么
Sybil Solutions 开源的 Agent skill，用于爬山法优化本地 LLM 推理服务速度。核心是 SKILL.md 工作流：先计算理论上限，再单变量修改，与对照测量，记录失败，以长上下文检索为门禁，最终发布 pinned clean build。覆盖 decode、speculative decoding、prefill、KV cache、startup 和 TTFT 等指标。

## 为什么火
该技能提炼自真实优化过程，附带大量实测数据（Intel Arc B390、RTX 3090、H200 等），展示从 43.6 到 53 tok/s、prefill 2.1x 等提升。它解决“本地推理还能快多少”的工程问题，强调统计严谨（中位数、对照、噪声范围）和物理学天花板，适合想系统调优的极客。

## 技术栈
Python + bash 脚本，bench.py 使用标准库，兼容 OpenAI-compatible server；服务引擎不限定，已对接 vLLM、SGLang、ExLlama、llama.cpp；面向 Claude Code 和其他支持 SKILL.md 的 agent。

## 核心能力
- 理论天花板计算：脚本根据带宽、FLOPs 和组件大小估算 decode/prefill/TTFT/startup/KV 最大值。
- 基准测试：启动、TTFT、单用户/并发 decode、冷 prefill、长上下文 needle、峰值内存控制，结果写 ledger.jsonl。
- 串行队列：queue.sh 实现对照-候选-对照，AC-only，内存看门狗，≥6 样本，中位数比较。
- 稳定性门禁：结果必须通过 full-context needle 和 concurrent full-KV soak，防止“伪优化”。

## 适用场景
- 自托管 LLM 服务，追求最大 tok/s 的个人和团队。
- 不同量化/引擎/硬件（Intel、NVIDIA、Apple、AMD）对比调优。
- 需要可复现评估 speculative decoding 效果的研究者。

## 同类对比
与 vLLM/SGLang 官方 benchmark 或 llama.cpp 性能测试相比，本仓库不提供推理引擎，而是方法论和可执行 harness，强调先算上限、单变量变化和长期稳定性验证。优点是可跨引擎、跨硬件，结果更可靠；缺点是需要自行准备服务，上手门槛稍高。

## 版本动态
仓库创建于 2026-11-16，最近推送同日，Star 854，MIT 许可，无主页。尚无正式 release 或稳定版本号，但已包含 examples 和结果来源链接，更新较为活跃。
---

## ℹ️ 置信度与信息盲区

- 置信度：**high**
- 信息盲区：主页未设置，仓库元数据中主页为 None；创建时间与最近推送均为 2026-11-16（未来日期），真实性待核实；README 未说明 Python 具体版本要求，仅说标准库；结果来源链接指向 PR 和外部仓库，本 README 未完全展开原始数据