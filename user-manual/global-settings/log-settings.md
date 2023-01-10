# Log Settings

```
settings:
  # easeprobe program running log file.
  log:
    file: "/path/to/easeprobe.log" # default: stdout
    # Log Level Configuration
    # can be: panic, fatal, error, warn, info, debug.
    level: "debug"
    # Log Rotate Configuration (optional)
    self_rotate: true # true: self rotate log file. default: true
                        # false: managed by outside  (e.g logrotate)
                        #        the blow settings will be ignored.
    size: 10 # max of access log file size. default: 10m
    age: 7 #  max of access log file age. default: 7 days
    backups: 5 # max of access log file backups. default: 5
    compress: true # compress the access log file. default: true
```
