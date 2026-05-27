---
name: eslint-fix
description: Corrige automáticamente los problemas de ESLint que tienen solución automática
category: code-quality
version: 1.0.0
type: bash
timeout: 60000
parameters:
  - name: path
    type: string
    description: Ruta o patrón a corregir (default: .)
outputs:
  - name: output
    type: string
    description: Reporte de correcciones aplicadas
  - name: exitCode
    type: integer
    description: 0 si no quedan errores
---

npx eslint --fix {path}
