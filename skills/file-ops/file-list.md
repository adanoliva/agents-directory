---
name: file-list
description: Lista los archivos de un directorio con detalles (tamaño, fecha, permisos)
category: file-ops
version: 1.1.0
type: bash
timeout: 5000
parameters:
  - name: path
    type: string
    description: Directorio a listar (default: .)
    default: .
outputs:
  - name: output
    type: string
    description: Listado de archivos
---

node -e "const fs=require('fs');const path=require('path');const dir=('{path}'||'.').trim()||'.';if(!fs.existsSync(dir)){console.error('No existe: '+dir);process.exit(1)};for(const name of fs.readdirSync(dir)){const p=path.join(dir,name);const s=fs.statSync(p);console.log((s.isDirectory()?'d':'f')+' ' + s.size + ' ' + s.mtime.toISOString() + ' ' + name)}"
