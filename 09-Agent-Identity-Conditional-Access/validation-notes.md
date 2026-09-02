# Validation Notes

This lab was completed through the Microsoft Entra and Microsoft 365 admin portals.

No shell commands were required.

## Final Conditional Access control

```text
Policy: SC500-Agent-High-Risk-Block
Identity scope: All agent identities
Resource scope: All resources
Condition: Agent risk = High
Grant control: Block access
Policy state: Report-only
```

## Expected policy-impact result

At validation time, the Policy impact page showed:

```text
No data to display
```

This is expected because no matching high-risk agent sign-in was generated during the lab.

The lab intentionally did not fabricate risky activity merely to populate reporting data. The configuration evidence, audit evidence, and Report-only policy state are the retained validation artifacts.
