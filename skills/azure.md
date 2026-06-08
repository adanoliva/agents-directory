---
name: azure
description: Microsoft Azure con servicios core, IAM, redes y buenas prácticas
model: sonnet
tools: []
---

## Azure Rules

**Identity & Access (IAM):**
- Use **Managed Identities** for app-to-service auth — no credentials in code or env vars.
- Apply **RBAC** at resource group or lower scope — avoid subscription-wide roles.
- Use **Entra ID** (AAD) groups, not individual user assignments.
- Rotate secrets stored in **Key Vault**; use references in App Service config.

**Resource Organization:**
- Group by lifecycle: one Resource Group per app/environment combination.
- Tag everything: `environment`, `owner`, `cost-center`, `project`.
- Use **Management Groups** and **Policies** to enforce tagging and allowed regions.

**Networking:**
- Use **VNets** with subnet segmentation (app, data, mgmt).
- Put databases and internal services in private subnets; no public endpoints.
- Use **Private Endpoints** for PaaS services (Storage, SQL, Key Vault).
- Apply **NSGs** on subnets, not individual NICs.

**Compute:**
- Prefer **App Service** or **Container Apps** over VMs for web workloads.
- Use **Azure Container Registry** (ACR) with geo-replication for images.
- Set **auto-scaling** rules based on CPU/memory/queue depth.

**Storage & Data:**
- Enable **soft delete** and **versioning** on Blob Storage.
- Use **Azure SQL Elastic Pools** for multiple small databases.
- Enable **Transparent Data Encryption** (on by default) and audit logs.

**Cost:**
- Use **Reserved Instances** for predictable workloads (1–3 year).
- Set **Budget alerts** at 80% and 100% of monthly limit.
- Enable **Cost Analysis** tags to track per-team spend.
