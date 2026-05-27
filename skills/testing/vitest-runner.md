---
name: vitest-runner
description: Ejecuta tests con Vitest (modo run, sin watch). Ideal para proyectos Vite.
category: testing
version: 1.0.0
type: bash
timeout: 180000
parameters:
  - name: pattern
    type: string
    description: Patrón de archivos de test
outputs:
  - name: output
    type: string
    description: Resultados de Vitest
  - name: exitCode
    type: integer
    description: 0 si todos pasan
---

npx vitest run {pattern}
