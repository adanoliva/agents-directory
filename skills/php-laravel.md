---
name: php-laravel
description: Laravel 11 con Eloquent, Livewire y arquitectura moderna
model: sonnet
tools: []
---

## Laravel 11 Rules (PHP 8.3+)

**Core:**
- **Eloquent ORM**: use relationships, scopes, mutators.
- **Artisan CLI**: use for migrations, seeders, factories, commands.
- Routing: `routes/api.php` or `routes/web.php`.
- Validation: **Form Requests**.
- Auth: **Policies** for granular control.

**Conventions:**
- Reversible migrations (`down()` implementation).
- Models must have factories/seeders.
- Use **Resources/Collections** for API responses.
- Config: use `config()`/`env()` ONLY in config files.
- Heavy tasks: use **Queue jobs**.

**Frontend:** **Livewire 3**, **Inertia.js**, **Vite**.

**Testing:** **Pest** or **PHPUnit**. Use `RefreshDatabase` trait.
