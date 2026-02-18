# What is an Agent?

## Definition

An **AI agent** is a system that perceives its environment, reasons about it using a language model, and takes actions to achieve a goal — then observes the result and repeats.

More formally, an agent is characterized by:

1. **Perception** — receiving input (user prompt, observations from tools)
2. **Reasoning** — using an LLM to decide what to do next
3. **Action** — calling tools, writing code, browsing the web, etc.
4. **Memory** — keeping track of previous steps (short-term context)

## The agent loop

```
while goal not achieved:
    thought  = LLM.think(context)
    action   = LLM.decide(thought)
    result   = tool.run(action)
    context += [thought, action, result]
```

## Agents vs. simple LLM calls

| Aspect | LLM call | Agent |
|--------|----------|-------|
| Steps | Single | Multiple (loop) |
| Tools | None | Many |
| Memory | No | Short/long-term |
| Autonomy | Low | High |

## Notes

_Add your own notes and observations here._
