---
name: test-runner
description: Ejecuta los tests del proyecto via npm test
category: testing
version: 1.2.0
type: bash
timeout: 180000
parameters:
  - name: args
    type: string
    description: Argumentos extra para el runner de tests
outputs:
  - name: output
    type: string
    description: Resultado de los tests
  - name: exitCode
    type: integer
    description: 0 si todos pasan, distinto de 0 si fallan
---

npm test {args}
