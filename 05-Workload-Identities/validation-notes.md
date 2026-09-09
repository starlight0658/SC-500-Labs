# Validation Notes

The workload-identity lab was validated through multiple independent control planes:

- App registration confirmed creation of the workload identity.
- Microsoft Graph application permission demonstrated application-to-API authorization.
- Workload Identity Conditional Access targeted the selected service principal.
- Service principal risk was configured as the policy condition.
- Block access was selected as the grant control.
- The policy was created in Report-only mode for safe validation.
- PIM showed a time-bound Directory Readers role assignment.
- An access review was created and reviewer attestation completed.
- A temporary client secret was created with a short lifetime.
- The client secret was removed after the credential-lifecycle exercise.
- Entra audit logs were reviewed during the lab to confirm application and role-management changes.

No client-secret value is included in this repository.
