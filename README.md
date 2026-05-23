# agents-directory

> Colección de agentes de Claude Code organizados por dominio y tecnología.

![Agentes](https://img.shields.io/badge/agentes-24-7c6af7)
![Formato](https://img.shields.io/badge/formato-.md%20frontmatter-blue)
![Compatibilidad](https://img.shields.io/badge/compatible-Claude%20Code-green)

*Construidos con IA. Para la IA. Con manos humanas al volante.*

---

## ¿Qué es esto?

Repositorio independiente de agentes listos para usar con [Claude Code](https://claude.ai/code). Cada agente es un fichero `.md` con frontmatter YAML que define su nombre, descripción, modelo, herramientas y system prompt.

Los agentes están organizados por carpetas según su ámbito de aplicación. Puedes usarlos directamente copiándolos a `~/.claude/agents/` (globales) o a `{proyecto}/.claude/agents/` (por proyecto).

---

## Estructura

```
agents-directory/
├── global/                        # Útiles en cualquier proyecto
│   ├── code-reviewer.md
│   ├── debugger.md
│   ├── doc-writer.md
│   ├── git-helper.md
│   ├── refactor-agent.md
│   └── test-writer.md
│
├── section-docs/                  # Proyectos de documentación
│   ├── diagram-maker.md
│   └── tech-writer.md
│
├── section-games/                 # Proyectos de videojuegos
│   ├── game-designer.md
│   └── performance-optimizer.md
│
├── section-mobile/                # Proyectos móviles
│   └── mobile-ux.md
│
├── section-web/                   # Proyectos web (cualquier stack)
│   ├── accessibility.md
│   ├── api-designer.md
│   └── security-audit.md
│
├── tech-games-godot/              # Godot 4
│   └── godot-dev.md
│
├── tech-games-unity/              # Unity
│   ├── unity-dev.md
│   ├── unity-shader.md
│   └── unity-ui.md
│
├── tech-mobile-pwa/               # Progressive Web Apps
│   └── pwa-dev.md
│
├── tech-mobile-react-native/      # React Native
│   └── rn-dev.md
│
├── tech-web-fullstack/            # Node.js + PostgreSQL
│   └── backend-dev.md
│
├── tech-web-nextjs/               # Next.js
│   └── nextjs-dev.md
│
└── tech-web-react/                # React
    ├── css-designer.md
    └── react-dev.md
```

---

## Catálogo de agentes

### Global

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `code-reviewer` | Revisa código en busca de bugs, problemas de seguridad, rendimiento y claridad | sonnet |
| `debugger` | Depuración sistemática de bugs, errores y comportamientos inesperados | sonnet |
| `doc-writer` | Documentación técnica clara en Markdown | sonnet |
| `git-helper` | Commits, ramas y resolución de conflictos Git | haiku |
| `refactor-agent` | Refactoriza código manteniendo funcionalidad | sonnet |
| `test-writer` | Genera tests unitarios y de integración | sonnet |

### Docs

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `diagram-maker` | Diagramas Mermaid: arquitecturas, flujos y secuencias | sonnet |
| `tech-writer` | Documentación técnica: guías, tutoriales y referencias | sonnet |

### Juegos

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `game-designer` | Diseño de mecánicas, balance numérico y documentación de sistemas de juego | sonnet |
| `performance-optimizer` | Optimiza framerate, memoria y rendimiento en juegos | sonnet |

### Móvil

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `mobile-ux` | UX y patrones de navegación para apps iOS/Android | sonnet |

### Web

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `accessibility` | Accesibilidad WCAG 2.1 AA en interfaces web | sonnet |
| `api-designer` | Diseño de APIs REST y GraphQL | sonnet |
| `security-audit` | Seguridad web: OWASP Top 10, auth y vulnerabilidades | sonnet |

### Godot

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `godot-dev` | Godot 4, GDScript y arquitectura de nodos | sonnet |

### Unity

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `unity-dev` | Unity C#, arquitectura de GameObjects y patrones | sonnet |
| `unity-shader` | Shaders HLSL, Shader Graph y materiales URP/HDRP | sonnet |
| `unity-ui` | UI Toolkit, Canvas y sistemas de menú en Unity | haiku |

### PWA

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `pwa-dev` | Service Workers, caché offline y Lighthouse 90+ | sonnet |

### React Native

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `rn-dev` | React Native + Expo, navegación y animaciones nativas | sonnet |

### Fullstack (Node.js)

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `backend-dev` | Node.js/Express, TypeScript, PostgreSQL y Prisma | sonnet |

### Next.js

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `nextjs-dev` | Next.js 14 App Router, Server Components y optimización | sonnet |

### React

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `css-designer` | TailwindCSS, diseño responsive y sistemas de diseño | haiku |
| `react-dev` | React 18, hooks, rendimiento y patrones de composición | sonnet |

---

## Formato de un agente

```markdown
---
name: nombre-del-agente
description: Descripción breve y precisa de lo que hace
model: claude-sonnet-4-20250514
tools:
  - Read
  - Edit
  - Bash
---

System prompt del agente aquí.
```

**Modelos disponibles:**

| Alias | Model ID |
|-------|----------|
| haiku | `claude-haiku-4-5-20251001` |
| sonnet | `claude-sonnet-4-20250514` |
| opus | `claude-opus-4-20250514` |

**Herramientas disponibles:** `Bash` `Read` `Write` `Edit` `MultiEdit` `Grep` `Glob` `WebFetch` `WebSearch` `TodoRead` `TodoWrite`

---

## Uso directo con Claude Code

### Instalar todos los agentes globales

```bash
# Copia los agentes de la carpeta global a ~/.claude/agents/
cp global/*.md ~/.claude/agents/
```

### Instalar agentes para un proyecto concreto

```bash
# Agentes globales + los de tu stack, por ejemplo Next.js
cp global/*.md .claude/agents/
cp section-web/*.md .claude/agents/
cp tech-web-nextjs/*.md .claude/agents/
```

### Invocar un agente en Claude Code

```
@code-reviewer revisa AuthService.ts
@unity-dev crea un sistema de inventario con ScriptableObjects
@test-writer genera tests para el módulo de pagos
```

---

## Contribuir

Acepto PRs con nuevos agentes o mejoras a los existentes. Criterios:

- El `name` debe ser un identificador en `kebab-case`
- La `description` debe ser concisa y describir el rol del agente, no sus acciones
- Usar solo las herramientas estrictamente necesarias
- El system prompt debe estar en inglés o español, no mezclados
- No incluir el campo `optimized: true` — ese lo gestiona Agent Hub

---

## Licencia

MIT © 2025
