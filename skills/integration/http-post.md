---
name: http-post
description: Realiza una petición HTTP POST con body JSON a una URL. Requiere curl.
model: sonnet
tools: []
---

curl -s -X POST -H "Content-Type: application/json" -d '{body}' --max-time 10 "{url}"
