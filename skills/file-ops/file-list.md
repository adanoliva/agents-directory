---
name: file-list
description: Lista los archivos de un directorio con detalles (tamaño, fecha, permisos)
model: sonnet
tools: []
---

node -e "const fs=require('fs');const path=require('path');const dir=('{path}'||'.').trim()||'.';if(!fs.existsSync(dir)){console.error('No existe: '+dir);process.exit(1)};for(const name of fs.readdirSync(dir)){const p=path.join(dir,name);const s=fs.statSync(p);console.log((s.isDirectory()?'d':'f')+' ' + s.size + ' ' + s.mtime.toISOString() + ' ' + name)}"
