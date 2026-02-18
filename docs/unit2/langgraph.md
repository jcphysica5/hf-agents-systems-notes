# LangGraph

> A library for building stateful, multi-actor applications with LLMs using directed graphs.

## Installation

```bash
pip install langgraph langchain-openai
```

## Core concepts

| Concept | Description |
|---------|-------------|
| **State** | A typed dict shared across all nodes |
| **Node** | A function that reads and writes to state |
| **Edge** | A connection between nodes (can be conditional) |
| **Graph** | The assembled pipeline |

## Minimal ReAct agent

```python
from langgraph.prebuilt import create_react_agent
from langchain_openai import ChatOpenAI
from langchain_core.tools import tool

@tool
def get_weather(city: str) -> str:
    """Get current weather for a city."""
    return f"Sunny, 22°C in {city}"

model = ChatOpenAI(model="gpt-4o-mini")
agent = create_react_agent(model, tools=[get_weather])

result = agent.invoke({"messages": [("user", "What's the weather in Paris?")]})
print(result["messages"][-1].content)
```

## Building a custom graph

```python
from typing import TypedDict, Annotated
from langgraph.graph import StateGraph, END
import operator

class AgentState(TypedDict):
    messages: Annotated[list, operator.add]

def call_model(state: AgentState):
    # ... call LLM ...
    return {"messages": [response]}

def should_continue(state: AgentState):
    last = state["messages"][-1]
    return "tools" if last.tool_calls else END

graph = StateGraph(AgentState)
graph.add_node("agent", call_model)
graph.set_entry_point("agent")
graph.add_conditional_edges("agent", should_continue)
app = graph.compile()
```

## Persistence & human-in-the-loop

LangGraph supports checkpointing so agents can pause and resume:

```python
from langgraph.checkpoint.memory import MemorySaver

checkpointer = MemorySaver()
app = graph.compile(checkpointer=checkpointer, interrupt_before=["tools"])
```

## Notes & experiments

_Add your LangGraph notes and experiment results here._
