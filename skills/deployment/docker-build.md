---
name: docker-build
description: Construye una imagen Docker a partir del Dockerfile del proyecto. Requiere Docker instalado.
category: deployment
version: 1.1.0
type: bash
timeout: 600000
requires: docker
parameters:
  - name: tag
    type: string
    required: true
    description: Nombre e tag de la imagen (ej: miapp:latest)
  - name: context
    type: string
    description: Directorio de contexto (default: .)
  - name: file
    type: string
    description: Ruta al Dockerfile (default: Dockerfile)
outputs:
  - name: output
    type: string
    description: Output del build de Docker
  - name: exitCode
    type: integer
    description: 0 si la imagen se construyó con éxito
---

docker build -t {tag} {context}
