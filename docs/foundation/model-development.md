# Model Development and Experimentation

Last updated: 2026-07-27

Development should optimize learning speed without sacrificing reproducibility.
Use notebooks for exploration, then move validated logic into version-controlled
Python modules and pipeline components.

## Experimentation practices

| Practice | Outcome |
| --- | --- |
| Baseline model | A clear performance floor before adding complexity. |
| MLflow tracking | Parameters, metrics, artifacts, and environments recorded per run. |
| Sweep jobs | Systematic hyperparameter search with early termination for poor runs. |
| Reproducible environment | Pinned package versions and registered Azure Machine Learning environments. |
| Version control | Training code, component specifications, and configuration tied to a Git commit. |

!!! tip
    Capture the training data asset version, source commit, environment version,
    parameters, and metrics for every candidate. This minimum record makes a
    successful experiment reproducible when it is promoted months later.

## Decision gates

Before a candidate becomes eligible for deployment, confirm it outperforms the
baseline or current production model on the agreed test data. Review not only
aggregate quality, but also material data slices and operational constraints
such as latency, model size, and inference cost.

| Gate | Example evidence |
| --- | --- |
| Quality | Accuracy, area under the curve (AUC), root mean square error (RMSE), or domain-specific metric. |
| Reliability | Repeatable results with the same data, code, and environment. |
| Fairness | Approved assessment for the scenario and known limitations. |
| Operability | Inference time, resource requirements, and failure handling within service objectives. |

Reference: [Track experiments with MLflow](https://learn.microsoft.com/azure/machine-learning/how-to-use-mlflow).