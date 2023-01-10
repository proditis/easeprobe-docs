# Ping

**Ping**. Just simply check whether can be pinged or not. ( Ping Probe Configuration )

### Ping Probe Configuration

```
ping:
  - name: Localhost
    host: 127.0.0.1
    count: 5 # number of packets to send, default: 3
    lost: 0.2 # 20% lost percentage threshold, mark it down if the loss is greater than this, default: 0
    privileged: true # if true, the ping will be executed with icmp, otherwise use udp, default: false (Note: On Windows platform, this must be set to True)
    timeout: 10s # default is 30 seconds
    interval: 2m # default is 60 seconds
```
