---
name: ansible
description: Ansible con playbooks, roles, inventarios y buenas prácticas de idempotencia
model: sonnet
tools: []
---

## Ansible Rules

**Structure:**
- Use the **roles** layout: `roles/{role}/tasks/main.yml`, `defaults/`, `handlers/`, `templates/`.
- Organize playbooks by environment (`site.yml`, `webservers.yml`, `databases.yml`).
- Use `group_vars/` and `host_vars/` for variable scoping — never hardcode in playbooks.

**Idempotency:**
- Every task must be idempotent — running it twice produces the same result.
- Use `state: present/absent` in all modules (`apt`, `yum`, `file`, `user`).
- Avoid `command`/`shell` modules when an idempotent module exists.
- If using `command`/`shell`, add `creates:` or `changed_when:` to control idempotency.

**Variables & Secrets:**
- Store secrets in **Ansible Vault** (`ansible-vault encrypt_string`).
- Use `defaults/main.yml` for overridable defaults; `vars/main.yml` for fixed role vars.
- Prefix role variables with the role name to avoid collisions: `nginx_port`, `app_user`.

**Tasks:**
- Always add `name:` to every task — descriptive, in English.
- Use `notify:` + `handlers` for service restarts — don't restart inline.
- Use `become: yes` at the play level, not per task, when the whole play needs root.
- Use `tags:` for selective execution: `--tags deploy`, `--tags config`.

**Testing:**
- Test roles with **Molecule** + Docker driver.
- Run `ansible-lint` in CI to catch style and correctness issues.
