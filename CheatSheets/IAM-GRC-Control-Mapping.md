# IAM / GRC Control Mapping Cheat Sheet

| Security objective | Microsoft control | Evidence type |
|---|---|---|
| Strong authentication | MFA / Authentication Strength | CA policy + sign-in evidence |
| Risk-based access | Identity Protection / Conditional Access | policy configuration |
| Least privilege | Entra roles / scoped API permissions | assignment and permission list |
| Temporary privilege | PIM | start/end assignment evidence |
| Access certification | Access Reviews | review + reviewer decision |
| Non-human identity governance | Workload Identities | service principal inventory + CA |
| Credential lifecycle | Client secrets / certificates | create/expire/remove evidence |
| Secret monitoring | Key Vault diagnostics + KQL | diagnostic settings + query |
| Cloud posture | Defender for Cloud | recommendations / Secure Score |
| Detection & response | Defender alerts + Logic Apps | alert + successful automation run |
| Network isolation | NSG / Private Endpoint / Private DNS | network configuration + connectivity |
| AI workload governance | Foundry Guardrails + Defender CSPM | blocked prompt + asset discovery |

## Evidence quality checklist

Good control evidence should answer:

- **What** control exists?
- **Why** was it implemented?
- **Who/what** is in scope?
- **How** was it configured?
- **Was it tested?**
- **What result proves it worked?**
- **What happens when access/control is no longer needed?**
