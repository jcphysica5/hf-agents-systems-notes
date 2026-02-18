# Unit 0 — Welcome & Setup

## Overview

This unit covers everything you need to get started:

- Understanding what the course is about
- Setting up your development environment
- Getting access to the required APIs and tools

## Environment setup

### 1. Clone this repository

```bash
git clone https://github.com/jcphysica5/hf-agents-systems-notes.git
cd hf-agents-systems-notes
```

### 2. Create the conda environment

```bash
conda env create -f environment.yml
conda activate hf-agents-env
```

### 3. Configure API keys

Create a `.env` file at the root of the project:

```bash
HF_TOKEN=hf_...          # Hugging Face token (Settings → Access Tokens)
OPENAI_API_KEY=sk-...    # Optional — only if you use OpenAI models
```

!!! warning
    Never commit your `.env` file. It is already listed in `.gitignore`.

## Key tools used in this course

| Tool | Purpose |
|------|---------|
| `smolagents` | Lightweight agent library by Hugging Face |
| `transformers` | Model loading & inference |
| `huggingface_hub` | Accessing HF Hub models and spaces |
| `langchain` / `langgraph` | Agent orchestration |
| `llama-index` | Data-centric agent framework |

## Notes

_Add your own notes here as you work through the setup._
