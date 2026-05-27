---
name: dead-code-finder
description: Busca exports de TypeScript que no se importan en ningún otro archivo del proyecto
category: code-quality
version: 1.0.0
type: bash
timeout: 60000
parameters:
  - name: config
    type: string
    description: Ruta al tsconfig.json (default: tsconfig.json)
outputs:
  - name: output
    type: string
    description: Exports no utilizados
  - name: exitCode
    type: integer
    description: 0 si no hay código muerto
---

npx ts-unused-exports tsconfig.json
