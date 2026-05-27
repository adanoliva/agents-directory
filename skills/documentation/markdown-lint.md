---
name: markdown-lint
description: Verifica el formato de los archivos Markdown del proyecto. Requiere markdownlint-cli.
category: documentation
version: 1.1.0
type: bash
timeout: 30000
requires: markdownlint-cli
parameters:
  - name: path
    type: string
    description: Archivos a verificar (default: **/*.md)
outputs:
  - name: output
    type: string
    description: Errores de formato encontrados
  - name: exitCode
    type: integer
    description: 0 si no hay errores
---

npx markdownlint {path}
