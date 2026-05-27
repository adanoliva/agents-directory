---
name: npm-install
description: Instala dependencias de npm. Sin paquete instala todas; con paquete instala uno concreto.
category: execution
version: 1.2.0
type: bash
timeout: 180000
parameters:
  - name: package
    type: string
    description: Paquete a instalar (ej: lodash). Vacío para npm install general.
  - name: dev
    type: boolean
    description: Instalar como devDependency (--save-dev)
outputs:
  - name: output
    type: string
    description: Output de npm
  - name: exitCode
    type: integer
    description: Código de salida
---

npm install {package}
