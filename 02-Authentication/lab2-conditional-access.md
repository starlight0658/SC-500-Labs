# Lab 2 - Conditional Access and Authentication Strength

## Objective

Configure a Microsoft Entra Conditional Access policy that requires phishing-resistant MFA for a test user, deploy the policy in Report-only mode, and analyze the results in Microsoft Entra sign-in logs.

## Technologies Used

* Microsoft Entra ID P2
* Conditional Access
* Authentication Strengths
* Microsoft Entra Sign-in Logs

## Lab User

The Conditional Access policy was scoped only to a dedicated test user to avoid affecting administrator access.

## Conditional Access Policy

**Policy name:**

`SC500-Lab-Require-Phishing-Resistant-MFA`

### Assignments

* Users: SC500 Student
* Target resources: All resources
* Network: Not configured
* Conditions: Not configured

### Access Control

Grant access was configured to require:

`Phishing-resistant MFA strength`

### Policy State

`Report-only`

Report-only mode was used so that the policy could be evaluated without actually enforcing the authentication requirement or blocking the test user.

## Testing

The SC500 Student account signed in to Microsoft My Apps.

The sign-in succeeded using single-factor authentication because the Conditional Access policy was running in Report-only mode.

The sign-in event was then reviewed in:

`Microsoft Entra ID → Sign-in logs → Conditional Access → Report-only`

## Result

The Conditional Access policy returned:

`Report-only: User action required`

This indicates that the policy matched the sign-in, but the user's current authentication method did not satisfy the phishing-resistant MFA authentication strength.

If the policy had been enabled, the user would have been required to perform additional phishing-resistant authentication before access was granted.

## What I Learned

* Conditional Access determines when access controls should be applied.
* Authentication Strength determines how strong the authentication method must be.
* Authentication Methods determine which authentication mechanisms users can register and use.
* Report-only mode allows administrators to evaluate Conditional Access policies before enforcement.
* Sign-in logs can be used to troubleshoot and verify Conditional Access policy evaluation.
* A successful sign-in does not necessarily mean a Report-only Conditional Access policy would have allowed the same sign-in if enforcement were enabled.

## Key SC-500 Concept

**Authentication Methods = What can the user use?**

**Authentication Strength = How strong must authentication be?**

**Conditional Access = When should the requirement be enforced?**

## Security Best Practice

New Conditional Access policies should be tested before broad enforcement to reduce the risk of accidentally locking users or administrators out of the environment.