[![Logo](https://www.virtua.cloud/img/logo_48.png)](https://www.virtua.cloud "Cloud Hosting Provider")

# Virtua.Cloud REST API

Deploy and manage your cloud infrastructure programmatically.

## Full reference

The complete, always-up-to-date API reference is available inside the Virtua.Cloud Manager:

**[https://manager.virtua.cloud/docs/api](https://manager.virtua.cloud/docs/api)** *(login required)*

You can also manage your API keys at **Account > API Keys** once logged in.

## Quickstart

### 1. Get an API key

Log in to the [Virtua.Cloud Manager](https://manager.virtua.cloud), open **Account > API Keys**, and create a key. Optionally restrict it to a list of allowed source IPs.

### 2. Make a request

All requests use Bearer authentication and return JSON.

Base URL: `https://api.virtua.cloud/v1`

```bash
curl -H "Authorization: Bearer YOUR_API_KEY" \
     -H "Content-Type: application/json" \
     https://api.virtua.cloud/v1/account
```

Successful responses include `"success": true`. Error responses include `"success": false`, an `"error"` code, and usually a `"messages"` array.

### 3. Common endpoints

| Method | Path | Description |
|--------|------|-------------|
| `GET` | `/account` | Account balance, usage, limits |
| `GET` | `/cloud-server` | List your cloud servers |
| `GET` | `/cloud-server/{uuid}` | Server details (status, IPs, config) |
| `POST` | `/cloud/order` | Deploy a new cloud server |
| `POST` | `/cloud-server/{uuid}/password` | Retrieve `root` / `manager` / `rescue` password and matching username |
| `GET` | `/project` | List projects (each with its `uuid`) |
| `GET` | `/cloud/offers` | List available offers |
| `GET` | `/cloud/systems` | List available operating systems |

The full reference covers cart/checkout, BGP sessions, IX ports, DDoS protection, networking, billing, and more — see the in-app docs link above.

## Rate limits

| Category | Limit |
|----------|-------|
| Pre-auth (per IP) | 30 req/min |
| Read (per account) | 60 req/min |
| Write (per account) | 20 req/min |
| Critical (per account) | 5 req/min |

When throttled, responses return `429 Too Many Requests` with a `Retry-After` header.

## Support

Email **hello@virtua.cloud**.

---

> **Note on the OpenAPI files in this repo:** `openapi3_0.yaml` / `openapi3_0.json` are stale (last updated July 2024) and do not reflect current endpoints, authentication, or response shapes. They will be regenerated. In the meantime, please rely on the in-app documentation above.
