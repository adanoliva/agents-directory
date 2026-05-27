---
name: git-branch
description: Lista todas las ramas del repositorio (locales y remotas)
category: deployment
version: 1.0.0
type: bash
timeout: 10000
parameters: []
outputs:
  - name: output
    type: string
    description: Lista de ramas
---

git branch -a
