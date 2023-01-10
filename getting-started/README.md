# Quick Start

Read the User Manual for detailed instructions on how to configure all EaseProbe parameters.

Create a configuration file (eg. `$CWD/config.yaml`) using the following simple configuration example&#x20;

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

A detailed configuration template can be found at [./resources/config.yaml](https://raw.githubusercontent.com/megaease/easeprobe/main/resources/config.yaml), which includes the complete list of configuration parameters.



```shell
$ build/bin/easeprobe -f config.yaml
```

* `-f` configuration file or URL or path for multiple files which will be auto merged into one. Can also be achieved by setting the environment variable `PROBE_CONFIG`
* `-d` dry run. Can also be achieved by setting the environment variable `PROBE_DRY`
