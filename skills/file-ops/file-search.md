---
name: file-search
description: Busca texto o patrón regex en los archivos del proyecto (grep recursivo)
model: sonnet
tools: []
---

grep -rn --include="*.{ext}" "{pattern}" {path}
