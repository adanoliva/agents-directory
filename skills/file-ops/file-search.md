---
name: file-search
description: Busca texto o patrón regex en los archivos del proyecto (grep recursivo)
model: sonnet
tools: []
---

node -e "const fs=require('fs');const path=require('path');const root=('{path}'||'.').trim()||'.';const pattern='{pattern}';const ext=('{ext}'||'').trim();let re;try{re=new RegExp(pattern,'i')}catch(e){console.error('Regex invalida: '+pattern);process.exit(1)};const walk=(d)=>{for(const e of fs.readdirSync(d,{ withFileTypes: true })){if(e.name==='node_modules'||e.name==='.git')continue;const p=path.join(d,e.name);if(e.isDirectory()){walk(p);continue}if(ext && !e.name.endsWith('.'+ext))continue;let txt='';try{txt=fs.readFileSync(p,'utf8')}catch(err){continue}const rows=txt.split(/\r?\n/);for(let i=0;i<rows.length;i++){if(re.test(rows[i]))console.log(p+':'+(i+1)+':'+rows[i]);}}};walk(root)"
