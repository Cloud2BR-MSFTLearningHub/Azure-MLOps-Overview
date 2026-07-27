# MLOps Overview

Last updated: 2026-07-27

<details markdown>
<summary>List of references</summary>

- [Azure Machine Learning documentation](https://learn.microsoft.com/azure/machine-learning/)
- [MLOps maturity model](https://learn.microsoft.com/azure/architecture/ai-ml/guide/mlops-maturity-model)
- [Model management and deployment with Azure Machine Learning](https://learn.microsoft.com/azure/machine-learning/concept-model-management-and-deployment)
- [Responsible AI in Azure Machine Learning](https://learn.microsoft.com/azure/machine-learning/concept-responsible-ai)

</details>

> **Business example:** A retailer forecasts demand for seasonal inventory. MLOps
> makes each forecast reproducible, validates it against prior models, controls
> approval for deployment, and monitors forecast quality as buying patterns
> change.

MLOps applies DevOps practices such as version control, continuous integration
and continuous delivery (CI/CD), automated testing, monitoring, and governance
to the complete machine learning lifecycle. It connects a business problem to a
model in production, then creates the feedback loop required to improve that
model safely.

## Core platform capabilities

| Capability | Azure service or practice |
| --- | --- |
| Data assets and lineage | Azure Machine Learning data assets, Azure Data Lake Storage Gen2, versioned URIs |
| Experimentation | Azure Machine Learning jobs, MLflow tracking, notebooks, and sweep jobs |
| Training | Azure Machine Learning pipelines, components, managed compute clusters, and environments |
| Model registry | Azure Machine Learning model registry with version and metadata controls |
| Inference | Managed online endpoints for real time, batch endpoints for scheduled scoring |
| Monitoring | Azure Monitor, Application Insights, Azure Machine Learning model monitoring |
| Governance | Azure role-based access control (RBAC), Azure Policy, private networking, and Responsible AI artifacts |

## Maturity levels

Microsoft's MLOps maturity model describes an incremental path from manual work
to a controlled, automated operating model.

| Level | Name | Practical outcome |
| --- | --- | --- |
| **0** | No MLOps | Notebook-driven experiments and manual model releases. |
| **1** | DevOps but no MLOps | Application CI/CD exists, but model training and release are manual. |
| **2** | Automated training | Reusable training pipelines and a traceable model registry. |
| **3** | Automated model deployment | Approved model versions can move through controlled deployment stages. |
| **4** | Full MLOps | Monitoring and retraining close the loop with automated controls. |

!!! tip
    Begin with the current maturity level, then make one reliable improvement at
    a time. A tested training pipeline and model registry are a stronger
    foundation than a partially automated end-to-end flow.

## Lifecycle

1. Define the business problem, intended use, success metrics, and risks.
2. Prepare and version data assets.
3. Develop reproducible experiments and select a candidate model.
4. Run scalable, parameterized training pipelines.
5. Evaluate quality, fairness, explainability, and release criteria.
6. Deploy the approved model through a controlled inference pattern.
7. Monitor service health, data drift, prediction behavior, and business impact.
8. Retrain or retire the model based on evidence and approved governance.

Continue with [business problem and responsible AI](foundation/business-and-responsible-ai.md) to begin the lifecycle.