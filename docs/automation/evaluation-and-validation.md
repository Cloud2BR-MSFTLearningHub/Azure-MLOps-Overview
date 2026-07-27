# Evaluation and Validation

Last updated: 2026-07-27

<details markdown>
<summary>List of references</summary>

- [Responsible AI in Azure Machine Learning](https://learn.microsoft.com/azure/machine-learning/concept-responsible-ai)

</details>

Evaluation is a release gate, not only a data-science activity. Define the
criteria in code so a candidate model cannot be registered or promoted when it
falls below agreed quality, fairness, or operational thresholds.

## Validation dimensions

| Dimension | Questions to answer |
| --- | --- |
| Model quality | Does the candidate outperform the baseline and current champion? |
| Data slices | Does quality remain acceptable by geography, segment, period, or other material group? |
| Fairness | Are selected fairness measures within agreed bounds? |
| Explainability | Can reviewers understand the influential features and limitations? |
| Resilience | How does the model behave on edge, missing, or out-of-distribution inputs? |
| Serving readiness | Does the model meet latency, scale, and resource requirements? |

## Promotion criteria as code

The evaluation component should emit machine-readable metrics and exit with a
non-zero result when a threshold is not met. The continuous integration pipeline
can then prevent registration or deployment automatically.

> **Business example:** A demand forecast is promoted only when its weighted
> absolute percentage error remains lower than the current production model for
> every high-volume region, not merely in the global average.

Record the data asset version, pipeline run identifier, Git commit, environment,
key metrics, and approval outcome on every registered model version.
