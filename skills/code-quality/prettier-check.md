---
name: prettier-check
description: Verifica si el código cumple el formato de Prettier sin modificar nada
category: code-quality
version: 1.0.0
type: bash
timeout: 30000
parameters:
  - name: path
    type: string
    description: Archivos a comprobar (default: .)
outputs:
  - name: output
    type: string
    description: Archivos que no cumplen el formato
  - name: exitCode
    type: integer
    description: 0 si todo cumple el formato
---

npx prettier --check {path}
