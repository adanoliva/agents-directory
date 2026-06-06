---
name: terraform
description: Terraform con módulos, remote state y buenas prácticas de IaC
model: sonnet
tools: []
---

## Terraform

- **Structure**: `main.tf` (resources), `variables.tf` (typed/validated), `outputs.tf` (outputs), `versions.tf` (versions).
- **Modules**: One per logical resource. Required inputs (no default), optional inputs (sensible defaults). Documented outputs.
- **Remote State**: Use S3+DynamoDB or GCS+Firestore. No local state in repos. Prefer directories over workspaces for environments.
- **Operations**:
  - Always `terraform plan` before `apply`.
  - Use `terraform fmt`, `validate`, and `tflint`.
  - Apply `prevent_destroy = true` on critical resources.
- **Secrets**: Mark sensitive outputs with `sensitive = true`. Never store in `.tfvars`. Use Vault or Cloud Secret Managers.
