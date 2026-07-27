# Deployment and Serving

Last updated: 2026-07-27

<details markdown>
<summary>List of references</summary>

- [Managed online endpoints](https://learn.microsoft.com/azure/machine-learning/concept-endpoints-online)

</details>

Choose the inference pattern based on the caller, latency expectation, traffic
shape, and cost profile. Validate the model in a staging environment before
routing production traffic.

| Pattern | Azure option | Suitable for |
| --- | --- | --- |
| Real-time inference | Managed online endpoint | Low-latency, synchronous predictions. |
| Batch inference | Batch endpoint | Scheduled or large-volume scoring without an always-on service. |
| Edge inference | Azure IoT Edge and ONNX Runtime | Constrained or disconnected environments. |
| Embedded inference | Software development kit (SDK) or representational state transfer (REST) API | Application-specific integration. |

## Safe promotion

1. Register the approved model and serving environment by version.
2. Deploy the candidate to staging and run smoke and integration tests.
3. Route a small percentage of production traffic using a canary strategy.
4. Monitor quality and service health before increasing traffic.
5. Preserve the previous deployment and test rollback before full promotion.

!!! tip
    Batch endpoints normally provide a lower-cost option for periodic scoring
    because the compute can start for the job and scale down after completion.

## Endpoint security

- Use Azure Active Directory authentication and least-privilege authorization.
- Use managed identities for dependent Azure resources.
- Restrict production services with private endpoints and approved network paths.
- Store no credentials in scoring scripts, deployment specifications, or source
  control.
