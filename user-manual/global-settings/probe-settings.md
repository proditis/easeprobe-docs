# Probe Settings

```
settings:
  probe:
    timeout: 30s # the time out for all probes
    interval: 1m # probe every minute for all probes
    failure: 2 # number of consecutive failed probes needed to determine the status down, default: 1
    success: 1 # number of consecutive successful probes needed to determine the status up, default: 1
```
