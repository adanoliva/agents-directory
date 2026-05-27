---
name: eslint-checker
description: Comprueba el código con ESLint y muestra los errores/warnings. Requiere eslint configurado.
category: code-quality
version: 1.1.0
type: bash
timeout: 60000
parameters:
  - name: path
    type: string
    description: Ruta o patrón a analizar (default: . — todo el proyecto)
outputs:
  - name: output
    type: string
    description: Errores y warnings encontrados
  - name: exitCode
    type: integer
    description: 0 si no hay errores
---

npx eslint {path}
