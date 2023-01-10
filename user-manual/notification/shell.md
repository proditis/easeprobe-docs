# Shell

Run a shell command to notify the result. (see example)

The plugin supports the following parameters:

* `name`: A unique name for this notification endpoint
* `cmd`: The command to execute
* `args`: Optional list of arguments as child items (see example below)
* `env`: Optional list of environment variables to set when he command is executed (see example below)

Example:

```
# Notification Configuration
notify:
  # EaseProbe set the following environment variables
  #  - EASEPROBE_TYPE: "Status" or "SLA"
  #  - EASEPROBE_NAME: probe name
  #  - EASEPROBE_STATUS: "up" or "down"
  #  - EASEPROBE_RTT: round trip time in milliseconds
  #  - EASEPROBE_TIME: time of probe time(formatted by timeformat configured in settings section)
  #  - EASEPROBE_TIMESTAMP: timestamp of probe time
  #  - EASEPROBE_MESSAGE: probe message
  # and offer two formats of string
  #  - EASEPROBE_JSON: the JSON format
  #  - EASEPROBE_CSV: the CSV format
  # The CSV format would be set for STDIN for the shell command.
  # (see the example: resources/scripts/notify/notify.sh)
  shell:
    - name: "shell alert service"
      cmd: "/bin/bash"
      args:
        - "-c"
        - "/path/to/script.sh"
      clean_env: true # Do not pass the OS environment variables to the command
                      # default: false
      env: # set the env to the notification command
        - "EASEPROBE=1"
        - "KEY=Value"
```
