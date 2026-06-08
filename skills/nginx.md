---
name: nginx
description: Nginx como reverse proxy, balanceador de carga y servidor estático
model: sonnet
tools: []
---

## Nginx Rules

**Server Blocks:**
- One `server` block per domain/app. Use `include` for shared config snippets.
- Always define `server_name` explicitly — avoid catch-all blocks in production.
- Serve static files directly from Nginx; proxy only dynamic requests.

**Reverse Proxy:**
- Set required headers on every proxy block:
  ```nginx
  proxy_set_header Host $host;
  proxy_set_header X-Real-IP $remote_addr;
  proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  proxy_set_header X-Forwarded-Proto $scheme;
  ```
- Set `proxy_read_timeout`, `proxy_connect_timeout` explicitly (default 60s).
- Use `upstream` blocks for load balancing; define `keepalive 32`.

**TLS/HTTPS:**
- Redirect all HTTP to HTTPS with a permanent `301`.
- Use `ssl_protocols TLSv1.2 TLSv1.3` only.
- Set `ssl_session_cache shared:SSL:10m` and `ssl_session_timeout 1d`.
- Add HSTS: `add_header Strict-Transport-Security "max-age=31536000; includeSubDomains"`.

**Security Headers:**
- `X-Frame-Options DENY`, `X-Content-Type-Options nosniff`, `Referrer-Policy same-origin`.
- Configure `Content-Security-Policy` per application.

**Performance:**
- Enable `gzip on` with `gzip_types text/html text/css application/javascript application/json`.
- Set `sendfile on`, `tcp_nopush on`, `tcp_nodelay on`.
- Cache static assets: `expires 1y; add_header Cache-Control "public, immutable"`.
- Set `client_max_body_size` for upload endpoints.
