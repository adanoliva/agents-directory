---
name: file-head
description: Muestra las primeras N líneas de un archivo (head)
model: sonnet
tools: []
---

node -e "const fs=require('fs');const p='{path}';const n=parseInt('{lines}'||'20',10)||20;if(!fs.existsSync(p)){console.error('No existe: '+p);process.exit(1)};const lines=fs.readFileSync(p,'utf8').split(/\r?\n/).slice(0,n);console.log(lines.join('\n'))"
