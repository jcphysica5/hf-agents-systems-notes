# Thoughts, Actions & Observations

## The ReAct pattern

**ReAct** (Reasoning + Acting) is the most common prompting pattern for agents. Each step of the loop has three parts:

| Part | Description |
|------|-------------|
| **Thought** | The LLM reasons about what to do next |
| **Action** | A tool call (name + arguments) |
| **Observation** | The result returned by the tool |

### Example trace

```
Thought: The user wants to know the population of France.
         I should search for it.
Action: web_search(query="France population 2024")
Observation: France has approximately 68 million inhabitants (2024).

Thought: I now have the answer.
Action: final_answer("France has approximately 68 million inhabitants.")
```

## Code agents

A **code agent** writes Python code as its action instead of calling structured tool APIs. The code is executed in a sandbox and the stdout/stderr become the observation.

```python
# LLM generates this code:
result = 2 ** 10
print(result)
# Observation: 1024
```

Code agents are more flexible because they can compose multiple tool calls in a single step using control flow (loops, conditions, etc.).

## Notes

_Add your own notes, traces and experiments here._
