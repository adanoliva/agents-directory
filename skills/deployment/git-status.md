---
name: git-status
description: Muestra el estado actual del repositorio git (cambios staged, unstaged, untracked)
category: deployment
version: 1.1.0
type: bash
timeout: 10000
parameters: []
outputs:
  - name: output
    type: string
    description: Estado del repositorio
---

git status
