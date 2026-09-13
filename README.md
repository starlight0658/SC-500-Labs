# Microsoft Identity, Cloud & AI Security Portfolio

Hands-on security engineering labs covering **Microsoft Entra ID, Conditional Access, privileged access, workload identities, Azure network security, Key Vault, Microsoft Defender for Cloud, agent identity, and Microsoft Foundry AI security**.

This repository began as SC-500 study work and has grown into a practical portfolio focused on **identity-first security, cloud posture management, governance, least privilege, and modern AI security controls**. Each major module documents the configuration, validation steps, screenshots, troubleshooting, and security lessons from a real Azure lab environment.

> **Portfolio focus:** IAM / Entra ID · Conditional Access · GRC-aligned controls · Azure security · Defender for Cloud · AI security

---

## Featured Projects

### 09 — Agent Identity & Conditional Access

[View project →](./09-Agent-Identity-Conditional-Access/)

Built and validated Conditional Access controls for Microsoft Entra **agent identities**, including:

- Microsoft Agent 365 licensing and agent identity discovery
- Conditional Access targeting **all agent identities**
- **Agent risk (Preview)** as a policy condition
- High-risk agent activity configured to **Block access**
- Safe deployment using **Report-only** mode
- Policy validation, inventory evidence, and audit-oriented documentation

**Security themes:** non-human identity governance, conditional access, least privilege, risk-based controls, policy rollout.

---

### 10 — Azure AI Security with Microsoft Foundry & Defender CSPM

[View project →](./10-Azure-AI-Security-Defender-Foundry/)

End-to-end AI security lab combining Microsoft Foundry with Defender for Cloud:

- Deployed a **GPT-5.4-mini** model endpoint in Microsoft Foundry
- Generated and monitored live inference traffic
- Validated benign prompts and **jailbreak / prompt-injection blocking** through Foundry Guardrails
- Captured deployment telemetry in Foundry Monitor
- Enabled **Defender CSPM** and AI workload protection capabilities
- Verified Defender discovery of Foundry resources and the model deployment
- Queried the **Cloud Security Explorer security graph** to identify the model-to-endpoint relationship
- Documented Defender ingestion delay / eventual-consistency troubleshooting

**Security themes:** AI governance, prompt security, runtime controls, CSPM, asset discovery, graph-based investigation, secure deployment validation.

---

### 11 — Defender for Cloud Security Posture & Recommendations

[View project →](./11-Defender-Cloud-Security-Posture/)

Reviewed live Defender for Cloud recommendations across Linux VM, AI/Foundry, Key Vault, Logic App, storage, and network resources; translated findings into a risk-to-remediation workflow.

**Security themes:** CSPM, vulnerability management, attack-surface reduction, remediation governance.

### 12 — File Integrity Monitoring

[View project →](./12-File-Integrity-Monitoring/)

Validated host file-change monitoring on `vm-sc500-linux`, including a controlled `/etc/` file modification with process, account, path, and cryptographic hash evidence.

**Security themes:** integrity monitoring, detective controls, host telemetry, audit evidence.

### 13 — Azure Policy Governance

[View project →](./13-Azure-Policy-Governance/)

Implemented and validated Azure Policy controls for centralized logging, tag inheritance, storage auditing, and anonymous blob-access enforcement, including completed remediation tasks.

**Security themes:** policy-as-code, compliance, preventive/detective/corrective controls, evidence and remediation.

### 14 — Sentinel Governance Automation

[View project →](./14-Sentinel-Governance-Automation/)

Built an end-to-end Sentinel workflow that detects Azure diagnostic-setting changes, creates incidents, and invokes a Logic App playbook to add governance-review instructions automatically.

**Security themes:** KQL, Sentinel analytics, MITRE ATT&CK, SOAR, Logic Apps, change governance.


### 15 — Regulatory Compliance Remediation & GRC Evidence Validation

[View project →](./15-Regulatory-Compliance-GRC/)

Closed the loop on a real Microsoft Defender for Cloud compliance finding mapped to **MCSB LT-3 — Enable logging for security investigation**:

- Identified a failed Logic Apps diagnostic-logging assessment
- Enabled workflow runtime logs and metrics to a central Log Analytics / Sentinel workspace
- Troubleshot missing telemetry by enabling the `LogicAppsManagement` workspace pack
- Validated six Logic App `WorkflowRuntime` events with KQL
- Reassessed the compliance recommendation and documented the remaining finding on a separate Logic App

**Security themes:** regulatory compliance, GRC evidence, centralized logging, KQL validation, residual-risk documentation, control remediation.

---

## What This Portfolio Demonstrates

| Area | Hands-on experience represented in this repo |
|---|---|
| **Identity & Access Management** | Entra ID, Azure RBAC, authentication, Conditional Access, privileged access, workload identities |
| **Authentication Security** | MFA-related controls, Temporary Access Pass, sign-in risk, user risk, trusted locations, device conditions |
| **Privileged Access** | Microsoft Entra Privileged Identity Management (PIM) and least-privilege concepts |
| **Workload Identity** | Managed identities, app registrations, service principals, client secrets, API permissions, admin consent |
| **Network Security** | VNets, subnet segmentation, NSGs, Private Link, Private Endpoints, Private DNS, UDRs, troubleshooting |
| **Secrets & Key Management** | Azure Key Vault, private endpoint hardening, network isolation, access validation |
| **Cloud Security Posture** | Defender for Cloud, Secure Score, recommendations, regulatory compliance, control remediation, evidence validation, vulnerability assessment |
| **Detection & Response** | Defender alerts, MITRE ATT&CK context, workflow automation, investigation and remediation workflows |
| **Agent / AI Security** | Agent identities, agent-risk Conditional Access, Microsoft Foundry, Guardrails, Defender CSPM AI discovery |
| **Security Documentation** | Validation notes, screenshots, troubleshooting records, cleanup plans, reproducible lab evidence |

---

## Lab Index

| Module | Focus | Key topics |
|---|---|---|
| [01 — Entra ID](./01-Entra-ID/) | Identity foundation | Azure RBAC, identity notes |
| [02 — Authentication](./02-Authentication/) | Authentication & risk | Conditional Access, TAP, sign-in risk, user risk, trusted locations, device controls, sign-in frequency |
| [03 — Conditional Access](./03-Conditional-Access/) | Access policy | Conditional Access policy practice and documentation |
| [04 — PIM](./04-PIM/) | Privileged identity | Privileged access and least-privilege administration |
| [Supplemental — Key Vault Monitoring](./04-key-vault-monitoring/) | Monitoring | Key Vault security monitoring lab |
| [05 — Workload Identities](./05-Workload-Identities/) | Non-human identity | Managed identity, service principals, app registrations, credentials, API permissions |
| [06 — Network Security](./06-Network-Security/) | Azure networking | VNets, NSGs, Private Endpoints, UDRs, Private DNS, troubleshooting |
| [07 — Defender for Cloud](./07-Defender-for-Cloud/) | CSPM / workload protection | Secure Score, compliance, Defender for Servers, vulnerability assessment, JIT, alerts, automation |
| [08 — Key Vault Private Endpoint](./08-Key-Vault-Private-Endpoint/) | Network hardening | Private Link, Private DNS, public-access lockdown, connectivity validation |
| [09 — Agent Identity Conditional Access](./09-Agent-Identity-Conditional-Access/) | Agent governance | Agent identity, agent risk, Conditional Access, report-only rollout |
| [10 — Azure AI Security](./10-Azure-AI-Security-Defender-Foundry/) | AI security | Foundry, GPT deployment, Guardrails, monitoring, Defender CSPM, AI discovery, security graph |
| [11 — Defender Security Posture](./11-Defender-Cloud-Security-Posture/) | CSPM / remediation | Defender recommendations, Linux vulnerabilities, AI/Foundry exposure, remediation prioritization |
| [12 — File Integrity Monitoring](./12-File-Integrity-Monitoring/) | Integrity monitoring | Linux FIM, file-change evidence, process/account attribution, hashes |
| [13 — Azure Policy Governance](./13-Azure-Policy-Governance/) | GRC / policy | Azure Policy compliance, remediation, tag governance, storage controls |
| [14 — Sentinel Governance Automation](./14-Sentinel-Governance-Automation/) | Detection & automation | AzureActivity, KQL, analytics rule, incident automation, Logic App playbook |
| [15 — Regulatory Compliance GRC](./15-Regulatory-Compliance-GRC/) | GRC / compliance validation | MCSB LT-3, Defender compliance finding, Logic App diagnostics, Log Analytics, KQL evidence, residual risk |

---

## Selected Technical Highlights

### Identity-first controls

The labs use identity and access policy as primary security controls rather than relying only on perimeter defenses. Examples include risk-based Conditional Access, managed identities, PIM, RBAC, service principals, and agent identities.

### Safe policy rollout

Potentially disruptive Conditional Access controls are documented in **Report-only** mode before enforcement. This mirrors a safer enterprise change-management workflow: define scope, validate impact, review evidence, then enforce.

### Private-access validation

The Key Vault hardening lab demonstrates a complete private-access path using **Private Endpoint + Private DNS**, followed by disabling public network access and validating that the Azure VM can still reach the vault over the private path.

### Cloud posture and investigation

Defender for Cloud labs cover posture management, recommendations, regulatory compliance, vulnerability assessment, alerts, remediation, and security-graph investigation.

### AI security beyond model deployment

The AI lab goes beyond simply provisioning a model. It validates **guardrails, runtime activity, Defender discovery, asset relationships, and Cloud Security Explorer graph queries** to demonstrate how generative-AI workloads can be governed and investigated in Azure.

---

## Repository Structure

Most modules contain some combination of:

```text
README.md
validation-notes.md
cleanup.md
screenshots/
lab*.md
```

The documentation is designed to show not only *what* was configured, but also **why the control matters, how it was validated, what failed during testing, and how the issue was resolved**.

---

## Security & Privacy Practices

- No passwords, access keys, API keys, client secrets, or authentication tokens are intentionally committed.
- Screenshots are selected or redacted to reduce exposure of personal and tenant-identifying information.
- Potentially disruptive controls are tested safely before enforcement where the platform supports it.
- Paid Azure resources are documented with cleanup steps to reduce unnecessary ongoing cost.
- These labs are educational portfolio environments, not production reference architectures.

---

## Current Direction

The portfolio is continuing to expand around **Microsoft identity security, cloud governance, Defender, AI security, and practical controls relevant to IAM / GRC / cloud-security roles**.
