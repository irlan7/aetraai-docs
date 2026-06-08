---
title: API Keys
description: Generate and manage sk-aetra-... API keys
---

# API Keys

AetraAI uses `sk-aetra-...` API keys for authentication. Get your free key at [aetraai.com/api-dashboard](https://aetraai.com/api-dashboard).

## Generate API Key

```bash
curl -X POST https://api.aetraai.com/api/v1/keys/create \
  -H "Content-Type: application/json" \
  -d '{
    "email": "you@example.com",
    "name": "My Trading Bot",
    "plan": "free"
  }'
```

**Response:**
```json
{
  "success": true,
  "data": {
    "key": "sk-aetra-xxxxxxxxxxxx",
    "plan": "free",
    "monthly_limit": 100000
  },
  "warning": "Save your API key now — it will not be shown again!"
}
```

<Warning>
Save your API key immediately. It will **not** be shown again after creation.
</Warning>

## List API Keys

```bash
curl https://api.aetraai.com/api/v1/keys/you@example.com
```

## Revoke API Key

```bash
curl -X POST https://api.aetraai.com/api/v1/keys/revoke \
  -H "Content-Type: application/json" \
  -d '{"email": "you@example.com", "key_id": "KEY_ID"}'
```

## Plans

| Plan | Tokens/month | Price |
|------|-------------|-------|
| Free | 100K | $0 |
| Starter | 1M | $9/mo |
| Pro | 10M | $49/mo |
| Enterprise | Unlimited | Custom |
