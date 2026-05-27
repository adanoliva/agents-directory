---
name: node-script
description: Ejecuta un archivo JavaScript con Node.js
category: execution
version: 1.0.0
type: bash
timeout: 60000
parameters:
  - name: file
    type: string
    required: true
    description: Ruta al archivo .js a ejecutar
  - name: args
    type: string
    description: Argumentos adicionales para el script
outputs:
  - name: output
    type: string
    description: Stdout del script
  - name: exitCode
    type: integer
    description: Código de salida
---

node {file} {args}
