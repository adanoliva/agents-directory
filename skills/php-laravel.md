---
name: php-laravel
description: Laravel 11 con Eloquent, Livewire y arquitectura moderna
model: sonnet
tools: []
---

## Technology context — PHP + Laravel

This project uses **Laravel 11** with PHP 8.3+.

- **Eloquent ORM** for data access — relationships, scopes and mutators
- **Artisan CLI** for migrations, seeders, factories and custom commands
- Routing in `routes/api.php` or `routes/web.php` depending on endpoint type
- Validation with **Form Requests** (`php artisan make:request`)
- **Policies** for granular per-resource authorization

**Conventions:**
- Migrations always reversible with `down()` implemented
- Factories and seeders for all models
- Resources and Collections to transform API responses
- `config()`, `env()` only from config files — no direct `env()` in application code
- Queue jobs for heavy or async tasks

**Frontend:**
- **Livewire 3** for server-side interactive components
- **Inertia.js** for SPA with Vue/React
- **Vite** as bundler (replaces Mix)

**Testing:**
- `pest` or `phpunit` — follow the project convention
- `RefreshDatabase` trait to isolate DB tests
