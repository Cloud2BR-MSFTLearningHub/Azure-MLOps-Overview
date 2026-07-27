# Security, Governance, and Cost

Last updated: 2026-07-27

Security, governance, and cost controls must apply across the lifecycle rather
than being added only to production deployment.

## Security controls

| Area | Recommended control |
| --- | --- |
| Access | Apply least-privilege Azure role-based access control (RBAC) at workspace, data, compute, and secret boundaries. |
| Identities | Use system-assigned or user-assigned managed identities wherever possible. |
| Secrets | Keep secrets in Azure Key Vault and rotate them under an approved policy. |
| Network | Use private endpoints for Azure Machine Learning, storage, Key Vault, and container registries in production. |
| Audit | Retain Azure Activity Log and deployment records for model registration and endpoint changes. |

## Governance controls

- Enforce required regions, tags, and encryption settings with Azure Policy.
- Tag resources with environment, project, owner, and cost-center values.
- Keep model cards, Responsible AI assessments, approvals, and deployment
  evidence alongside each release.
- Define retention rules for data, model versions, endpoint logs, and pipeline
  artifacts.

## Cost controls

| Control | Outcome |
| --- | --- |
| Budgets and alerts | Detect unexpected ML spend early. |
| Scale-to-zero training | Avoid charges for idle compute clusters. |
| Automatic development shutdown | Stops non-production compute outside working windows. |
| Platform hygiene | Removes stale data, model versions, and pipeline artifacts according to policy. |
| Reserved capacity review | Evaluates long-running production inference workloads for savings. |