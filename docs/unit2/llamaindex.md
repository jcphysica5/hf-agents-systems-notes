# LlamaIndex

> A data framework for building LLM-powered agents over structured and unstructured data.

## Installation

```bash
pip install llama-index
```

## Core abstractions

| Abstraction | Purpose |
|-------------|---------|
| `VectorStoreIndex` | Index documents for semantic search |
| `QueryEngine` | Answer questions over an index |
| `FunctionTool` | Wrap a Python function as an agent tool |
| `ReActAgent` | Agent using ReAct over a set of tools |
| `Workflow` | Event-driven pipeline for complex flows |

## Minimal agent example

```python
from llama_index.core import VectorStoreIndex, SimpleDirectoryReader
from llama_index.core.tools import QueryEngineTool
from llama_index.core.agent import ReActAgent
from llama_index.llms.openai import OpenAI

# Load and index documents
docs = SimpleDirectoryReader("./data").load_data()
index = VectorStoreIndex.from_documents(docs)

# Wrap as a tool
query_tool = QueryEngineTool.from_defaults(
    query_engine=index.as_query_engine(),
    name="knowledge_base",
    description="Answers questions using the indexed documents.",
)

# Create agent
llm = OpenAI(model="gpt-4o-mini")
agent = ReActAgent.from_tools([query_tool], llm=llm, verbose=True)

response = agent.chat("Summarize the main findings.")
print(response)
```

## Workflows

LlamaIndex **Workflows** are an event-driven alternative to the ReAct loop for building multi-step pipelines with explicit control flow.

```python
from llama_index.core.workflow import Workflow, StartEvent, StopEvent, step

class MyWorkflow(Workflow):
    @step
    async def run_step(self, ev: StartEvent) -> StopEvent:
        result = f"Processed: {ev.input}"
        return StopEvent(result=result)
```

## Notes & experiments

_Add your LlamaIndex notes and experiment results here._
