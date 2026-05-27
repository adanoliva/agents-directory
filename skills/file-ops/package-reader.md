---
name: package-reader
description: Lee el archivo package.json del proyecto y muestra nombre, versión, scripts y dependencias
model: sonnet
tools: []
---

node -e "const fs=require('fs');const p='package.json';if(!fs.existsSync(p)){console.error('No existe package.json');process.exit(1)};console.log(fs.readFileSync(p,'utf8'))"
