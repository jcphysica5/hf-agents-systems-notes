# Bonus Unit 1 — Fine-tuning LLMs for Function Calling

## Overview

This bonus unit covers how to fine-tune open-weight LLMs so they become better at **function calling** — the skill of producing well-formed tool-call JSON when acting as an agent.

## Why fine-tune for function calling?

Base models and even many instruction-tuned models struggle with:

- Generating valid JSON schemas consistently
- Choosing the right tool when multiple are available
- Producing correct argument types and values

Fine-tuning on function-call datasets teaches the model the expected format.

## Dataset formats

Two common formats are used:

=== "OpenAI format"
    ```json
    {
      "messages": [
        {"role": "user", "content": "What is the weather in Paris?"},
        {"role": "assistant", "tool_calls": [{
          "type": "function",
          "function": {"name": "get_weather", "arguments": "{\"city\": \"Paris\"}"}
        }]}
      ]
    }
    ```

=== "ShareGPT format"
    ```json
    {
      "conversations": [
        {"from": "human", "value": "What is the weather in Paris?"},
        {"from": "gpt", "value": "<tool_call>\n{\"name\": \"get_weather\", \"arguments\": {\"city\": \"Paris\"}}\n</tool_call>"}
      ]
    }
    ```

## Training with TRL

```python
from trl import SFTTrainer, SFTConfig
from transformers import AutoModelForCausalLM, AutoTokenizer

model = AutoModelForCausalLM.from_pretrained("Qwen/Qwen2.5-0.5B-Instruct")
tokenizer = AutoTokenizer.from_pretrained("Qwen/Qwen2.5-0.5B-Instruct")

trainer = SFTTrainer(
    model=model,
    train_dataset=dataset,
    args=SFTConfig(output_dir="./output", num_train_epochs=3),
)
trainer.train()
```

## Notes & experiments

_Add your fine-tuning notes, training curves and evaluation results here._
