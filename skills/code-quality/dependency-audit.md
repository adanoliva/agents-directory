---
name: dependency-audit
description: Analiza las dependencias del proyecto en busca de vulnerabilidades conocidas (npm audit)
category: code-quality
version: 1.0.0
type: bash
timeout: 60000
parameters:
  - name: level
    type: string
    description: Nivel mínimo a reportar: low, moderate, high, critical (default: low)
outputs:
  - name: output
    type: string
    description: Reporte de vulnerabilidades
  - name: exitCode
    type: integer
    description: 0 si no hay vulnerabilidades
---

npm audit
