# Tools & Actions

## What is a tool?

A **tool** is a function the agent can call to interact with the external world. It has:

- A **name** (used by the LLM to reference it)
- A **description** (tells the LLM when and how to use it)
- A typed **signature** (arguments and return type)

## Defining a tool with smolagents

```python
from smolagents import tool

@tool
def get_weather(city: str) -> str:
    """Return current weather for a given city.

    Args:
        city: Name of the city, e.g. 'Paris'.
    """
    # ... call a weather API ...
    return f"Sunny, 22°C in {city}"
```

The `@tool` decorator automatically extracts the JSON schema from the docstring and type hints, so the LLM knows exactly how to call it.

## Tool categories

| Category | Examples |
|----------|---------|
| Information retrieval | Web search, Wikipedia lookup, RAG |
| Computation | Python REPL, calculator |
| I/O | File read/write, email, calendar |
| External services | APIs, databases |
| Perception | Image captioning, OCR |

## Notes

_Add your own notes and tool experiments here._
