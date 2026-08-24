# Lab 24 - Secure Score, Recommendations, and Regulatory Compliance

## Objective

Use Microsoft Defender for Cloud to assess cloud security posture, interpret recommendations, understand Secure Score, and validate regulatory compliance controls.

## Configuration

Reviewed Microsoft Defender for Cloud posture information for the lab subscription.

Key activities:

- Reviewed Secure Score as a posture metric rather than a guarantee of security.
- Opened security recommendations and examined remediation guidance.
- Reviewed the Microsoft cloud security benchmark in Regulatory Compliance.
- Investigated the Identity Management control family.
- Identified a failed centralized identity control caused by Storage Shared Key access.
- Disabled Shared Key access on the lab storage account.
- Returned to Regulatory Compliance and verified the Identity Management control returned to a healthy state.

## What I Learned

- Secure Score measures security posture and configuration hygiene.
- Recommendations identify configuration weaknesses and provide remediation guidance.
- Regulatory Compliance maps technical assessments to security controls.
- A compliance dashboard does not guarantee organizational compliance.
- A failed control can be caused by one specific resource assessment.
- Remediation fixes an existing issue; prevention controls help stop future insecure configurations.

## Memory Aid

- Secure Score = How healthy is the configuration?
- Recommendation = What should I fix?
- Compliance = Which control does it map to?
- Alert = What suspicious activity happened?
- Find -> Fix -> Prevent

## Screenshots

Screenshots for this lab were reviewed during the exercise. Sensitive portal identifiers were intentionally not included in this package.

## Interview Takeaway

I can use Defender for Cloud to trace a failed compliance control to the underlying resource assessment, remediate the configuration, and verify that the compliance posture improves after reassessment.

## Exam Notes

- Secure Score is not a percentage guarantee of security.
- Regulatory Compliance is not proof of legal or regulatory compliance.
- Recommendations are posture findings; alerts are threat detections.
- Exemptions mark justified exceptions as not applicable.
- Governance can assign recommendation owners and due dates.
