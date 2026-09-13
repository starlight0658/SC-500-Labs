# Validation Notes — Lab 15

## Initial finding

Microsoft Defender for Cloud Regulatory Compliance mapped the Logic Apps diagnostic-logging assessment to **MCSB LT-3 — Enable logging for security investigation**.

`logic-sc500-defender-alert` was initially shown as the affected resource, with the Logic Apps recommendation at **1 of 1 failed**.

## Remediation performed

- Created diagnostic setting `sc500-compliance-logging`.
- Enabled Workflow runtime diagnostic events / allLogs.
- Enabled AllMetrics.
- Sent data to `Microsoft-Sentinel-Workspace`.
- Checked the Log Analytics `LogicAppsManagement` intelligence pack with Azure CLI.
- Enabled the pack after confirming it was `False`.
- Triggered the Logic App successfully after remediation.

## Technical validation

`AzureDiagnostics` returned six `WorkflowRuntime` records for `logic-sc500-defender-alert`, including run, trigger, and action start/completion events.

This independently validates that centralized investigation logging is operational.

## Compliance reassessment

The Defender assessment later displayed **1 of 2 failed** rather than **1 of 1 failed**. The unhealthy-resource view displayed a separate Logic App (`sc500-governanc...`), while the remediated `logic-sc500-defender-alert` was no longer the unhealthy resource shown.

Therefore:

- **Target resource remediation:** validated successfully.
- **LT-3 aggregate control:** still not fully compliant because a separate Logic App remains outstanding.

## Portfolio conclusion

The lab intentionally documents both successful remediation and residual compliance risk rather than claiming the entire control is green when another resource remains non-compliant.
