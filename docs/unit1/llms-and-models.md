# LLMs & the Model Family

## Role of LLMs in agents

The LLM is the **brain** of the agent. It:

- Interprets the user's goal
- Decides which tool to use (and with what arguments)
- Synthesizes observations into a final answer

## Model families

| Family | Examples | Notes |
|--------|---------|-------|
| Open-weight | Llama 3, Mistral, Qwen | Run locally or on HF Inference |
| Proprietary | GPT-4o, Claude 3.5 | API access only |
| Code-specialized | DeepSeek-Coder, StarCoder | Better for code tools |

## Special tokens

Chat models use special tokens to structure conversation turns. Example (Llama 3 format):

```
<|begin_of_text|>
<|start_header_id|>system<|end_header_id|>
You are a helpful assistant.<|eot_id|>
<|start_header_id|>user<|end_header_id|>
What is 2+2?<|eot_id|>
<|start_header_id|>assistant<|end_header_id|>
```

Agents inject **tool schemas** and **observations** into these structured turns.

## Accessing models via HF Hub

```python
from huggingface_hub import InferenceClient

client = InferenceClient(model="meta-llama/Meta-Llama-3-8B-Instruct")
response = client.chat_completion(
    messages=[{"role": "user", "content": "Hello!"}],
    max_tokens=256,
)
print(response.choices[0].message.content)
```

## Notes

_Add your own notes and experiments here._
