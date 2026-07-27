# Monitoring and Retraining

Last updated: 2026-07-27

Deployment is the beginning of the operational lifecycle. Monitor both the
inference service and the model's behavior as real-world data changes.

| Signal | Why it matters | Example service |
| --- | --- | --- |
| Latency, throughput, and errors | Identifies endpoint health and user impact. | Azure Monitor and Application Insights |
| Input data drift | Detects changes from the training distribution. | Azure Machine Learning model monitoring |
| Prediction drift | Reveals changes in output behavior. | Azure Machine Learning model monitoring |
| Model performance | Detects declining quality when ground truth is available. | Azure Machine Learning model monitoring |
| Compute utilization | Controls capacity and cost. | Azure Monitor and Container Insights |

## Retraining triggers

| Trigger | Appropriate use |
| --- | --- |
| Scheduled | A predictable refresh cycle when data changes regularly. |
| Drift-based | Input or prediction distribution exceeds an approved threshold. |
| Performance-based | Ground truth proves quality has fallen below a release threshold. |
| Event-based | An upstream schema, product, policy, or market event requires review. |

!!! note
    Data drift is an early warning signal, not proof of reduced model quality.
    Pair alerts with investigation, governance, and approved retraining gates.

Every retrained model remains a challenger. It must pass the same evaluation,
approval, and deployment process as the original release.

Reference: [Monitor models in production](https://learn.microsoft.com/azure/machine-learning/concept-model-monitoring).