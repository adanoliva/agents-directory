---
name: file-reader
description: Lee y muestra el contenido de un archivo del proyecto
category: file-ops
version: 1.2.0
type: bash
timeout: 5000
parameters:
  - name: path
    type: string
    required: true
    description: Ruta relativa al archivo a leer
outputs:
  - name: output
    type: string
    description: Contenido del archivo
---

node -e "const fs=require('fs');const p='{path}';if(!fs.existsSync(p)){console.error('No existe: '+p);process.exit(1)};console.log(fs.readFileSync(p,'utf8'))"
