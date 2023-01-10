# Administration

EaseProbe can be configured by supplying a YAML file or URL to fetch configuration settings from.

By default, EaseProbe will look for its `config.yaml` on the current folder. This behavior can be changed by supplying the `-f` parameter.

```shell
easeprobe -f path/to/config.yaml
easeprobe -f https://example.com/config
```

The following environment variables can be used to fine-tune the request to the configuration file

* `HTTP_AUTHORIZATION`
* `HTTP_TIMEOUT`

### 5.2 Log file Rotation

There are two types of the log files: **Application Log** and **HTTP Access Log**.

Both application and HTTP access logs will be displayed on StdOut by default. Both can be be configured by the `log:` directive such as:

```
log:
file: /path/to/log/file
self_rotate: true # default: true
```

If `self_rotate` is `true`, EaseProbe would rotate the log automatically, and the following options are available:

```
size: 10 # max size of log file. default: 10M
age: 7 # max age days of log file. default: 7 days
backups: 5 # max backup log files. default: 5
compress: true # compress. default: true
```

If `self_rotate` is `false`, EaseProbe will not rotate the log, and the log file will have to be rotated by a 3rd-party tool (such as `logrotate`) or manually by the administrator.

```shell
mv /path/to/easeprobe.log /path/to/easeprobe.log.0
kill -HUP `cat /path/to/easeprobe.pid`
```

EaseProbe accepts the `HUP` signal to rotate the log.
