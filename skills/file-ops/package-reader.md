---
name: package-reader
description: Lee el archivo package.json del proyecto y muestra nombre, versión, scripts y dependencias
category: file-ops
version: 1.1.0
type: bash
timeout: 5000
parameters: []
outputs:
  - name: output
    type: string
    description: Contenido del package.json
---

node -e "const fs=require('fs');const p='package.json';if(!fs.existsSync(p)){console.error('No existe package.json');process.exit(1)};console.log(fs.readFileSync(p,'utf8'))"
