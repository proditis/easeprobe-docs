# SLA Settings

```
settings:
  # SLA Report schedule
  sla:
    #  minutely, hourly, daily, weekly (Sunday), monthly (Last Day), none
    schedule : "daily"
    # the time to send the SLA report. Ignored on hourly and minutely schedules
    # - the format is 'hour:min:sec'.
    # - the timezone can be configured by `settings.timezone`, default is UTC.
    time: "23:59"
    # SLA data persistence file path.
    # The default location is `$CWD/data/data.yaml`
    data: /path/to/data/file.yaml
    # Use the following to disable SLA data persistence
    # data: "-"
    backups: 5 # max of SLA data file backups. default: 5
               # if set to a negative value, keep all backup files
```
