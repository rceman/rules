# 🛎️ Agno Framework Rules

## 1. Tool Design

Each tool is a **class** with:

* `name`
* `description`
* `run(**kwargs)` signature

Keep side‑effects inside `run`; avoid globals.

## 2. Agent Wiring

```python
from agno import Agent

agent = Agent(
    model="qwen3-1.7b",
    tools=[vision_tool, control_tool, edit_tool],
    memory="local"
)
```

## 3. Prompt Templates

* System prompt defines role.  
* User prompt comes from CLI.  
* Add a *reflection chain* if tasks are long (> 20 steps).

## 4. Limits

* `max_tokens = 2048`.
* Timeout long steps with `asyncio.wait_for`.
