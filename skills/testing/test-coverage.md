---
name: test-coverage
description: Ejecuta los tests y genera reporte de cobertura de código
category: testing
version: 1.0.0
type: bash
timeout: 300000
parameters: []
outputs:
  - name: output
    type: string
    description: Reporte de cobertura
  - name: exitCode
    type: integer
    description: 0 si todos pasan
---

npx jest --coverage --no-coverage-provider=v8 2>&1 || npx vitest run --coverage 2>&1
