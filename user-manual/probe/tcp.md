# TCP

**TCP**. Just simply check whether the TCP connection can be established or not. ( TCP Probe Configuration )

### TCP Probe Configuration

```
# TCP Probe Configuration
tcp:
  - name: SSH Service
    host: example.com:22
    timeout: 10s # default is 30 seconds
    interval: 2m # default is 60 seconds
    proxy: socks5://proxy.server:1080 # Optional. Only support socks5.
                                      # Also support the `ALL_PROXY` environment.
  - name: Kafka
    host: kafka.server:9093
```
