---
name: changelog-reader
description: Lee el archivo CHANGELOG.md para consultar el historial de versiones
model: sonnet
tools: []
---

node -e "const fs=require('fs');const p='CHANGELOG.md';if(!fs.existsSync(p)){console.error('No existe CHANGELOG.md');process.exit(1)};console.log(fs.readFileSync(p,'utf8'))"
