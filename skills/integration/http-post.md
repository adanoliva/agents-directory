---
name: http-post
description: Realiza una petición HTTP POST con body JSON a una URL. Requiere curl.
category: integration
version: 1.1.0
type: bash
timeout: 15000
requires: curl
parameters:
  - name: url
    type: string
    required: true
    description: URL destino
  - name: body
    type: string
    required: true
    description: Body JSON de la petición (string escapado)
  - name: token
    type: string
    description: Bearer token de autorización (opcional)
outputs:
  - name: output
    type: string
    description: Respuesta del servidor
  - name: exitCode
    type: integer
    description: 0 si la petición fue exitosa
---

curl -s -X POST -H "Content-Type: application/json" -d '{body}' --max-time 10 "{url}"
