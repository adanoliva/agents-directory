---
name: test-coverage
description: Ejecuta los tests y genera reporte de cobertura de código
model: sonnet
tools: []
---

npx jest --coverage --no-coverage-provider=v8 2>&1 || npx vitest run --coverage 2>&1
