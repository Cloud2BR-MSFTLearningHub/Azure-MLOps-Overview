# Business Problem and Responsible AI

Last updated: 2026-07-27

> **Business example:** A lender uses a model to prioritize applications for
> review. The business outcome is faster decisions, but the release criteria
> must also ensure the model does not create unjustified differences in outcomes
> for protected groups.

Start with the decision the model will support, not with a preferred algorithm.
Document the intended users, the expected benefit, known limitations, and the
cost of incorrect predictions before collecting or preparing data.

## Define the problem

| Activity | Practical question |
| --- | --- |
| Business objective | What decision, process, or customer experience will improve? |
| Machine learning task | Is this classification, regression, forecasting, natural language processing, or computer vision? |
| Success metrics | Which model measures and business key performance indicators (KPIs) define success? |
| Feasibility | Is representative data available and is the prediction useful at the required latency? |
| Stakeholders | Who owns the data, accepts risk, consumes predictions, and operates the platform? |

!!! important
    A technically accurate model can still be unsuitable if the intended use,
    limitations, and human decision process are unclear. Treat this information
    as a release artifact, not as a project kickoff note.

## Responsible AI controls

Use the Azure Machine Learning Responsible AI dashboard to evaluate fairness,
explainability, error patterns, and causal or counterfactual analysis when
appropriate for the scenario.

| Control | Evidence to retain |
| --- | --- |
| Fairness | Selected groups, measures, findings, and approved mitigations. |
| Explainability | Global and local explanation results that reviewers can interpret. |
| Error analysis | Failure slices, edge cases, and actions for material weaknesses. |
| Privacy and security | Data classification, access paths, retention, and approved use. |
| Human oversight | Escalation, override, and rollback procedures for consequential decisions. |

Reference: [Responsible AI in Azure Machine Learning](https://learn.microsoft.com/azure/machine-learning/concept-responsible-ai).