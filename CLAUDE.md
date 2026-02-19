# Project instructions for Claude

## &...& convention in .md files

Whenever you see text wrapped in `&` symbols inside any `.md` file under `docs/`,
treat it as an instruction directed at you. Replace the entire `&instruction&` span
(including the `&` delimiters) with your response to that instruction.

**Example:**

```
## My notes

&explain why stop sequences prevent hallucination in one concise paragraph&
```

Should become:

```
## My notes

Stop sequences tell the inference API to halt generation the moment a specific
token pattern appears in the output. In the agent loop this matters because, ...
```

Always replace in-place — do not add extra headings or wrappers around the replacement.
