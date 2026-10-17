# agents-directory

> Colección de agentes y skills de Claude Code organizados por dominio. Es el directorio que sincroniza [Agent Hub](https://github.com/adanoliva/agent-hub).

![Agentes](https://img.shields.io/badge/agentes-23-7c6af7)
![Skills](https://img.shields.io/badge/skills-68-34d399)
![Formato](https://img.shields.io/badge/formato-.md%20frontmatter-blue)
![Compatibilidad](https://img.shields.io/badge/compatible-Claude%20Code-green)

*Construidos con IA. Para la IA. Con manos humanas al volante.*

---

## ¿Qué es esto?

- **Agentes**: ficheros `.md` con frontmatter YAML (nombre, descripción, modelo, herramientas) y un system prompt. Definen *cómo* trabaja el agente.
- **Skills**: bloques de contexto tecnológico (React, PostgreSQL, Docker…) que Agent Hub inyecta en el system prompt según las tecnologías del proyecto. Definen *con qué* trabaja.

Los agentes no mencionan tecnologías concretas: el stack lo aportan las skills. Así un mismo `front-coder` sirve para React, Vue o Svelte.

---

## Estructura

```
agents-directory/
├── global/             # Útiles en cualquier proyecto
├── section-backend/    # Proyectos backend
├── section-data/       # Datos e IA
├── section-devops/     # CI/CD e infraestructura
├── section-frontend/   # Interfaces web
├── section-games/      # Videojuegos
├── section-mobile/     # Apps móviles
└── skills/             # Contexto tecnológico inyectable
```

---

## Catálogo de agentes

### Global

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `api-documenter` | Genera documentación de APIs REST y GraphQL a partir del código | sonnet |
| `code-reviewer` | Revisa código buscando bugs, problemas de seguridad y code smells | sonnet |
| `doc-writer` | Documentación para desarrolladores (READMEs, arquitectura y referencia de código) | sonnet |
| `git-assistant` | Genera commits descriptivos, PRs y changelogs desde el diff actual | haiku |
| `refactor-expert` | Refactoriza código mejorando estructura sin cambiar comportamiento | sonnet |
| `security-auditor` | Audita el código buscando vulnerabilidades de seguridad | sonnet |
| `tech-writer` | Guías de usuario, tutoriales, quickstarts y troubleshooting | sonnet |
| `test-writer` | Genera tests unitarios e integración con buena cobertura | sonnet |

### Backend

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `api-designer` | Diseña y documenta APIs REST y GraphQL coherentes y ergonómicas | sonnet |
| `back-coder` | Implementa endpoints, servicios y lógica de negocio backend | sonnet |
| `db-expert` | Optimiza queries, esquemas y migraciones de bases de datos | sonnet |

### Data / IA

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `data-analyst` | Analiza datos, genera queries SQL y visualizaciones para extraer insights | sonnet |
| `ml-engineer` | Implementa y optimiza pipelines de ML desde datos hasta producción | sonnet |

### DevOps

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `ci-engineer` | Configura pipelines CI/CD y automatización de builds y deploys | sonnet |
| `infra-coder` | Escribe y mantiene infraestructura como código (IaC) | sonnet |

### Frontend

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `accessibility-checker` | Audita y corrige problemas de accesibilidad (WCAG 2.2 AA) | sonnet |
| `css-expert` | Optimiza estilos, layout y responsive design | sonnet |
| `front-coder` | Implementa componentes UI y lógica de presentación | sonnet |
| `performance-optimizer` | Detecta y resuelve cuellos de botella de rendimiento en el frontend | sonnet |

### Juegos

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `game-coder` | Implementa mecánicas, sistemas y lógica de juego | sonnet |
| `game-reviewer` | Revisa arquitectura de juego, patrones y calidad del código | sonnet |

### Móvil

| Agente | Descripción | Modelo |
|--------|-------------|--------|
| `mobile-coder` | Implementa pantallas, navegación y lógica en apps móviles | sonnet |
| `mobile-reviewer` | Revisa UX móvil, permisos, rendimiento y store readiness | sonnet |

---

## Skills

angular · ansible · ant-design · api-rest · astro · auth-jwt · aws · azure · chakra-ui · clean-arch · cypress · defold · docker · dotnet · drizzle · elasticsearch · fastify · flutter · gcp · git-conventional · github-actions · go · godot · graphql · helm · html · java-spring · kafka · kotlin · kubernetes · microservices · mongodb · monorepo · mui · mysql · nestjs · nextjs · nginx · nodejs · nuxtjs · owasp · php-laravel · playwright · postgresql · prisma · prometheus · pytest · python-django · python-fastapi · react-native · react · redis · remix · rust · shadcn · sqlite · supabase · svelte · swift · tailwind · terraform · testing-jest · testing-vitest · typescript · unity · unreal · vanilla · vue

---

## Formato

### Agente

```markdown
---
name: nombre-del-agente
description: Descripción breve del rol del agente
model: sonnet
tools:
  - Read
  - Edit
  - Grep
---

System prompt del agente.
```

**Modelos:** `haiku`, `sonnet`, `opus`.

**Herramientas:** `Bash` `Read` `Write` `Edit` `MultiEdit` `Grep` `WebFetch` `WebSearch` `TodoRead` `TodoWrite`

### Skill

```markdown
---
name: react
description: React con TypeScript, hooks y patrones modernos
---

## Technology context — React
...
```

Las skills solo llevan `name` y `description`; no tienen modelo ni herramientas.

---

## Uso directo con Claude Code

```bash
# Agentes globales para todos tus proyectos
cp global/*.md ~/.claude/agents/

# Agentes de un proyecto concreto (por ejemplo, frontend)
cp global/*.md section-frontend/*.md .claude/agents/
```

```
@code-reviewer revisa AuthService.ts
@test-writer genera tests para el módulo de pagos
```

---

## Contribuir

- `name` en `kebab-case`, igual que el nombre del fichero.
- La `description` describe el rol del agente, en una línea y sin `: ` (rompe el YAML).
- Solo las herramientas que el prompt necesita, y todas las que necesita: si el prompt pide escribir ficheros, el agente necesita `Write`/`Edit`.
- Agentes de código en inglés; agentes de documentación en español. Sin mezclar idiomas en un mismo prompt.
- Nada de tecnologías concretas en los agentes: eso va en las skills.
- Los agentes con `Bash` deben indicar qué no pueden hacer sin petición explícita (push, deploy, apply, migraciones…).

---

## Licencia

MIT © 2025
