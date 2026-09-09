# Cleanup

This project used an Azure Logic App on a Consumption-style pay-per-operation model and Defender for Cloud lab resources.

After the lab:

- Disable or delete workflow automation if it is no longer required.
- Delete the Logic App when portfolio validation is complete if ongoing executions are unnecessary.
- Review Defender plans enabled on lab subscriptions and disable paid plans that are no longer needed.
- Stop/deallocate or remove lab VMs when not needed.
- Review Cost Management for residual resources.

Do not delete screenshots or documentation needed as portfolio evidence.
