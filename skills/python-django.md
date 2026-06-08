---
name: python-django
description: Django 5 con DRF, ORM y arquitectura MTV      
model: sonnet
tools: []
---

## Django 5 Rules (Python 3.11+)

**Framework:**
- Use **Django REST Framework (DRF)** for APIs.
- Use **Django ORM**; avoid raw SQL.
- Prevent N+1: use `select_related` (FK) and `prefetch_related` (M2M).
- Split settings: `base.py`, `development.py`, `production.py`.

**Conventions:**
- Modular apps: `models`, `views`, `serializers`, `urls` per app.
- Never edit migrations manually; use `makemigrations`.
- Environment: `django-environ` or `python-decouple`.
- Production: `DEBUG=False` and explicit `ALLOWED_HOSTS`.

**Testing:**
- Use `pytest-django` and `@pytest.mark.django_db`.
- Use DRF `APIClient` and `factory_boy`/`mixer` for fixtures.
