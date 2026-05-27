---
name: prettier-fix
description: Aplica el formato de Prettier a los archivos del proyecto
category: code-quality
version: 1.0.0
type: bash
timeout: 30000
parameters:
  - name: path
    type: string
    description: Archivos a formatear (default: .)
outputs:
  - name: output
    type: string
    description: Archivos formateados
  - name: exitCode
    type: integer
    description: 0 si éxito
---

npx prettier --write {path}
