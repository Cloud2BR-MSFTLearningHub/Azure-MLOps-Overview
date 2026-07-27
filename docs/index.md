# Azure MLOps Setup and Overview Hub

Last updated: 2026-07-27

<details markdown>
<summary>List of references</summary>

- [Azure Machine Learning documentation](https://learn.microsoft.com/azure/machine-learning/)
- [MLOps maturity model](https://learn.microsoft.com/azure/architecture/ai-ml/guide/mlops-maturity-model)

</details>

Azure Machine Learning Operations (MLOps) combines people, processes, and
technology to deliver machine learning (ML) models reliably, repeatably, and
responsibly. This hub turns the lifecycle into practical setup and operational
guidance for Azure Machine Learning.

!!! warning
    These guides are learning material. Confirm current Azure service behavior,
    support, pricing, and compliance requirements in Microsoft's official
    documentation before production use.

<div class="guide-grid">
  <a class="guide-card" href="overview/"><strong>MLOps overview</strong><br>Lifecycle, maturity levels, platform capabilities, and delivery patterns.</a>
  <a class="guide-card" href="foundation/business-and-responsible-ai/"><strong>Foundation</strong><br>Business outcomes, data assets, experimentation, and responsible AI.</a>
  <a class="guide-card" href="automation/training-pipelines/"><strong>Automation and deployment</strong><br>Training, validation, serving, monitoring, and retraining.</a>
  <a class="guide-card" href="operations/security-governance-and-cost/"><strong>Operations</strong><br>Security, governance, cost controls, and platform operations.</a>
  <a class="guide-card" href="operations/terraform-infrastructure/"><strong>Terraform infrastructure</strong><br>Deploy the repository's Azure Machine Learning foundation.</a>
  <a class="guide-card" href="operations/deployment-checklist/"><strong>Deployment checklist</strong><br>Use a staged checklist before promoting a model to production.</a>
</div>

## Start here

| Need | Start with |
| --- | --- |
| Understand the end-to-end operating model | [MLOps overview](overview.md) |
| Prepare data and develop a reproducible model | [Foundation](foundation/business-and-responsible-ai.md) |
| Automate promotion from training to inference | [Automation and deployment](automation/training-pipelines.md) |
| Deploy the reference platform | [Terraform infrastructure](operations/terraform-infrastructure.md) |