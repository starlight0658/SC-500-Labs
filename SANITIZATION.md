# Screenshot Sanitization

The screenshots in this portfolio are derived from a real training tenant but have been prepared for public GitHub use.

## Removed or masked

Where present, the portfolio copies remove or obscure:

- browser address bars and URL query strings
- signed-in account information
- personal email addresses
- tenant IDs
- subscription IDs
- object IDs when they are not necessary to explain the control
- public/private IP addresses when they add no portfolio value
- credential identifiers when unnecessary
- secret values, passwords, tokens, and keys

## Client-secret safety

The workload-identity exercise included creation of a temporary client secret.

**No screenshot containing the client-secret value is included.**

The portfolio contains only:

1. the pre-creation form showing the short custom lifetime, and
2. the post-cleanup view confirming the secret was removed.

## Advanced projects

Modules 08, 09, and 10 were already prepared as sanitized, public-portfolio packages and are included unchanged.

## Reminder before publishing

Even after sanitization, review screenshots once more before pushing to a public repository. Security hygiene should treat screenshots as data, not decoration.
