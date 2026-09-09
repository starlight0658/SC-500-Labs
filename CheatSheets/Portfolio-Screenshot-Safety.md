# Portfolio Screenshot Safety

Before publishing a cloud/security screenshot:

- Remove browser URL and account chrome.
- Mask personal email addresses.
- Mask tenant/subscription/object IDs unless necessary.
- Mask public IP addresses unless they are intentionally disposable and required for the explanation.
- Never publish passwords, access tokens, API keys, client-secret values, recovery codes, private keys, SAS tokens, or connection strings.
- Prefer screenshots of configuration state and successful validation over screenshots containing raw credentials.
- Re-check Git history if a secret was ever committed; deleting it from the latest version is not enough.
