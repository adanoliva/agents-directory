---
name: changelog-reader
description: Lee el archivo CHANGELOG.md para consultar el historial de versiones
category: documentation
version: 1.1.0
type: bash
timeout: 5000
parameters: []
outputs:
  - name: output
    type: string
    description: Contenido del CHANGELOG.md
---

node -e "const fs=require('fs');const p='CHANGELOG.md';if(!fs.existsSync(p)){console.error('No existe CHANGELOG.md');process.exit(1)};console.log(fs.readFileSync(p,'utf8'))"
