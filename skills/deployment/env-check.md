---
name: env-check
description: Verifica que las variables de entorno requeridas estén definidas en el sistema
category: deployment
version: 1.0.0
type: bash
timeout: 5000
parameters:
  - name: vars
    type: string
    required: true
    description: Variables a comprobar separadas por coma (ej: DATABASE_URL,API_KEY)
outputs:
  - name: output
    type: string
    description: Estado de cada variable (definida / no definida)
---

node -e "const vars='{vars}'.split(',');vars.forEach(v=>{const val=process.env[v.trim()];console.log(v.trim()+ ':' + (val ? '✓ definida' : '✗ no definida'))})"
