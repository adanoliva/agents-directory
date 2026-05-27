---
name: file-reader
description: Lee y muestra el contenido de un archivo del proyecto
category: file-ops
version: 1.1.0
type: bash
timeout: 5000
parameters:
  - name: path
    type: string
    required: true
    description: Ruta relativa al archivo a leer
outputs:
  - name: output
    type: string
    description: Contenido del archivo
---

cat {path}
