---
name: port-check
description: Comprueba si un puerto está en uso en localhost
category: integration
version: 1.0.0
type: bash
timeout: 5000
parameters:
  - name: port
    type: integer
    required: true
    description: Número de puerto a comprobar
outputs:
  - name: output
    type: string
    description: Estado del puerto (en uso / libre)
---

node -e "const net=require('net');const s=net.createServer();s.once('error',()=>console.log('Puerto {port}: EN USO'));s.once('listening',()=>{s.close();console.log('Puerto {port}: LIBRE')});s.listen({port})"
