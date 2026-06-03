---
name: python-django
description: Django 5 con DRF, ORM y arquitectura MTV
model: sonnet
tools: []
---

## Technology context — Python + Django

This project uses **Django 5** with Python 3.11+.

- **Django REST Framework (DRF)** for APIs: ViewSets, Serializers, Permissions
- Django ORM for data access — avoid raw SQL except for performance cases
- `select_related` and `prefetch_related` to prevent N+1 queries
- Class-based or function-based views — follow the project convention
- `settings/` split by environment: `base.py`, `development.py`, `production.py`

**Conventions:**
- Modular apps by domain: each app has its own `models`, `views`, `serializers`, `urls`
- Migrations always created with `makemigrations` — never edit manually
- `django-environ` or `python-decouple` for environment variables
- `DEBUG=False` in production, explicit `ALLOWED_HOSTS`

**Testing:**
- `pytest-django` with `@pytest.mark.django_db` for database tests
- DRF's `APIClient` for endpoint tests
- `mixer` or `factory_boy` for test fixtures
