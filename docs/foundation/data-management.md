# Data Management

Last updated: 2026-07-27

<details markdown>
<summary>List of references</summary>

- [Azure Machine Learning data assets](https://learn.microsoft.com/azure/machine-learning/how-to-create-data-assets)

</details>

Reliable models require traceable, secure, and representative data. Register the
data used by every training run as a versioned Azure Machine Learning data asset
so the model can be reproduced and audited.

## Data foundation

| Need | Azure service or practice |
| --- | --- |
| Scalable storage | Azure Data Lake Storage Gen2 with managed access controls. |
| Transformation | Azure Data Factory, Azure Databricks, or pipeline components. |
| Dataset versioning | Azure Machine Learning data assets with immutable versions. |
| Labeling | Azure Machine Learning data labeling when managed labeling is appropriate. |
| Quality checks | Schema, row count, range, null, and distribution checks at pipeline entry. |

!!! caution
    Prevent data leakage. Features available only after the prediction point,
    future records, or information from the test set must not influence model
    training. Use temporal splits when the production problem has a time axis.

## Recommended flow

1. Ingest source data into a governed storage zone.
2. Profile quality, representativeness, missing values, and outliers.
3. Apply transformation and feature engineering with versioned code.
4. Register the approved input as a data asset.
5. Create train, validation, and test splits that match the production scenario.
6. Record lineage from data asset version to training run and model version.

| Control | Implementation detail |
| --- | --- |
| Access | Use Azure role-based access control (RBAC), access control lists, and managed identities. |
| Secrets | Store credentials in Azure Key Vault. Do not include them in code or data paths. |
| Protection | Enable soft delete and versioning where supported; define retention requirements. |
| Data contracts | Fail the pipeline when input schema or quality thresholds are violated. |
