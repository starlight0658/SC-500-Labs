# Validation Notes — Lab 14

## End-to-end result

The full governance workflow was validated successfully:

1. A real diagnostic-setting change was generated.
2. The change appeared in Azure Activity / `AzureActivity` as a successful diagnostic-settings write.
3. The scheduled Sentinel analytics rule detected the event.
4. Sentinel created a Medium-severity incident.
5. The incident-created automation rule ran the Logic App playbook.
6. The playbook added the governance-review comment to the incident.

## ATT&CK context

The detection was mapped to **Defense Evasion → T1562 Impair Defenses → T1562.008 Disable or Modify Cloud Logs**, because altering cloud logging can reduce security visibility and audit evidence.

## Portfolio conclusion

This lab demonstrates practical detection engineering, Sentinel automation, Logic Apps, and GRC-oriented review design in one workflow.
