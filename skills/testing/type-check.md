---
name: type-check
description: Verifica los tipos TypeScript sin compilar (tsc --noEmit). Requiere tsconfig.json.
category: testing
version: 1.0.0
type: bash
timeout: 120000
parameters:
  - name: config
    type: string
    description: Ruta al tsconfig.json (default: tsconfig.json)
outputs:
  - name: output
    type: string
    description: Errores de tipo encontrados
  - name: exitCode
    type: integer
    description: 0 si no hay errores
---

npx tsc --noEmit
