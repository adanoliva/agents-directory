---
name: port-check
description: Comprueba si un puerto está en uso en localhost
model: sonnet
tools: []
---

node -e "const net=require('net');const s=net.createServer();s.once('error',()=>console.log('Puerto {port}: EN USO'));s.once('listening',()=>{s.close();console.log('Puerto {port}: LIBRE')});s.listen({port})"
