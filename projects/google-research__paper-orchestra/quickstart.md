## 安装
```bash
conda create -n paper_orchestra python=3.11
conda activate paper_orchestra
pip install -r requirements.txt
```

## 配置环境变量
在项目根目录创建 `.env`，按需填写：
```env
SEMANTIC_SCHOLAR_API_KEY=...
OPENAI_API_KEY=...
VERTEX_AI_PROJECT=...
VERTEX_AI_LOCATION=...
GEMINI_API_KEY=...
```

## 最小可用示例
```bash
python paper_writing_cli.py --raw_materials_dir /path_to_your_raw_materials/ --latex_template_dir /path_to_your_latex_template/ --output_dir /path_to_your_output_folder/ --use_plotting true
```

## 依赖前提
- Python 3.11 环境
- 至少一个可用 LLM API：OpenAI 或 Gemini/Vertex AI
- 可选 Semantic Scholar API key
- 准备好原始材料目录和 LaTeX 模板目录
- README 未明确是否要求本地 LaTeX 编译环境；若需编译 PDF 可能需要额外安装 TeX 发行版