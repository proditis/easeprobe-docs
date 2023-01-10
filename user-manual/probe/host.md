# Host

**Host**. Run an SSH command on a remote host and check the CPU, Memory, and Disk usage. ( Host Load Probe )

### Host Resource Usage Probe Configuration

The host resource usage probe allows for collecting information and alerting when certain resource utilization thresholds are exceeded.

The resources currently monitored include CPU, memory and disk utilization. The probe status is considered as `down` when any value exceeds its defined threshold.

> **Note**:
>
> * The remote system to be monitored needs to have the following commands installed and available: `top`, `df`, `free`, `awk`, `grep`, `tr`, `cat` and `hostname`.
> * The disk usage check is limited to the root filesystem only with the following command `df -h /`.
> * The actual load would be divided by cpu core number, the threshold won't consider the cpu core number (requires proc filesystem support).

```yaml
host:
  bastion: # bastion server configuration
    aws: # bastion host ID      ◄──────────────────┐
      host: ubuntu@example.com # bastion host      │
      key: /path/to/bastion.pem # private key file │
  # Servers List                                   │
  servers: #                                       │
    - name : aws server   #                        │
      bastion: aws #  <-- bastion server id ------─┘
      host: ubuntu@172.20.2.202:22
      key: /path/to/server.pem
      disks: # [optional] Check multiple disks. if not present, only check `/` by default
        - /
        - /data
      threshold:
        cpu: 0.80  # cpu usage  80%
        mem: 0.70  # memory usage 70%
        disk: 0.90  # disk usage 90%
        load: # load average - Note: the actual load would be divided by cpu core number, the threshold won't consider the cpu core number.
          m1: 0.5  # 1 minute load average 0.5 (default: 0.8)
          m5: 0.9  # 5 minute load average 0.9 (default: 0.8)
          m15: 0.9 # 15 minute load average 0.9 (default: 0.8)

    # Using the default threshold
    # cpu 80%, mem 80%, disk 95% and 0.8 load average
    - name : My VPS
      host: user@example.com:22
      key: /Users/user/.ssh/id_rsa
```
