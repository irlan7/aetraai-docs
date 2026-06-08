---
title: Memory System
description: Persistent user memory across sessions
---

# Memory System

AetraAI remembers user preferences across sessions — no need to explain your tech stack every time.

## How It Works

1. User sends message with `email` parameter
2. AetraAI auto-detects language preference (Go, Python, Flutter, etc.)
3. Preference saved to CockroachDB
4. Next session, memory injected automatically into AI context

## Load User Memory

```bash
curl https://api.aetraai.com/api/v1/memory/you@example.com
```

**Response:**
```json
{
  "memory": {
    "preferences": {
      "language": "Go",
      "framework": "Fiber",
      "project": "aetraai-core",
      "stack": "Go + CockroachDB + Docker"
    }
  },
  "context": "[MEMORY CONTEXT]\nFavorite language: Go\n[/MEMORY CONTEXT]"
}
```

## Using Memory in Chat

```python
response = client.chat.completions.create(
    model="aetra-coder",
    messages=[{"role": "user", "content": "Build a REST API"}],
    # Memory auto-injected when using AetraAI Python Engine
)
# AI automatically uses Go + Fiber based on saved preferences
```
