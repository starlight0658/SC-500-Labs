# Cleanup

After validation:

1. Remove temporary client secrets.
2. Allow the temporary PIM role assignment to expire or remove it if no longer required.
3. Keep Conditional Access policies in Report-only unless the tenant is intentionally being used to test enforcement.
4. Remove the lab application/service principal when the portfolio exercise is no longer required.
5. Review audit logs to verify cleanup actions.

The screenshot evidence in this repository confirms the temporary client secret was removed.
