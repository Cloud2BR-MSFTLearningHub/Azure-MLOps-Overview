# Deployment Checklist

Last updated: 2026-07-27

<details markdown>
<summary>List of references</summary>

- [MLOps maturity model](https://learn.microsoft.com/azure/architecture/ai-ml/guide/mlops-maturity-model)
- [Model management and deployment with Azure Machine Learning](https://learn.microsoft.com/azure/machine-learning/concept-model-management-and-deployment)

</details>

Use this checklist as a staged control before a model reaches production.

## Foundation

- [ ] Business objective, intended use, limitations, and success measures are approved.
- [ ] Data owners, model owners, operational owners, and approvers are assigned.
- [ ] Data assets are versioned, access-controlled, and validated.
- [ ] Responsible AI assessment requirements are defined for the scenario.

## Training and validation

- [ ] Training code, components, environments, and parameters are version-controlled.
- [ ] Pipeline runs record data asset, source commit, environment, metrics, and artifacts.
- [ ] Candidate model passes quality, slice, fairness, and operational gates.
- [ ] Model registry metadata and release evidence are complete.

## Deployment

- [ ] Staging endpoint deployment and automated smoke tests pass.
- [ ] Endpoint identity, authorization, network controls, and secret handling are approved.
- [ ] Canary traffic plan, rollback procedure, and on-call ownership are tested.
- [ ] Monitoring dashboards, alerts, and cost budgets are active.

## Operations

- [ ] Data and prediction drift monitoring has a documented response process.
- [ ] Retraining triggers and approval controls are agreed.
- [ ] Retention, audit evidence, and platform hygiene tasks are scheduled.
- [ ] Infrastructure can be reproduced from reviewed Terraform configuration.