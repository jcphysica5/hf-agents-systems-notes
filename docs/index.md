# Hugging Face Agents Course — Notes & Experiments

> Personal notes, experiments and implementations following the
> [Hugging Face Agents Course](https://github.com/huggingface/agents-course).

---

## What is this site?

This site collects my personal study notes and hands-on experiments as I work through the **Hugging Face Agents Course**. It is not a replacement for the official material — rather, it is a living notebook where I deepen my understanding by re-explaining concepts in my own words, running code experiments, and building small projects.

## Course outline

| Unit | Topic |
|------|-------|
| [Unit 0](unit0/index.md) | Welcome, setup & tools |
| [Unit 1](unit1/index.md) | Agent fundamentals — LLMs, tools, thoughts, actions & observations |
| [Unit 2](unit2/index.md) | Agent frameworks — smolagents, LlamaIndex, LangGraph |
| [Unit 3](unit3/index.md) | Agentic RAG |
| [Unit 4](unit4/index.md) | Capstone project & automated evaluation |
| [Bonus](bonus/unit1-finetuning.md) | Fine-tuning, observability, agents in games |

## Prerequisites

- Basic Python programming
- Familiarity with large language models (prompting, inference APIs)

## How to run the notebooks

All notebooks live inside `notebooks/`. Install the environment and launch Jupyter:

```bash
conda env create -f environment.yml
conda activate hf-agents-env
jupyter lab
```

Or open them directly on Google Colab using the links provided on each page.

---

!!! tip "Official course"
    Follow the original course at [huggingface.co/learn/agents-course](https://huggingface.co/learn/agents-course) and join the community on the [HF Discord](https://discord.gg/huggingface).
