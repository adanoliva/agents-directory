---
name: file-head
description: Muestra las primeras N líneas de un archivo (head)
category: file-ops
version: 1.1.0
type: bash
timeout: 5000
parameters:
  - name: path
    type: string
    required: true
    description: Ruta al archivo
  - name: lines
    type: integer
    description: Número de líneas a mostrar (default: 20)
    default: 20
outputs:
  - name: output
    type: string
    description: Primeras N líneas del archivo
---

node -e "const fs=require('fs');const p='{path}';const n=parseInt('{lines}'||'20',10)||20;if(!fs.existsSync(p)){console.error('No existe: '+p);process.exit(1)};const lines=fs.readFileSync(p,'utf8').split(/\r?\n/).slice(0,n);console.log(lines.join('\n'))"
