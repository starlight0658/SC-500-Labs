# Validation Notes — Lab 12

## Verified evidence

- Defender for Cloud FIM displayed `vm-sc500-linux`.
- The captured dashboard showed **94 file changes**.
- A detailed event for `sc500-fim-test.conf` recorded a **Modified** change under `/etc/`.
- The event contained host, process, account, and hash evidence.

## Controlled test conclusion

The end-to-end File Integrity Monitoring pipeline was functioning: host change → telemetry collection → Defender/Log Analytics evidence.
