# Application settings

The following example configurations illustrate the EaseProbe supported features.

```
version: v2.0.0
# Global settings for all probes and notifiers.
settings:
  # The customized name and icon
  name: "EaseProbe" # the name of the probe: default: "EaseProbe"
  icon: "https://path/to/icon.png" # the icon of the probe. default: "https://megaease.com/favicon.png"
  # Daemon settings

  # pid file path,  default: $CWD/easeprobe.pid,
  # if set to "", will not create pid file.
  pid: /var/run/easeprobe.pid
  # Date format
  # Date
  #  - January 2, 2006
  #  - 01/02/06
  #  - Jan-02-06
  #
  # Time
  #   - 15:04:05
  #   - 3:04:05 PM
  #
  # Date Time
  #   - Jan _2 15:04:05                   (Timestamp)
  #   - Jan _2 15:04:05.000000            (with microseconds)
  #   - 2006-01-02T15:04:05-0700          (ISO 8601 (RFC 3339))
  #   - 2006-01-02 15:04:05
  #   - 02 Jan 06 15:04 MST               (RFC 822)
  #   - 02 Jan 06 15:04 -0700             (with numeric zone)
  #   - Mon, 02 Jan 2006 15:04:05 MST     (RFC 1123)
  #   - Mon, 02 Jan 2006 15:04:05 -0700   (with numeric zone)
  timeformat: "2006-01-02 15:04:05 Z07:00"
  # check the following link to see the time zone list
  # https://en.wikipedia.org/wiki/List_of_tz_database_time_zones
  timezone: "America/New_York" #  default: UTC  
```

## PID File

The EaseProbe would create a PID file (default `$CWD/easeprobe.pid`) when it starts. it can be configured by:

```
settings:
pid: /var/run/easeprobe.pid
```

* If the file already exists, EaseProbe would overwrite it.
* If the file cannot be written, EaseProbe would exit with an error.

If you want to disable the PID file, you can configure the pid file to "".

```
settings:
pid: "" # EaseProbe won't create a PID file
```
