# Configuration

Read the User Manual for detailed instructions on how to configure all EaseProbe parameters.

Create a configuration file (eg. `$CWD/config.yaml`) using the configuration template at [./resources/config.yaml](https://raw.githubusercontent.com/megaease/easeprobe/main/resources/config.yaml), which includes the complete list of configuration parameters.

The following simple configuration example can be used to get started:

```
http: # http probe
  - name: EaseProbe Github
    url: https://github.com/megaease/easeprobe
notify:
  log:
    - name: log file # local log file
      file: /var/log/easeprobe.log
settings:
  probe:
    timeout: 30s # the timeout for all probes
    interval: 1m # probe every minute for all probes
```

You can check the EaseProbe JSON schema section to use a JSON Scheme file to make your life easier when you edit the configuration file.
