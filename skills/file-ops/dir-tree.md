---
name: dir-tree
description: Muestra la estructura de carpetas del proyecto (primeros 3 niveles, excluye node_modules)
model: sonnet
tools: []
---

find {path} -maxdepth {depth} -not -path "*/node_modules/*" -not -path "*/.git/*" | sort | head -100
