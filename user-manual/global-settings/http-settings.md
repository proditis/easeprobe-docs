# HTTP Settings

```
settings:
  # A HTTP Server configuration
  http:
    ip: 127.0.0.1 # the IP address of the server. default:"0.0.0.0"
    port: 8181 # the port of the server. default: 8181
    refresh: 5s # the auto-refresh interval of the server. default: the minimum value of the probes' interval.
    log:
      file: /path/to/access.log # access log file. default: Stdout
      # Log Rotate Configuration (optional)
      self_rotate: true # true: self rotate log file. default: true
                        # false: managed by outside  (e.g logrotate)
                        #        the blow settings will be ignored.
      size: 10 # max of access log file size. default: 10m
      age: 7 #  max of access log file age. default: 7 days
      backups: 5 # max of access log file backups. default: 5
      compress: true # compress the access log file. default: true
```
