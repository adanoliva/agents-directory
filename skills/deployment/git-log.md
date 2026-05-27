---
name: git-log
description: Muestra el historial de commits recientes del repositorio
category: deployment
version: 1.1.0
type: bash
timeout: 10000
parameters:
  - name: limit
    type: integer
    description: Número de commits a mostrar (default: 10)
    default: 10
  - name: branch
    type: string
    description: Rama a consultar (default: rama actual)
outputs:
  - name: output
    type: string
    description: Historial de commits
---

git log --oneline --graph --decorate --max-count={limit} {branch}
