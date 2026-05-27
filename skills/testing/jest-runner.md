---
name: jest-runner
description: Ejecuta tests con Jest. Permite filtrar por patrón de archivo o nombre de test.
category: testing
version: 1.0.0
type: bash
timeout: 180000
parameters:
  - name: pattern
    type: string
    description: Patrón de archivos de test (ej: Button.test)
  - name: testName
    type: string
    description: Filtro por nombre de test (-t)
outputs:
  - name: output
    type: string
    description: Resultados de Jest
  - name: exitCode
    type: integer
    description: 0 si todos pasan
---

npx jest {pattern}
