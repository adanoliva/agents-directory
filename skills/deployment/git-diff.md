---
name: git-diff
description: Muestra los cambios actuales respecto a un commit, rama o HEAD
category: deployment
version: 1.1.0
type: bash
timeout: 10000
parameters:
  - name: target
    type: string
    description: Commit, rama o referencia a comparar (default: HEAD)
    default: HEAD
  - name: path
    type: string
    description: Ruta de archivo específico (opcional)
outputs:
  - name: output
    type: string
    description: Diff de los cambios
---

git diff {target} {path}
