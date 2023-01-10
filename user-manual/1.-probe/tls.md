# TLS

**TLS**. Ping the remote endpoint, can probe for revoked or expired certificates ( TLS Probe Configuration )

### TLS Probe Configuration

TLS ping to remote endpoint, can probe for revoked or expired certificates

```
tls:
- name: expired test
    host: expired.badssl.com:443
    proxy: socks5://proxy.server:1080 # Optional. Only support socks5.
                                    # Also support the `ALL_PROXY` environment.
    insecure_skip_verify: true # dont check cert validity
    expire_skip_verify: true # dont check cert expire date
    alert_expire_before: 168h # alert if cert expire date is before X, the value is a Duration, see https://pkg.go.dev/time#ParseDuration. example: 1h, 1m, 1s. expire_skip_verify must be false to use this feature.
    # root_ca_pem_path: /path/to/root/ca.pem # ignore if root_ca_pem is present
    # root_ca_pem: |
    #   -----BEGIN CERTIFICATE-----
- name: untrust test
    host: untrusted-root.badssl.com:443
    # insecure_skip_verify: true # dont check cert validity
    # expire_skip_verify: true # dont check cert expire date
    # root_ca_pem_path: /path/to/root/ca.pem # ignore if root_ca_pem is present
    # root_ca_pem: |
    #   -----BEGIN CERTIFICATE-----
```
