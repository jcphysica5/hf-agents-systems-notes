# smolagents

> A lightweight library by Hugging Face for building capable AI agents with minimal boilerplate.

## Installation

```bash
pip install smolagents
```

## Core concepts

### ToolCallingAgent vs. CodeAgent

`smolagents` ships with two agent classes:

- **`ToolCallingAgent`** — the LLM selects tools via structured JSON calls (classic ReAct)
- **`CodeAgent`** — the LLM writes Python code; tools are Python functions in scope

### Minimal example

```python
from smolagents import CodeAgent, DuckDuckGoSearchTool, HfApiModel

model = HfApiModel()  # uses the default Qwen model on HF Inference
agent = CodeAgent(tools=[DuckDuckGoSearchTool()], model=model)

agent.run("How many seconds are in a year?")
```

## Defining custom tools

```python
from smolagents import tool

@tool
def celsius_to_fahrenheit(celsius: float) -> float:
    """Convert a temperature from Celsius to Fahrenheit.

    Args:
        celsius: Temperature in degrees Celsius.
    """
    return celsius * 9 / 5 + 32
```

## Multi-agent systems

```python
from smolagents import CodeAgent, HfApiModel, ManagedAgent

model = HfApiModel()

web_agent = ManagedAgent(
    agent=CodeAgent(tools=[DuckDuckGoSearchTool()], model=model),
    name="web_search",
    description="Searches the web for up-to-date information.",
)

manager = CodeAgent(tools=[], model=model, managed_agents=[web_agent])
manager.run("What is the latest news about AI agents?")
```

## Notes & experiments

_Add your smolagents notes and experiment results here._
