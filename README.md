# Microsoft Identity, Cloud & AI Security Portfolio

Hands-on Microsoft security labs covering **Entra ID, authentication, Conditional Access, PIM, workload identities, Azure networking, Key Vault, Defender for Cloud, agent identities, and Azure AI security**.

This repository preserves the original detailed SC-500 exercises (**Labs 1–29**) and adds newer module-level portfolio projects and sanitized evidence. The detailed lab files are retained as technical build records; each module `README.md` provides a recruiter-friendly security and governance summary.

**Portfolio model:** Scenario → Risk → Control → Implementation → Validation → Evidence → GRC relevance

> **Portfolio direction:** IAM / identity governance · GRC-aligned controls · Azure security · Defender · AI security

---

## Module index

| Module | Project | Main controls / evidence |
|---|---|---|
| [01](01-Entra-ID/) | Entra ID Identity Foundation | Lab 1 Azure RBAC, identity inventory, governance foundation |
| [02](02-Authentication/) | Authentication Security | Labs 2–9: Conditional Access, TAP, sign-in/user risk, trusted locations, device/platform controls, session controls |
| [03](03-Conditional-Access/) | Conditional Access | policy design, report-only rollout, contextual access |
| [04](04-PIM/) | Privileged Identity Management | Labs 10–14 plus time-bound service-principal privilege, access review, attestation |
| [04B](04B-Key-Vault-Monitoring/) | Key Vault Monitoring | diagnostics, Log Analytics/KQL, secret-access alert validation |
| [05](05-Workload-Identities/) | Workload Identity Governance | Labs 15–18 plus service-principal risk, workload CA, PIM, access review, credential lifecycle |
| [06](06-Network-Security/) | Network Security | Labs 19–23 plus NSG/JIT/private networking evidence |
| [07](07-Defender-for-Cloud/) | Defender for Cloud | Labs 24–29 plus posture, alert investigation, Logic App workflow automation |
| [08](08-Key-Vault-Private-Endpoint/) | Key Vault Private Endpoint | Private Link, Private DNS, public-access lockdown, positive/negative validation |
| [09](09-Agent-Identity-Conditional-Access/) | Agent Identity Conditional Access | agent governance, agent risk, report-only blocking |
| [10](10-Azure-AI-Security-Defender-Foundry/) | Azure AI Security | Foundry, guardrails, Defender CSPM, AI asset discovery and security graph |

---

## Original detailed labs retained

The historical exercise numbering is intentionally preserved rather than renumbered:

- **Lab 1** — Azure RBAC (`01-Entra-ID`)
- **Labs 2–9** — Authentication and risk-based Conditional Access (`02-Authentication`)
- **Labs 10–14** — PIM and privileged-access workflows (`04-PIM`)
- **Labs 15–18** — Workload identity fundamentals (`05-Workload-Identities`)
- **Labs 19–23** — Azure network security (`06-Network-Security`)
- **Labs 24–29** — Microsoft Defender for Cloud (`07-Defender-for-Cloud`)

`03-Conditional-Access` is a module-level policy summary rather than a separately numbered historical exercise. `04B` and Modules `08–10` are later standalone portfolio projects.

---

## Featured project — Workload Identity Governance

The workload identity module follows a non-human identity through an end-to-end governance lifecycle:

```text
App registration
  -> Microsoft Graph application permission
  -> Workload Identity Conditional Access
  -> high service-principal risk blocking
  -> time-bound PIM role assignment
  -> access review + attestation
  -> temporary client credential
  -> credential removal + audit evidence
```

This demonstrates practical controls for service principals and applications alongside human identities.

---

## Featured project — Defender alert automation

The Defender module proves a complete detection-to-response path:

```text
Defender finding
  -> high-severity alert
  -> workflow automation
  -> Azure Logic App
  -> successful response action
  -> run-history evidence
```

---

## Skills represented

- Microsoft Entra ID and Azure RBAC
- Conditional Access and risk-based access
- MFA and authentication strength
- Privileged Identity Management and access reviews
- Service principals and workload identities
- Microsoft Graph application permissions and admin consent
- Credential lifecycle governance
- Azure networking, NSGs, JIT, Private Link and Private DNS
- Azure Key Vault
- Log Analytics and KQL
- Azure Monitor alerts
- Microsoft Defender for Cloud
- Azure Logic Apps security automation
- Microsoft Entra agent identities
- Microsoft Foundry / Azure AI security
- audit-log validation, control testing, remediation evidence, and security documentation

---

## Security & privacy

Screenshots added in the newer portfolio modules are sanitized copies. Browser/account chrome is cropped where practical and tenant/account identifiers are masked where needed. No client-secret value, password, API key, token, or other credential is intentionally included.

The original detailed exercise evidence is preserved because it represents the work already completed; before publishing any newly added screenshots, follow [`SANITIZATION.md`](SANITIZATION.md).

---

## Repository use

These projects document a personal training environment. They demonstrate security reasoning, implementation, validation, troubleshooting, and evidence collection; they are not production reference architectures.
