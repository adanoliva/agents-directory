---
name: terraform
description: Terraform con módulos, remote state y buenas prácticas de IaC
model: sonnet
tools: []
---

## Technology context — Terraform

This project uses **Terraform** (or **OpenTofu** as open-source alternative).

**Structure:**
- `main.tf`: main resources
- `variables.tf`: variables with type, description and validations
- `outputs.tf`: module outputs
- `versions.tf`: version constraints for Terraform and providers
- `terraform.tfvars`: values (don't commit if it contains secrets)

**Modules:**
- One module per logical resource: VPC module, RDS module, etc.
- Required inputs without defaults; optional inputs with sensible defaults
- Documented outputs for other modules to consume

**Remote state:**
- `terraform.tfstate` in S3 + DynamoDB locking (AWS) or GCS + Cloud Firestore (GCP)
- Never `terraform.tfstate` locally in shared repositories
- Workspaces or separate directories per environment (prefer directories)

**Best practices:**
- `terraform plan` before `terraform apply` — always review the diff
- `terraform fmt` and `terraform validate` in CI
- `tflint` for best-practice linting
- Destroy protections on critical resources: `prevent_destroy = true`

**Secrets:**
- Never in `.tfvars` or in state if avoidable
- `sensitive = true` to mark sensitive outputs
- Integrations: Vault provider, AWS Secrets Manager data source
