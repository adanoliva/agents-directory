---
name: bash-runner
description: Ejecuta cualquier comando bash/shell en el directorio del proyecto
category: execution
version: 1.1.0
type: bash
timeout: 30000
parameters:
  - name: cmd
    type: string
    required: true
    description: Comando a ejecutar
  - name: timeout
    type: integer
    description: Timeout en ms (default: 30000)
outputs:
  - name: output
    type: string
    description: Stdout + stderr del comando
  - name: exitCode
    type: integer
    description: Código de salida (0 = éxito)
---

{cmd}
