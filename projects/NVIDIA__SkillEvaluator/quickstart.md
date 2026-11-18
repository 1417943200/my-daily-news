## 安装
需要 Python 3.12–3.14。基础安装：
```bash
pip install skillevaluator
```
或使用 uv：
```bash
uv tool install --python 3.13 skillevaluator
```
完整功能（Tier2/3）需要：
```bash
pip install "skillevaluator[all]"
```
并配置 LLM 提供方（如 NVIDIA Build 免费密钥）和 Docker。

## 最小可用示例
无密钥快速检查技能质量：
```bash
skillevaluator quality-check ./my-skill
```
检查跨代理兼容性（无需密钥和代理）：
```bash
skillevaluator harness-check ./my-skill
```
运行完整三层评估（需设置 NVIDIA_API_KEY 和 Docker）：
```bash
export SKILL_EVAL_LLM_PROVIDER=nv_build
export NVIDIA_API_KEY='nvapi-...'
skillevaluator validate ./my-skill
```

## 依赖前提
- Tier1 静态检查大部分无需外部依赖，但完整安全扫描需要安装系统工具（SkillSpector、Gitleaks、Bandit，Semgrep 可选）。
- Tier2 需要嵌入和聊天模型，推荐使用 NVIDIA Build 免费密钥或自备 provider。
- Tier3 需要支持代理和运行中的沙箱（默认 Docker）。
- 若使用 NeMo Gym 后端，需额外配置（参见官方文档）。