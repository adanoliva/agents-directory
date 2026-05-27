---
name: file-reader
description: Lee y muestra el contenido de un archivo del proyecto
model: sonnet
tools: []
---

node -e "const fs=require('fs');const p='{path}';if(!fs.existsSync(p)){console.error('No existe: '+p);process.exit(1)};console.log(fs.readFileSync(p,'utf8'))"
