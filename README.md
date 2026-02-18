# HF Agents Course — Notes & Experiments

Personal notes and hands-on experiments following the [Hugging Face Agents Course](https://github.com/huggingface/agents-course).

The site is built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) and deployed to GitHub Pages.

**Live site:** https://jcphysica5.github.io/hf-agents-systems-notes/

## Local development

```bash
# Create and activate the environment
conda env create -f environment.yml
conda activate hf-agents-env

# Serve the docs locally (hot-reload)
mkdocs serve
```

Open http://127.0.0.1:8000 in your browser.

## Project structure

```
hf-agents-systems-notes/
├── docs/                  # MkDocs content
│   ├── index.md
│   ├── unit0/
│   ├── unit1/
│   ├── unit2/
│   ├── unit3/
│   ├── unit4/
│   ├── bonus/
│   ├── experiments/
│   ├── assets/
│   ├── css/
│   └── javascripts/
├── notebooks/             # Jupyter notebooks
│   ├── unit1/
│   ├── unit2/
│   ├── unit3/
│   └── experiments/
├── .github/workflows/     # GitHub Actions CI/CD
├── mkdocs.yml
├── requirements.txt
└── environment.yml
```

## License

MIT
