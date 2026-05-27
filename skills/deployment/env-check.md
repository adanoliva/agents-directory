---
name: env-check
description: Verifica que las variables de entorno requeridas estén definidas en el sistema
model: sonnet
tools: []
---

node -e "const vars='{vars}'.split(',');vars.forEach(v=>{const val=process.env[v.trim()];console.log(v.trim()+ ':' + (val ? '✓ definida' : '✗ no definida'))})"
