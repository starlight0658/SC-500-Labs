# Validation Notes

## Objective

Validate an end-to-end security workflow for a generative AI workload deployed in Microsoft Foundry and monitored through Microsoft Defender for Cloud.

## Validation results

| Test | Expected result | Observed result | Status |
| --- | --- | --- | --- |
| Defender CSPM | Enhanced posture/security graph enabled | Defender CSPM enabled successfully | PASS |
| Defender for AI Services | AI workload protection enabled | AI Services plan enabled | PASS |
| Model deployment | Deploy a usable Foundry model endpoint | `gpt-5-4-mini-sc500` deployed in East US | PASS |
| Benign inference | Normal security question receives response | Successful response returned | PASS |
| Jailbreak test | Guardrail detects adversarial instruction override | Interaction blocked; risk type reported as `Jailbreak` | PASS |
| Runtime monitoring | Requests and tokens appear in monitor | 10 requests / 50.02K total tokens observed | PASS |
| Defender Inventory | Foundry assets appear after ingestion | Two Foundry resources and model deployment discovered | PASS |
| Data and AI Security | AI assets classified | 4 AI services reported | PASS |
| AI Discovery | Model/endpoint visible | 5 AI-related resources; 1 model & endpoint | PASS |
| Cloud Security Explorer | Model relationship visible in graph | Base model `Runs on` deployed endpoint | PASS |

## Troubleshooting timeline

### Initial symptom

The Foundry deployment was operational, but Defender initially reported:

- AI services: `0`
- AI Discovery: `0`
- No Foundry resources in Defender Inventory
- No results from the **AI workloads and models in use** Cloud Security Explorer query

### Evidence that the workload itself was healthy

Before Defender discovery completed, the lab had already validated:

- Foundry resource creation
- GPT-5.4-mini model deployment
- Successful inference
- Guardrail enforcement against jailbreak attempts
- Runtime request/token telemetry

This evidence indicated the workload was functional and pointed away from a deployment failure.

### Resolution

No destructive reconfiguration was performed. The environment was left running long enough for Defender's ingestion/security-graph processing to complete.

On the next validation pass:

- Defender Inventory increased from 15 to 18 resources.
- `foundry-sc500-ai` appeared.
- `foundry-sc500-ai-us` appeared.
- `gpt-5-4-mini-sc500` appeared as a Microsoft Foundry model deployment.
- Data and AI Security reported 4 AI services.
- AI Discovery reported 5 AI-related resources: 4 services and 1 model/endpoint.
- Cloud Security Explorer returned the GPT-5.4-mini base model → `Runs on` → `gpt-5-4-mini-sc500` relationship.

## Security interpretation

### Guardrail control

The Foundry Guardrail blocked attempts to override prior instructions and request hidden prompts/secrets. This validated an application/model interaction control designed to reduce jailbreak and prompt-injection risk.

### Defender CSPM control

Defender CSPM supplied posture and graph visibility. Once ingestion completed, the workload could be investigated as related entities rather than isolated Azure resources.

### Monitoring control

Foundry Monitor provided operational evidence that requests were reaching the deployed model. This helped separate model/runtime health from Defender discovery timing.

## Important distinction

The Foundry Guardrail and Defender AI threat-detection counters are separate control planes. A guardrail-blocked interaction does not necessarily produce a Defender AI threat-detection alert or increment the same telemetry counter.

## Portfolio takeaway

A useful troubleshooting sequence for cloud AI security is:

1. Verify resource deployment.
2. Verify benign runtime behavior.
3. Verify preventive controls.
4. Verify runtime telemetry.
5. Verify posture/inventory ingestion.
6. Verify security-graph relationships.

This avoids unnecessary reconfiguration when the actual issue is asynchronous security-service ingestion.
