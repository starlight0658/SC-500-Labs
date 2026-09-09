# Azure AI Security with Microsoft Foundry and Defender for Cloud

> **Portfolio note:** This is a standalone project/module. Its numbering is canonical and is not part of the historical Lab 1–29 sequence.
## Overview

This lab demonstrates a practical Azure AI security workflow using **Microsoft Foundry**, **Microsoft Defender for Cloud**, **Defender CSPM**, and **Foundry Guardrails**.

The goal was not simply to deploy a language model. The lab validates the security lifecycle around an AI workload:

1. Enable cloud posture and AI workload protection.
2. Deploy an Azure-hosted generative AI model.
3. Validate normal inference.
4. Test adversarial prompt behavior against a guardrail.
5. Verify runtime telemetry.
6. Confirm Defender discovers the AI resources and model deployment.
7. Query the Defender security graph to validate the model-to-endpoint relationship.

## Environment

| Component | Configuration used in the lab |
| --- | --- |
| Cloud | Microsoft Azure |
| AI platform | Microsoft Foundry |
| AI resource | `foundry-sc500-ai-us` |
| Foundry project | `proj-sc500-ai-us` |
| Model deployment | `gpt-5-4-mini-sc500` |
| Model | GPT-5.4-mini |
| Model version | `2026-03-17` |
| Deployment type | Data Zone Standard |
| Region | East US |
| Cloud security | Microsoft Defender for Cloud |
| Posture management | Defender CSPM |
| AI protection | Defender for AI Services |
| AI safety control | Foundry Guardrail |

## Architecture

```mermaid
flowchart LR
    U[User / Tester] --> F[Microsoft Foundry Project]
    F --> D[GPT-5.4-mini Deployment]
    G[Foundry Guardrail] --> D
    D --> M[Foundry Runtime Monitoring]
    F --> A[Azure AI / Foundry Resource]
    A --> C[Defender for Cloud]
    D --> C
    C --> I[Defender Inventory]
    C --> DA[Data and AI Security]
    C --> S[Cloud Security Explorer]
```

## Security controls demonstrated

### 1. Defender CSPM enabled

Defender CSPM was enabled to provide enhanced posture management and security-graph capabilities for the Azure subscription.

![Defender CSPM enabled](screenshots/01-defender-cspm-enabled.png)

### 2. Model deployment with a guardrail

A GPT-5.4-mini model deployment was configured as a **Data Zone Standard** deployment in East US with the default Foundry guardrail applied.

![Foundry model deployment configuration](screenshots/02-foundry-model-deployment-config.png)

### 3. Normal inference validated

A benign request completed successfully, confirming that the model deployment was functional before adversarial testing.

![Benign request succeeds](screenshots/03-foundry-benign-request-success.png)

### 4. Jailbreak attempt blocked

Adversarial prompts attempted to override previous instructions and obtain hidden prompts, secrets, API keys, credentials, or confidential configuration. Foundry blocked the interaction and classified the input risk as **Jailbreak**.

![Foundry guardrail blocks jailbreak](screenshots/04-foundry-guardrail-jailbreak-block.png)

### 5. Runtime telemetry recorded

Foundry Monitor recorded real usage from the test session, including request count and token telemetry.

Observed during validation:

- 10 requests
- 50.02K total tokens
- 47.67K input tokens
- 2.35K output tokens

![Foundry runtime monitoring](screenshots/05-foundry-runtime-monitoring.png)

### 6. Defender discovered the AI workload

After Defender's ingestion cycle completed, Inventory showed both Foundry resources and the `gpt-5-4-mini-sc500` model deployment as a **Microsoft Foundry model deployment**.

![Defender Inventory discovers the model deployment](screenshots/06-defender-inventory-foundry-model-discovered.png)

### 7. Data and AI Security classified the resources

The Data and AI Security dashboard reported four AI services, and AI Discovery identified five AI-related resources consisting of four services and one model/endpoint.

![Defender Data and AI Security overview](screenshots/07-defender-data-ai-security-overview.png)

![Defender AI Discovery](screenshots/08-defender-ai-discovery-model-endpoint.png)

### 8. Security graph relationship validated

Cloud Security Explorer returned the relationship between the Azure base model and the deployed Foundry endpoint:

**GPT-5.4-mini base model → Runs on → `gpt-5-4-mini-sc500`**

This demonstrates that Defender CSPM understands the AI workload as a graph of related security entities rather than only as a flat resource inventory.

![Cloud Security Explorer model graph](screenshots/09-defender-cloud-security-explorer-ai-model-graph.png)

## What this lab demonstrates

- Azure AI workload deployment and configuration
- AI-specific cloud security posture management
- Generative-AI guardrail testing
- Adversarial prompt / jailbreak testing in a controlled lab
- Runtime request and token monitoring
- Defender for Cloud asset discovery
- AI inventory and model/endpoint classification
- Security-graph investigation with Cloud Security Explorer
- Troubleshooting asynchronous Defender ingestion
- Cost-aware Azure lab management

## Key finding

The most important operational lesson was that **resource creation and Defender discovery are not instantaneous**. The Foundry deployment was fully operational and producing runtime telemetry before Defender's Data and AI Security views and Cloud Security Explorer showed the workload. After the ingestion cycle completed, Defender identified the Foundry resources, the model deployment, and the model-to-endpoint graph relationship.

This is a useful example of distinguishing a **control/configuration failure** from **eventual-consistency or ingestion delay** during cloud-security troubleshooting.

## Validation evidence

Detailed observations and the troubleshooting timeline are documented in [validation-notes.md](validation-notes.md).

## Cost and cleanup

The lab used paid Azure security and AI capabilities in a controlled subscription. Cleanup steps are documented in [cleanup.md](cleanup.md). No API keys, credentials, or secrets are stored in this repository.
