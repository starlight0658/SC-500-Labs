# Cost and Cleanup Notes

This lab was intentionally run with paid Azure capabilities. Because the subscription was upgraded to pay-as-you-go, resources can continue generating charges after promotional credit expires.

## Before cleanup

Keep the environment only as long as needed to capture portfolio evidence and complete any remaining SC-500 exercises.

## Paid or potentially billable components to review

- Defender CSPM
- Defender for AI Services
- Defender for Servers Plan 2
- Microsoft Foundry / Azure AI model inference
- Existing virtual machine resources
- Storage, networking, logging, and monitoring resources already used by the broader SC-500 lab environment

## Recommended cleanup sequence

1. **Delete the model deployment** `gpt-5-4-mini-sc500` when no longer needed.
2. **Delete the East US Foundry resource** `foundry-sc500-ai-us` when the AI lab is complete.
3. Review whether the earlier Foundry resource `foundry-sc500-ai` is still needed; remove it if it was only created during the regional/quota troubleshooting phase.
4. In **Defender for Cloud → Environment settings → Defender plans**, turn off paid plans that are no longer required for later labs.
5. Stop/deallocate the SC-500 VM whenever it is not being used, and remove it when the bootcamp no longer needs it.
6. Review **Cost Management + Billing** after cleanup to confirm that expected daily charges are falling.

## Do not delete the entire shared resource group blindly

The Foundry resources were placed in the broader `rg-sc500-lab` environment, which also contains resources used by other SC-500 labs. Delete individual AI resources unless the entire SC-500 environment is ready for teardown.

## Secret hygiene

- Do not commit API keys, access tokens, credentials, `.env` files, or copied endpoint secrets.
- Public portfolio screenshots should redact personal account identifiers where practical.
- The screenshots in this package redact the Azure portal account label on selected images.
