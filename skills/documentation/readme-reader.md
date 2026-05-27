---
name: readme-reader
description: Lee el archivo README.md del proyecto para obtener contexto de documentación
model: sonnet
tools: []
---

node -e "const fs=require('fs');const p='README.md';if(!fs.existsSync(p)){console.error('No existe README.md');process.exit(1)};console.log(fs.readFileSync(p,'utf8'))"
