# Validation Commands

These are the only shell commands used in this lab.

## Private DNS resolution

```bash
getent hosts kv-sc500-01.vault.azure.net
```

Expected result includes:

```text
172.16.0.5
```

## HTTPS destination validation

```bash
curl -sS -o /dev/null \
  -w "Connected IP: %{remote_ip}\nHTTP status: %{http_code}\n" \
  https://kv-sc500-01.vault.azure.net/
```

Expected network-validation result:

```text
Connected IP: 172.16.0.5
```

The HTTP status itself is not the goal of this test. The important evidence is that the connection reaches the Private Endpoint IP.
