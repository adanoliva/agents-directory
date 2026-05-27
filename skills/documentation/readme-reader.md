---
name: readme-reader
description: Lee el archivo README.md del proyecto para obtener contexto de documentación
category: documentation
version: 1.1.0
type: bash
timeout: 5000
parameters: []
outputs:
  - name: output
    type: string
    description: Contenido del README.md
---

node -e "const fs=require('fs');const p='README.md';if(!fs.existsSync(p)){console.error('No existe README.md');process.exit(1)};console.log(fs.readFileSync(p,'utf8'))"
