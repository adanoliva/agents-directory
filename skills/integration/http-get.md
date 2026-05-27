---
name: http-get
description: Realiza una petición HTTP GET a una URL y devuelve la respuesta. Requiere curl.
category: integration
version: 1.1.0
type: bash
timeout: 15000
requires: curl
parameters:
  - name: url
    type: string
    required: true
    description: URL a consultar
  - name: headers
    type: string
    description: Headers adicionales en formato "Key: Value" separados por coma
outputs:
  - name: output
    type: string
    description: Cuerpo de la respuesta HTTP
  - name: exitCode
    type: integer
    description: 0 si la petición fue exitosa
---

curl -s -L --max-time 10 "{url}"
