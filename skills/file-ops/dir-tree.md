---
name: dir-tree
description: Muestra la estructura de carpetas del proyecto (primeros 3 niveles, excluye node_modules)
category: file-ops
version: 1.1.0
type: bash
timeout: 10000
parameters:
  - name: path
    type: string
    description: Directorio raíz (default: .)
    default: .
  - name: depth
    type: integer
    description: Profundidad máxima (default: 3)
    default: 3
outputs:
  - name: output
    type: string
    description: Árbol de directorios
---

node -e "const fs=require('fs');const path=require('path');const root=('{path}'||'.').trim()||'.';const maxDepth=parseInt('{depth}'||'3',10)||3;let count=0;const walk=(d,depth,prefix)=>{if(depth>maxDepth||count>=150)return;let entries=[];try{entries=fs.readdirSync(d,{ withFileTypes: true })}catch{return}entries=entries.filter(e=>e.name!=='node_modules'&&e.name!=='.git').sort((a,b)=>a.name.localeCompare(b.name));for(const e of entries){if(count>=150)break;const line=prefix+e.name+(e.isDirectory()?'/':'');console.log(line);count++;if(e.isDirectory())walk(path.join(d,e.name),depth+1,prefix+'  ')}};console.log(root);walk(root,1,'')"
