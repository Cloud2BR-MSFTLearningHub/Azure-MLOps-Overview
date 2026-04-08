# Azure MLOps (Machine Learning Operations) - Overview

Costa Rica

[![GitHub](https://img.shields.io/badge/--181717?logo=github&logoColor=ffffff)](https://github.com/) [Cloud2BR OSS - Learning Hub](https://github.com/Cloud2BR-MSFTLearningHub)

Last updated: 2026-04-08

-----------------------------

<details>
<summary><b>List of References</b> (Click to expand)</summary>

- [MLOps model management with Azure Machine Learning](https://learn.microsoft.com/en-us/azure/machine-learning/concept-model-management-and-deployment?view=azureml-api-2)
- [Azure Machine Learning Documentation](https://learn.microsoft.com/en-us/azure/machine-learning/)
- [MLOps Maturity Model](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/mlops-maturity-model)
- [Machine Learning Operations (MLOps) with Azure ML](https://learn.microsoft.com/en-us/azure/machine-learning/concept-model-management-and-deployment)
- [Responsible AI Overview](https://learn.microsoft.com/en-us/azure/machine-learning/concept-responsible-ai)
- [Monitor models in production](https://learn.microsoft.com/en-us/azure/machine-learning/concept-model-monitoring)
- [Azure ML Pipelines](https://learn.microsoft.com/en-us/azure/machine-learning/concept-ml-pipelines)
- [Azure ML Managed Online Endpoints](https://learn.microsoft.com/en-us/azure/machine-learning/concept-endpoints-online)
- [GitHub Actions for Azure ML](https://learn.microsoft.com/en-us/azure/machine-learning/how-to-github-actions-machine-learning)

</details>

<details>
<summary><b>Table of Contents</b> (Click to expand)</summary>

- [What is MLOps?](#what-is-mlops)
- [MLOps Maturity Levels](#mlops-maturity-levels)
- [Phase 1: Problem Definition & Business Understanding](#phase-1--problem-definition--business-understanding)
- [Phase 2: Data Management & Preparation](#phase-2--data-management--preparation)
- [Phase 3: Model Development & Experimentation](#phase-3--model-development--experimentation)
- [Phase 4: Model Training at Scale](#phase-4--model-training-at-scale)
- [Phase 5: Model Evaluation & Validation](#phase-5--model-evaluation--validation)
- [Phase 6: Model Deployment & Serving](#phase-6--model-deployment--serving)
- [Phase 7: Monitoring & Observability](#phase-7--monitoring--observability)
- [Phase 8: Retraining & Continuous Improvement](#phase-8--retraining--continuous-improvement)
- [Cross-Cutting Concerns](#cross-cutting-concerns)
- [Infrastructure as Code](#infrastructure-as-code)

</details>


## What is MLOps?

> MLOps (Machine Learning Operations) is a set of practices that combines **Machine Learning**, **DevOps**, and **Data Engineering** to reliably and efficiently deploy and maintain ML models in production. It is the discipline of applying DevOps principles (automation, CI/CD, versioning, monitoring, etc) to the full ML lifecycle.

> [!NOTE]
> Microsoft defines MLOps as the union of people, process, and technology to productionize ML models reliably and at scale. The goal is to shorten the cycle from idea to production while maintaining quality, reproducibility, and governance.

The core pillars of MLOps on Azure are:

| Pillar | Azure Service / Concept |
|---|---|
| Data management | Azure Data Lake, Azure ML Datasets, Data versioning |
| Experimentation | Azure ML Studio, MLflow tracking |
| Training at scale | Azure ML Compute Clusters, Pipelines |
| Model registry | Azure ML Model Registry |
| Deployment | Managed Online / Batch Endpoints |
| Monitoring | Azure Monitor, Application Insights, Data drift detection |
| CI/CD | GitHub Actions, Azure DevOps Pipelines |
| Governance | Azure Policy, Responsible AI dashboard, RBAC |

## MLOps Maturity Levels

> Microsoft defines an [MLOps Maturity Model](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/mlops-maturity-model) with five levels ranging from manual, ad-hoc processes to fully automated self-healing systems.

| Level | Name | Description |
|---|---|---|
| **0** | No MLOps | Manual, notebook-driven. No reproducibility. |
| **1** | DevOps but no MLOps | Basic CI/CD for application code only. ML is still manual. |
| **2** | Automated training | Training pipelines automated. Models tracked in a registry. |
| **3** | Automated model deployment | Deployment pipelines trigger on approved model versions. |
| **4** | Full MLOps | End-to-end automation including retraining, monitoring, and drift-triggered pipelines. |

> [!TIP]
> Start by assessing your current maturity level honestly. Most organizations land at Level 0 or 1. Focus on progressing one level at a time rather than trying to implement everything at once.

## Phase 1: Problem Definition & Business Understanding

> Before writing a single line of code, align on what success looks like. This phase is often underestimated but is the single biggest determinant of whether an ML project delivers value.

| Key Activity | Description |
|---|---|
| **Define the business objective** | What decision or process will this model support? What KPI will it improve? |
| **Identify the ML task** | Classification, regression, forecasting, NLP, computer vision, etc. |
| **Define success metrics** | Agree on both ML metrics (accuracy, AUC, RMSE) and business metrics (revenue impact, cost reduction, time saved). |
| **Assess feasibility** | Do you have enough data? Is the problem learnable? What is the cost of a wrong prediction? |
| **Map stakeholders** | Data owners, model consumers, compliance/legal, and platform team. |

> [!IMPORTANT]
> Skipping this phase leads to technically correct models that solve the wrong problem. Microsoft's Responsible AI framework requires that the intended use, limitations, and potential harms of a model be documented from the start.

| Best Practice | Consideration |
|---|---|
| **Project structure** | Use the [Team Data Science Process (TDSP)](https://learn.microsoft.com/en-us/azure/architecture/data-science-process/overview) as a lightweight template to organize work across teams. |
| **Responsible AI documentation** | Establish a **Model Card** or **AI Use Case Description** early — this feeds directly into Responsible AI documentation later. |
| **Service Level Agreements** | Define **SLAs** for model latency, availability, and retraining frequency before any architecture decisions are made. |

## Phase 2: Data Management & Preparation

> Data is the foundation of every ML system. Azure provides a rich ecosystem for storing, versioning, and transforming data at scale.

| Key Activity | Description |
|---|---|
| **Data ingestion** | Pull data from source systems (databases, APIs, streaming sources) into a central store. |
| **Data exploration (EDA)** | Profile the data for missing values, outliers, distribution shifts, and class imbalance. |
| **Feature engineering** | Transform raw signals into features meaningful to the model. |
| **Data versioning** | Track exactly which version of the dataset was used to train each model version. |
| **Data splitting** | Define train / validation / test splits with care to avoid leakage. |

> [!CAUTION]
> Data leakage between train and test sets is one of the most common and damaging mistakes in ML. Ensure temporal splits for time-series data and that feature computation only uses information available at prediction time.

| Need | Azure Services & Tools Offering |
|---|---|
| Scalable storage | Azure Data Lake Storage Gen2 |
| Structured datasets | Azure ML Datasets (File & Tabular) |
| Data transformation | Azure Data Factory, Azure Databricks |
| Data versioning | Azure ML Data Assets with versioned URIs |
| Labeling | Azure ML Data Labeling (supports ML-assisted labeling) |

| Best Practice | Consideration |
|---|---|
| **Dataset versioning** | Register all datasets as **Azure ML Data Assets** so every training run references a versioned, traceable data snapshot. |
| **Data validation** | Apply data validation checks (schema, row counts, value ranges) as the first step of every pipeline run. Fail fast on bad data. |
| **Secure storage** | Store sensitive data in **Azure Data Lake Storage Gen2** with hierarchical namespace enabled, access controlled via Azure RBAC and ACLs — never embed credentials in code. |
| **Data protection** | Enable **soft delete** and **versioning** on Azure Blob/ADLS to protect against accidental deletion. |

## Phase 3: Model Development & Experimentation

> This phase is the most iterative. The goal is to rapidly explore hypotheses, track experiments, and identify the best modeling approach.

| Key Activity | Description |
|---|---|
| **Baseline model** | Always start with a simple baseline (e.g., majority class classifier, mean predictor) to set a performance floor. |
| **Feature selection & engineering** | Iterate on which features move the needle. |
| **Algorithm selection** | Try multiple algorithms; avoid premature commitment to a complex model. |
| **Hyperparameter tuning** | Systematic search over the parameter space. |
| **Experiment tracking** | Log every run — parameters, metrics, artifacts, and environment. |

| Need | Azure Offering Services & Tools|
|---|---|
| Interactive development | Azure ML Studio Notebooks, VS Code with Azure ML extension |
| Experiment tracking | Azure ML Jobs + MLflow autologging |
| Hyperparameter tuning | Azure ML Sweep Jobs (supports grid, random, Bayesian) |
| AutoML | Azure AutoML (tabular, NLP, computer vision) |
| Version control | Git + Azure Repos / GitHub |

> [!TIP]
> Azure ML's **sweep jobs** natively support early termination policies (Bandit, Median Stopping, Truncation Selection). Always configure early termination on hyperparameter sweeps to avoid wasting compute on poor configurations.

| Best Practice | Consideration |
|---|---|
| **Experiment tracking** | Use MLflow autologging from day one. Retrofitting experiment tracking onto an existing codebase is painful. |
| **Reproducibility** | Pin library versions (`requirements.txt` or `conda.yaml`), seed all random number generators, and use fixed data asset versions for every experiment. |
| **Code separation** | Separate **research code** (notebooks) from **production code** (Python modules). Notebooks are great for exploration but not for pipelines. |
| **Environment management** | Register **compute environments** as Azure ML Environments so the same Docker image is used in local dev, CI, and production training. |

## Phase 4: Model Training at Scale

> Once you have a promising approach, move from interactive notebooks to **automated, parameterized training pipelines** that can run reliably on cloud compute.

| Key Activity | Description |
|---|---|
| **Refactor training code** | Move from notebooks into reusable Python modules/scripts ready for pipeline execution. |
| **Define an Azure ML Pipeline** | Structure the workflow into discrete, versioned steps: data prep → feature engineering → training → evaluation. |
| **Parameterize everything** | Externalize data version, hyperparameters, and compute target — nothing hardcoded in scripts. |
| **Compute selection** | Choose the right cluster type for the workload: CPU for classical ML, GPU for deep learning. |
| **Distributed training** | For large models or datasets, configure multi-node training with frameworks like PyTorch DDP or Horovod. |

> [!NOTE]
> Azure ML Pipelines cache step outputs by default. If the input data and parameters for a step haven't changed, the cached output is reused. This dramatically speeds up iterative pipeline development.

| Need | Azure Services & Tools Offering |
|---|---|
| Orchestration | Azure ML Pipelines (component-based) |
| Compute | Azure ML Compute Clusters (auto-scaling) |
| Container images | Azure ML Curated Environments / Custom Environments |
| Distributed training | Azure ML + PyTorch / TensorFlow distributed |
| Scheduling | Azure ML Schedules, Azure Data Factory triggers |

| Best Practice | Consideration |
|---|---|
| **Reusable components** | Define each pipeline step as an **Azure ML Component** with a typed interface (inputs, outputs, parameters) shareable via a component registry. |
| **Scale-to-zero compute** | Configure compute clusters with a minimum node count of 0 so they scale to zero when idle and you're not paying for unused resources. |
| **Cost optimization** | Use **spot/low-priority VMs** for non-time-sensitive runs (typically 60–80% cheaper), with checkpointing to handle pre-emption. |
| **Named outputs** | Store all training outputs (model artifacts, metrics, logs) as named outputs in the pipeline for automatic tracking and lineage. |
| **Pinned environments** | Pin the **Azure ML Environment** (Docker image + conda/pip dependencies) so training is fully reproducible months later. |

## Phase 5: Model Evaluation & Validation

> A model that performs well on a held-out test set is not automatically ready for production. Validation must go beyond aggregate metrics.

| Key Activity | Description |
|---|---|
| **Metric evaluation** | Compare against baseline and previous production model version on the same test dataset. |
| **Slice-based evaluation** | Measure performance across important data subgroups: demographics, geographies, time periods. |
| **Fairness assessment** | Identify disparate impact across protected groups using statistical parity and equalized odds metrics. |
| **Explainability** | Understand which features drive predictions globally (SHAP summary) and locally (per-prediction explanations). |
| **Stress testing** | Evaluate behavior on edge cases, adversarial inputs, and out-of-distribution samples. |
| **Model registration gate** | Only register a model in the registry if it passes all defined quality and fairness thresholds. |

> [!IMPORTANT]
> Under Microsoft's Responsible AI framework, fairness and explainability are not optional for high-stakes decisions (e.g., credit scoring, hiring, healthcare). Document the RAI assessment as part of the model's release artifacts.

| Need | Azure Services & Tools Offering |
|---|---|
| Responsible AI analysis | Azure ML Responsible AI Dashboard |
| Fairness assessment | Fairlearn (integrated into Azure ML RAI Dashboard) |
| Explainability | SHAP / InterpretML (integrated into Azure ML RAI Dashboard) |
| Counterfactual analysis | DiCE (integrated into Azure ML RAI Dashboard) |
| Error analysis | ErrorAnalysis (integrated into Azure ML RAI Dashboard) |
| Model registry | Azure ML Model Registry |

| Best Practice | Consideration |
|---|---|
| **Responsible AI Dashboard** | Use the Azure ML RAI Dashboard for a unified view of fairness, explainability, error analysis, and causal analysis before registering a model. |
| **Promotion criteria as code** | Define a Python evaluation script that exits non-zero if thresholds are not met, enabling automated gating in CI/CD pipelines. |
| **Champion comparison** | Always compare the new model against the **currently deployed champion** on the same test dataset, not just an absolute threshold. |
| **Model tagging & lineage** | Tag every registered model with training data version, pipeline run ID, Git commit SHA, and key metrics to ensure full traceability. |

## Phase 6: Model Deployment & Serving

> Getting a validated model to production in a reliable, secure, and observable way.

| Deployment Pattern | Azure Offering | Use Case |
|---|---|---|
| Real-time inference | Managed Online Endpoints (MIR) | Low-latency, synchronous predictions |
| Batch inference | Batch Endpoints | Large-scale, scheduled scoring |
| Edge / IoT | Azure IoT Edge + ONNX Runtime | Offline / constrained environments |
| Embedded in app | Direct SDK / REST API | Custom integration scenarios |

| Key Activity | Description |
|---|---|
| **Package the model** | Create a scoring script (`score.py`) and register the serving environment in Azure ML. |
| **Deploy to staging** | Validate the endpoint behavior against integration tests before routing any production traffic. |
| **Blue/green or canary deployment** | Gradually shift traffic to the new model version (e.g., 10% → 50% → 100%) to minimize blast radius. |
| **Rollback plan** | Document and test the rollback procedure before going live — know the exact steps to revert traffic to the previous deployment. |

> [!TIP]
> For batch workloads, **Batch Endpoints** are significantly more cost-efficient than keeping an online endpoint scaled up. They spin compute up on demand and scale to zero after the job completes.

| Best Practice | Consideration |
|---|---|
| **Managed Online Endpoints** | Use Managed Online Endpoints for real-time serving — Microsoft handles provisioning, autoscaling, certificates, and blue/green traffic splitting natively. |
| **Traffic splitting** | Configure canary deployments at the endpoint level (e.g., 10% new / 90% current) before committing to full promotion. |
| **Autoscaling** | Scale based on request queue depth and CPU/GPU utilization. Set appropriate min/max instance counts to balance cost and availability. |
| **Authentication** | Protect all endpoints with **Azure AD authentication** — never expose unauthenticated endpoints in production. |
| **Smoke & integration tests** | Run automated tests against the staging deployment in the CD pipeline before promoting to production. |
| **Registry-based deployments** | Reference model artifacts from the **Azure ML Model Registry** by name and version — never copy files manually. |

## Phase 7: Monitoring & Observability

> A deployed model is not "done." Its performance degrades over time as the real world changes. Monitoring is what keeps production models healthy.

| What to Monitor? (Signal) | Description | Azure Service |
|---|---|---|
| **Operational metrics** | Latency, throughput, error rate, availability | Azure Monitor, Application Insights |
| **Data drift** | Input feature distributions shift from training baseline | Azure ML Data Drift Monitor |
| **Prediction drift** | Output score/label distributions change over time | Azure ML Model Monitor |
| **Model performance** | Accuracy degrades when ground truth labels are available | Azure ML Model Monitor |
| **Infrastructure** | CPU/GPU/memory utilization, pod health | Azure Monitor, Container Insights |

> [!NOTE]
> Data drift does not always mean model performance has degraded, but it is a leading indicator. Configure your monitoring to alert on drift and trigger a human review or automated retraining workflow accordingly.

| Best Practice | Consideration |
|---|---|
| **Model Monitors** | Create Azure ML Model Monitors for every production model, scheduled daily or weekly, with alerts when drift exceeds thresholds. |
| **Application Insights instrumentation** | Instrument the scoring script to log prediction inputs, outputs, and latency for every inference request (subject to data privacy requirements). |
| **Operational alerts** | Set up Azure Monitor Alerts for P99 latency spikes, error rate increases, and endpoint availability drops. |
| **Baseline dataset** | Store a baseline dataset (training data or representative sample) at deployment time — Azure ML uses this as the reference distribution for drift calculations. |
| **Ground truth collection** | Collect and store ground truth labels wherever possible to compute actual model performance metrics in production. |

## Phase 8: Retraining & Continuous Improvement

> Models must evolve with the data. The goal of this phase is a closed-loop system where monitoring signals feed back into the training pipeline automatically or with minimal human intervention.

| Retraining Trigger Type | Description |
|---|---|
| **Scheduled** | Retrain on a fixed cadence (e.g., weekly, monthly) regardless of detected drift |
| **Drift-based** | Monitoring detects data or prediction drift above a threshold; triggers retraining pipeline |
| **Performance-based** | Model accuracy drops below an acceptable threshold (requires ground truth) |
| **Event-based** | A significant upstream event (data schema change, product update) triggers retraining |

> [!TIP]
> Start with scheduled retraining before investing in drift-triggered automation. A reliable weekly retrain often provides 80% of the value of a fully automated system with 20% of the complexity.

| Key Activity | Description |
|---|---|
| **Automated retraining pipeline** | The same parameterized training pipeline from Phase 4 should be fully triggerable via an event or schedule without manual intervention. |
| **Automated evaluation gate** | The retrained model must pass all evaluation thresholds from Phase 5 before being registered — fail the pipeline otherwise. |
| **Automated deployment** | A passing model version automatically updates the production endpoint with a canary rollout. |
| **Human-in-the-loop** | For high-stakes models, include a mandatory human approval step in the CD pipeline before promoting to production. |

| Best Practice | Consideration |
|---|---|
| **Event-driven triggers** | Wire Azure ML Model Monitor alerts to **Azure Event Grid**, which can trigger a Logic App or GitHub Actions workflow to kick off a retraining pipeline run. |
| **CI/CD orchestration** | Use GitHub Actions or Azure DevOps for orchestration. Keep the ML pipeline YAML definition in source control alongside the training code. |
| **Champion/challenger framework** | The current production model is always the champion; every retrained candidate is a challenger evaluated head-to-head before promotion. |
| **Model versioning discipline** | Never overwrite a production model artifact. Always register as a new version in the Azure ML Model Registry with full lineage metadata. |

## Cross-Cutting Concerns

> These concerns apply across all phases and should be addressed from the start of the project.

| Security & Access Control Practice | Consideration |
|---|---|
| **Least-privilege RBAC** | Apply minimal permissions at every layer: Azure ML Workspace, Storage Account, Key Vault, and compute. |
| **Secret management** | Store all secrets in **Azure Key Vault** — never in code, baked-in environment variables, or `terraform.tfvars` committed to source control. |
| **Managed Identity** | Use System-Assigned or User-Assigned Managed Identity for all Azure ML resources to eliminate credential management entirely. |
| **Private endpoints** | Enable private endpoints for the Azure ML Workspace, Storage, Key Vault, and Container Registry in production to eliminate public internet exposure. |

| Governance & Compliance Practice | Consideration |
|---|---|
| **Azure Policy** | Assign policies to enforce organizational standards: allowed regions, required tags, mandatory encryption settings across all Azure ML resources. |
| **Resource tagging** | Attach required tags (`environment`, `project`, `owner`, `cost-center`) to all resources to enable cost allocation and governance reporting. |
| **Responsible AI artifacts** | Use the Azure ML Responsible AI Dashboard to generate an RAI assessment artifact for every model version promoted to production. |
| **Audit trail** | Maintain a record of all model registrations, deployments, and endpoint configuration changes via Azure Activity Log. |

| Cost Management Practice | Consideration |
|---|---|
| **Budget alerts** | Configure budget alerts in Azure Cost Management for the ML resource group to catch unexpected spend early. |
| **Scale-to-zero training** | Use compute clusters that scale to zero nodes when idle — never leave clusters running between jobs. |
| **Dev instance shutdown** | Schedule automatic shutdown for compute instances used for development (e.g., nightly shutdown policy). |
| **Workspace hygiene** | Regularly review and delete unused model versions, stale datasets, and old pipeline run logs that accumulate over time. |
| **Reserved Instances** | Use Reserved Instances for stable, predictable production endpoint compute to reduce costs by up to 40%. |

> CI/CD Pipeline Structure: A typical MLOps CI/CD pipeline on Azure looks like.

```
PR / Push to main
    │
    ├── [CI] Lint & unit tests (pytest, flake8)
    ├── [CI] Integration test: run pipeline on sample data
    ├── [CI] Evaluate model — fail if below threshold
    │
    └── [CD] Deploy to staging endpoint
            ├── Smoke tests against staging
            └── [Manual approval gate] ──► Deploy to production endpoint
                                              └── Canary rollout (10% → 100%)
```

> [!NOTE]
> Use **GitHub Actions** (preferred for open source / GitHub-native projects) or **Azure DevOps Pipelines** for CI/CD. Both have first-class Azure ML integration via the `azure/ml` GitHub Actions or `AzureML` DevOps tasks.

## Infrastructure as Code

> All Azure ML infrastructure in this repository is provisioned via **Terraform**. See the [terraform-infrastructure/README.md](terraform-infrastructure/README.md) for full deployment instructions. 

| Best Practice | Consideration |
|---|---|
| **Remote state** | Configure the Terraform backend to store state in Azure Blob Storage (see `optional/remote-storage.tf`), never use local state in team environments. |
| **Externalized variables** | All environment-specific values are in `terraform.tfvars`, do not commit files with real subscription IDs or secrets to source control. |
| **Managed Identity** | The ML workspace uses a system-assigned identity, removing the need to manage service principal credentials. |
| **Naming & tagging** | Apply a consistent naming convention and tag all resources with environment, project, and owner tags to support governance and cost management. |

<!-- START BADGE -->
<div align="center">
  <img src="https://img.shields.io/badge/Total%20views-1287-limegreen" alt="Total views">
  <p>Refresh Date: 2026-04-08</p>
</div>
<!-- END BADGE -->
