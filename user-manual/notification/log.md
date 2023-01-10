# Log

Write notifications into a log file or send through syslog.

The plugin supports the following parameters:

* `name`: A unique name for this notification endpoint
* `file`: The path to the file that will hold the logs or **`syslog`**
* `host`: Optionally the hostname or IP and port that your syslog server accepts messages, _syslog delivery is **NOT** supported on Windows hosts_
* `network`: Optionally the network transport to use **`tcp`**, **`udp`**

**NOTE:**

> Windows platforms do not support syslog as notification method

Example:

```
# Notification Configuration
notify:
  log:
    - name: "Local Log"
      file: "/tmp/easeprobe.log"
      dry: true
    - name: Remote syslog # syslog (!!! Not For Windows !!!)
      file: syslog # <-- must be "syslog" keyword
      host: 127.0.0.1:514 # remote syslog server - optional
      network: udp #remote syslog network [tcp, udp] - optional
```
