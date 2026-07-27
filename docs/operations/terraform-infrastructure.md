# Terraform Infrastructure

Last updated: 2026-07-27

<details markdown>
<summary>List of references</summary>

- [Repository Terraform infrastructure](https://github.com/Cloud2BR-MSFTLearningHub/Azure-MLOps-Overview/tree/main/terraform-infrastructure)
- [Terraform Azure Provider documentation](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs)

</details>

This repository includes Terraform configuration in
[`terraform-infrastructure`](https://github.com/Cloud2BR-MSFTLearningHub/Azure-MLOps-Overview/tree/main/terraform-infrastructure)
to provision an Azure Machine Learning workspace, compute clusters, and
supporting platform resources.

![Azure Machine Learning platform architecture](https://github.com/user-attachments/assets/8933eb5c-7cc9-4d06-978c-64cb755a48ee){ width="760" }

*Source: [Terraform infrastructure guide](https://github.com/Cloud2BR-MSFTLearningHub/Azure-MLOps-Overview/tree/main/terraform-infrastructure).*

## Before deployment

1. Review `variables.tf` and create environment-specific values outside source
   control.
2. Authenticate with the Azure Command-Line Interface (CLI) using an identity
   with the required permissions.
3. Configure remote state in Azure Blob Storage for collaborative environments.
4. Confirm naming, tags, regions, network requirements, and cost limits.

```sh
cd terraform-infrastructure
az login
terraform init
terraform plan -var-file terraform.tfvars
terraform apply -var-file terraform.tfvars
```

!!! warning
    Do not commit subscription identifiers, secrets, access keys, or production
    `terraform.tfvars` values. Use remote state with suitable access controls
    for team environments.

## Expected repository contents

| File | Purpose |
| --- | --- |
| `main.tf` | Core Azure Machine Learning and supporting resource declarations. |
| `variables.tf` | Input schema for environment configuration. |
| `provider.tf` | Azure provider configuration. |
| `outputs.tf` | Deployment output values. |
| `optional/` | Optional configuration, including remote state examples. |

To remove the demonstration resources when they are no longer required:

```sh
terraform destroy -var-file terraform.tfvars
```
