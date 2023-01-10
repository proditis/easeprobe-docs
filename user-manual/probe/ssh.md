# SSH

**SSH**. Run a remote command via SSH and check the result. Support the bastion/jump server (SSH Command Probe Configuration)

### SSH Command Probe Configuration

SSH probe is similar to Shell probe.

* Support Password and Private key authentication.
* Support the Bastion host tunnel.

The `host` supports the following configuration

* `example.com`
* `example.com:22`
* `user@example.com:22`

The following are examples of SSH probe configuration.

```
# SSH Probe Configuration
ssh:
  # SSH bastion host configuration
  bastion:
    aws: # bastion host ID      ◄──────────────────────────────┐
      host: aws.basition.com:22 #                              │
      username: ubuntu # login user                            │
      key: /path/to/aws/basion/key.pem # private key file      │
    gcp: # bastion host ID                                     │
      host: ubuntu@gcp.basition.com:22 # bastion host          │
      key: /path/to/gcp/basion/key.pem # private key file      │
  # SSH Probe configuration                                    │
  servers:   #                                                 │
    # run redis-cli ping and check the "PONG"                  │
    - name: Redis (AWS) # Name                                 │
      bastion: aws  # bastion host id ------------------------─┘
      host: 172.20.2.202:22
      username: ubuntu  # SSH Login username
      password: xxxxx   # SSH Login password
      key: /path/to/private.key # SSH login private file
      passphrase: xxxxxxx  # PrivateKey password
      cmd: "redis-cli"
      args:
        - "-h"
        - "127.0.0.1"
        - "ping"
      env:
        # set the `REDISCLI_AUTH` environment variable for redis password
        - "REDISCLI_AUTH=abc123"
      # check the command output, if does not contain the PONG, mark the status down
      contain : "PONG"
      not_contain: "failure" # response body must NOT contain this string, if it does the probe is considered failed.
      regex: false # if true, the contain and not_contain will be treated as regular expression. default: false

    # Check the process status of `Kafka`
    - name:  Kafka (GCP)
      bastion: gcp         #  ◄------ bastion host id
      host: 172.10.1.100:22
      username: ubuntu
      key: /path/to/private.key
      cmd: "ps -ef | grep kafka"
```

> **Note**:
>
> The Regular Expression supported refer to https://github.com/google/re2/wiki/Syntax
