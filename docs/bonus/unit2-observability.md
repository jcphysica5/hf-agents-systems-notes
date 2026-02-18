# Bonus Unit 2 — Observability & Evaluation

## Overview

As agents become more complex, **observability** — the ability to inspect what the agent did and why — becomes essential for debugging and improvement.

## Key questions observability answers

- Which tool calls were made, in what order?
- How long did each step take?
- Where did the agent fail or hallucinate?
- Which sub-task caused a wrong final answer?

## Tracing with OpenTelemetry

smolagents integrates with OpenTelemetry-compatible backends (Langfuse, Arize Phoenix, etc.):

```python
from opentelemetry.sdk.trace import TracerProvider
from opentelemetry.sdk.trace.export import SimpleSpanProcessor
from openinference.instrumentation.smolagents import SmolagentsInstrumentor

# Configure your exporter (e.g. Langfuse, Phoenix)
provider = TracerProvider()
provider.add_span_processor(SimpleSpanProcessor(your_exporter))

SmolagentsInstrumentor().instrument(tracer_provider=provider)
```

## Evaluation metrics

| Metric | Description |
|--------|-------------|
| **Exact match** | Is the final answer exactly correct? |
| **F1 / ROUGE** | Partial credit for text overlap |
| **Tool accuracy** | Did the agent call the right tools? |
| **Steps to answer** | Efficiency of the trajectory |
| **Cost** | Total tokens consumed |

## LLM-as-judge

```python
from smolagents import HfApiModel

judge_model = HfApiModel(model_id="meta-llama/Meta-Llama-3-8B-Instruct")

def llm_judge(question: str, answer: str, reference: str) -> bool:
    prompt = f"""Question: {question}
Reference answer: {reference}
Agent answer: {answer}
Is the agent answer correct? Reply only YES or NO."""
    response = judge_model(prompt)
    return "YES" in response.upper()
```

## Notes & experiments

_Add your observability setup and evaluation results here._
