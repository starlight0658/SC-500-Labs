# SC-500 Recent Labs — Add-Only Package

This package contains **only the labs completed during the most recent ~10-day study block**. It intentionally excludes the older 01–04 portfolio content so that the richer existing material is not overwritten.

## Included labs

- **11 — Azure Key Vault Monitoring & Alerting** — diagnostic settings, Log Analytics/KQL, and secret-access alert evidence.
- **12 — Microsoft Entra Workload Identity Governance** — app registration, Microsoft Graph application permissions, workload-identity Conditional Access, service-principal risk, time-bound PIM assignment, access review, short-lived credential lifecycle, audit evidence, and cleanup.
- **13 — Azure Network Security Baseline & JIT / Private Access Validation** — VM networking, NSG/JIT evidence, and private-network validation.
- **14 — Microsoft Defender for Cloud: Posture, Alerts & Workflow Automation** — posture/recommendations, security-alert investigation, Defender-to-Logic-App automation, and successful workflow run.
- **15 — Azure Key Vault Private Endpoint and Network Hardening** — Private Endpoint, Private DNS, connectivity validation, and public-access lockdown.
- **16 — Microsoft Entra Agent Identity and Risk-Based Conditional Access** — agent blueprint/identity governance and risk-based Conditional Access.
- **17 — Azure AI Security with Microsoft Foundry and Defender for Cloud** — Defender CSPM, Foundry deployment, guardrails, runtime validation, and Defender AI-discovery evidence.

## Safe merge method

1. Keep your existing `SC-500-Labs` folder exactly as it is.
2. Open this extracted package in Finder.
3. Copy **only folders 11 through 17** into the root of your existing `SC-500-Labs` repository.
4. Do **not** replace or delete folders 01–10.
5. Add the entries from `README-INDEX-SNIPPET.md` to your existing main `README.md`.
6. Review the sanitized screenshots once more before making the repository public.

Because these labs use new numbers, Finder should not ask to replace any of your existing lab folders.
