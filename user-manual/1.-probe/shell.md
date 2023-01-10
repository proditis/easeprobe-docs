# Shell

**Shell**. Run a Shell command and check the result. ( Shell Command Probe Configuration )

### Shell Command Probe Configuration

The shell command probe is used to execute a shell command and check the output.

The following example shows how to configure the shell command probe.

```
# Shell Probe Configuration
shell:
  # A proxy curl shell script
  - name: Google Service
    cmd: "./resources/probe/scripts/proxy.curl.sh"
    args:
      - "socks5://127.0.0.1:1085"
      - "www.google.com"

  # run redis-cli ping and check the "PONG"
  - name: Redis (Local)
    cmd: "redis-cli"
    args:
      - "-h"
      - "127.0.0.1"
      - "ping"
    clean_env: true # Do not pass the OS environment variables to the command
                    # default: false
    env:
      # set the `REDISCLI_AUTH` environment variable for redis password
      - "REDISCLI_AUTH=abc123"
    # check the command output, if does not contain the PONG, mark the status down
    contain : "PONG"
    not_contain: "failure" # response body must NOT contain this string, if it does the probe is considered failed.
    regex: false # if true, the `contain` and `not_contain` will be treated as regular expression. default: false

  # Run Zookeeper command `stat` to check the zookeeper status
  - name: Zookeeper (Local)
    cmd: "/bin/sh"
    args:
      - "-c"
      - "echo stat | nc 127.0.0.1 2181"
    contain: "Mode:"
```

> **Note**:
>
> The Regular Expression supported refer to https://github.com/google/re2/wiki/Syntax
