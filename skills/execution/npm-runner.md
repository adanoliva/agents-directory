---
name: npm-runner
description: Ejecuta un script de npm del package.json (npm run <script>)
category: execution
version: 1.1.0
type: bash
timeout: 120000
parameters:
  - name: script
    type: string
    required: true
    description: Nombre del script (ej: build, start, lint)
outputs:
  - name: output
    type: string
    description: Output del script
  - name: exitCode
    type: integer
    description: Código de salida
---

npm run {script}
