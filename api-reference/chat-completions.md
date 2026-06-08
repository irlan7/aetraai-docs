---
title: Chat Completions
description: OpenAI-compatible chat completions API
---

# Chat Completions

AetraAI provides an **OpenAI-compatible** chat completions endpoint. Drop-in replacement — just change `base_url` and `api_key`.

## Base URL
https://api.aetraai.com/api/v1
## Available Models

| Model | Description | Speed |
|-------|-------------|-------|
| `aetra-haiku` | Fast & lightweight | ~2s |
| `aetra-sonnet` | Balanced, best for most tasks | ~5s |
| `aetra-opus` | Most powerful | ~10s |
| `aetra-coder` | Code specialist, 15+ languages | ~4s |
| `aetra-trader` | Forex & crypto analyst | ~5s |
| `aetra-chain` | Web3 & Solidity specialist | ~5s |

## Request

```bash
curl https://api.aetraai.com/api/v1/v1/chat/completions \
  -H "Authorization: Bearer sk-aetra-YOUR_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "aetra-sonnet",
    "messages": [
      {"role": "user", "content": "Write a Go REST API"}
    ],
    "stream": false,
    "max_tokens": 4096
  }'
```

## Response

```json
{
  "id": "chatcmpl-aetraai-001",
  "object": "chat.completion",
  "model": "aetra-sonnet",
  "choices": [{
    "message": {
      "role": "assistant",
      "content": "Here is a Go REST API..."
    },
    "finish_reason": "stop"
  }],
  "usage": {
    "prompt_tokens": 12,
    "completion_tokens": 150,
    "total_tokens": 162
  }
}
```

## Python SDK

```python
from openai import OpenAI

client = OpenAI(
    api_key="sk-aetra-YOUR_KEY",
    base_url="https://api.aetraai.com/api/v1"
)

response = client.chat.completions.create(
    model="aetra-sonnet",
    messages=[{"role": "user", "content": "Hello!"}]
)
print(response.choices[0].message.content)
```

## JavaScript SDK

```javascript
import OpenAI from "openai";

const client = new OpenAI({
  apiKey: "sk-aetra-YOUR_KEY",
  baseURL: "https://api.aetraai.com/api/v1",
});

const response = await client.chat.completions.create({
  model: "aetra-sonnet",
  messages: [{ role: "user", content: "Hello!" }],
});
```

## Go SDK

```go
cfg := openai.DefaultConfig("sk-aetra-YOUR_KEY")
cfg.BaseURL = "https://api.aetraai.com/api/v1"
client := openai.NewClientWithConfig(cfg)
```

## Streaming

```python
stream = client.chat.completions.create(
    model="aetra-sonnet",
    messages=[{"role": "user", "content": "Write a REST API"}],
    stream=True
)
for chunk in stream:
    if chunk.choices[0].delta.content:
        print(chunk.choices[0].delta.content, end="")
```
