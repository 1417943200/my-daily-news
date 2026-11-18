## 安装
需要 Python 3.11 和 Conda：
```bash
conda create -n paper_orchestra python=3.11
conda activate paper_orchestra
pip install -r requirements.txt
```
在根目录创建 `.env`，至少配置一种 LLM 钥匙（Gemini 或 OpenAI）和可选 Semantic Scholar key。

## 最小可用示例
```bash
python paper_writing_cli.py --raw_materials_dir /path_to_your_raw_materials/ --latex_template_dir /path_to_your_latex_template/ --output_dir /path_to_your_output_folder/ --use_plotting true
```
也可运行 `./paper_writing_cli.sh`。需准备原始材料目录和 LaTeX 模板目录；模板可参考 `templates/cvpr2025` 或按同样结构新增。

## 依赖前提
- 至少一个可用 LLM API：`GEMINI_API_KEY` 或 `VERTEX_AI_PROJECT`+`VERTEX_AI_LOCATION` 或 `OPENAI_API_KEY`。
- 文献搜索可选 `SEMANTIC_SCHOLAR_API_KEY`。
- 演示邮件通知需 SMTP 配置，非必需。
- 数据集未包含，需自行准备放在 `datasets/`（官方称后续发布）。