### 安装（Claude Code）
```bash
git clone https://github.com/sybil-solutions/inference-optimisation-skill
mkdir -p ~/.claude/skills
cp -r inference-optimisation-skill/skills/inference-optimisation ~/.claude/skills/
```
其他 agent 可直接指向 SKILL.md 或使用 PROMPT.md。

### 最小可用示例
```bash
S=skills/inference-optimisation
python3 $S/scripts/ceiling.py $S/examples/ceiling-ornith-b390.json   # 计算理论上限
mkdir -p configs && cp $S/examples/config-existing-server.json configs/base.json   # 修改 base_url/model
python3 $S/scripts/bench.py run configs/base.json --long 131072     # 单次基准
bash $S/scripts/queue.sh base cand base                              # 对照 A/B
python3 $S/scripts/bench.py show                                     # 查看 ledger 表格
```

### 依赖前提
- Python 3 标准库（无额外 pip 包）
- bash 环境
- 可访问的 OpenAI-compatible 本地 LLM server