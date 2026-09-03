# Azure Key Vault Secret Access Monitoring and Alerting

## Overview

This lab demonstrates an end-to-end security monitoring workflow for Azure Key Vault. The goal was to control access to secrets using Azure RBAC, collect Key Vault audit logs, detect successful secret reads with KQL, and automatically generate an Azure Monitor alert when the activity occurs.

The lab was completed using the Azure portal with a GUI-first workflow and documented with screenshots for repeatability.

## Security Objective

Protect sensitive secrets and create auditable evidence of secret access.

The control objective was to answer the following questions:

- Who can access secrets in the Key Vault?
- Are secret-read operations being logged?
- Can successful secret reads be detected reliably?
- Can Azure automatically alert when such activity occurs?

## Environment

- Microsoft Azure
- Azure Key Vault
- Azure RBAC
- Log Analytics workspace
- Azure Monitor
- Microsoft Sentinel workspace connection
- Kusto Query Language (KQL)

## Architecture

```text
User
  |
  v
Azure Key Vault
  |
  | AuditEvent / SecretGet
  v
Diagnostic Settings
  |
  v
Log Analytics Workspace
  |
  | KQL detection
  v
Azure Monitor Log Search Alert
  |
  v
Alert Fired
```

## Implementation

### 1. Create an Azure Key Vault

A Key Vault was created in the lab resource group using the Azure role-based access control permission model.

Key configuration choices included:

- Standard pricing tier
- Soft delete enabled
- Azure RBAC permission model
- Public endpoint enabled for the lab environment

> In a production environment, network access should be restricted according to organizational requirements.

### 2. Configure Least-Privilege Access

The `Key Vault Secrets Officer` role was assigned at the Key Vault scope.

This role allows secret operations without granting permission-management capabilities.

This demonstrates the principle of least privilege by separating secret-management permissions from broader administrative control.

### 3. Create a Test Secret

A non-production test secret was created to generate Key Vault audit activity.

The actual secret value is intentionally not included in this repository or screenshots.

### 4. Enable Diagnostic Logging

A Log Analytics workspace was created and connected to the Key Vault through **Diagnostic settings**.

The Key Vault was configured to send audit logs to the workspace.

This created a centralized location for security monitoring and investigation.

### 5. Verify Key Vault Audit Events

After revealing the test secret in the Azure portal, the Key Vault generated a successful `SecretGet` operation.

The events were ingested into the `AzureDiagnostics` table in Log Analytics.

## Detection Query

The following KQL query identifies successful secret-read operations for the lab Key Vault:

```kusto
AzureDiagnostics
| where ResourceProvider =~ "MICROSOFT.KEYVAULT"
| where Resource =~ "KV-SC500-01"
| where Category == "AuditEvent"
| where OperationName == "SecretGet"
| where ResultType == "Success"
| project TimeGenerated, OperationName, ResultType, CallerIPAddress, Resource
| order by TimeGenerated desc
```

### What the query checks

- `ResourceProvider` limits results to Azure Key Vault.
- `Resource` limits the search to the lab vault.
- `Category == "AuditEvent"` selects Key Vault audit activity.
- `OperationName == "SecretGet"` identifies secret reads.
- `ResultType == "Success"` confirms the operation succeeded.
- `CallerIPAddress` provides useful investigation context.

## Alert Rule

An Azure Monitor log search alert was created using the KQL detection.

Configuration:

- Signal: Custom log search
- Measure: Table rows
- Aggregation: Count
- Threshold type: Static
- Operator: Greater than
- Threshold value: `0`
- Evaluation frequency: 10 minutes
- Evaluation period: 10 minutes
- Severity: Informational

The rule therefore fires when at least one successful `SecretGet` event is detected during the evaluation window.

## Validation

The alert was tested by revealing the secret value in the Azure portal.

The validation sequence was:

```text
Secret accessed
    ↓
Key Vault generates SecretGet audit event
    ↓
Diagnostic settings export the event
    ↓
Log Analytics receives the event
    ↓
KQL matches SecretGet + Success
    ↓
Azure Monitor evaluates the rule
    ↓
Alert fires
```

The final Azure Monitor alert showed:

- Alert name: `SC500 - Key Vault Secret Read Alert`
- Severity: Informational
- Affected resource: `kv-sc500-01`
- Condition: Fired

This confirmed the monitoring pipeline was working end to end.

## Screenshots

| Screenshot | Description |
|---|---|
| `01-key-vault-created.png` | Key Vault deployment / configuration |
| `02-rbac-secret-officer.png` | Key Vault Secrets Officer RBAC assignment |
| `03-diagnostic-settings.png` | Key Vault logs routed to Log Analytics |
| `04-kql-secretget-detection.png` | KQL detecting successful `SecretGet` events |
| `05-alert-fired.png` | Azure Monitor alert successfully fired |

## Security Concepts Demonstrated

This lab demonstrates practical experience with:

- Least privilege
- Azure RBAC
- Secrets management
- Audit logging
- Security monitoring
- Log Analytics
- KQL
- Detection engineering fundamentals
- Alert creation and validation
- Control testing
- Evidence collection
- Cloud security governance

## Governance / GRC Relevance

Although the implementation includes technical monitoring, the workflow also demonstrates governance and compliance concepts.

A security control is not complete simply because it is configured. It should also be possible to verify that the control is operating as intended.

In this lab:

- **Preventive control:** RBAC restricts who can access secrets.
- **Detective control:** Key Vault audit logging records secret access.
- **Monitoring control:** KQL identifies relevant access events.
- **Response mechanism:** Azure Monitor raises an alert.
- **Evidence:** Log records and alert history demonstrate control operation.

This is an example of translating a security requirement into a technical control and then validating that control with auditable evidence.

## Key Takeaways

- Azure Key Vault access can be controlled using narrowly scoped RBAC roles.
- Diagnostic settings are required to route Key Vault audit logs to Log Analytics.
- Successful secret reads appear as `SecretGet` operations.
- KQL can turn raw audit data into a focused security detection.
- Azure Monitor can automatically evaluate that detection and generate alerts.
- Security controls should be tested and supported with evidence rather than assumed to be working.

## Repository Safety

No real credentials or production secrets are included in this lab.

Screenshots containing visible secret values are intentionally excluded or redacted before publication.

---

This lab was completed as part of hands-on Microsoft cloud security training.
