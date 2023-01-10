# 1. Probe

## 1.1 Overview

EaseProbe supports the following probing methods: **HTTP**, **TCP**, **TLS**, **Shell Command**, **SSH Command**, **Host Resource Usage**, and **Native Client**.

Each probe is identified by the method it supports (eg `http`), a unique name (across all probes in the configuration file) and the method specific parameters.

* **HTTP**. Checking the HTTP status code, Support mTLS, HTTP Basic Auth, and can set the Request Header/Body. ( HTTP Probe Configuration )
* **TCP**. Just simply check whether the TCP connection can be established or not. ( TCP Probe Configuration )
* **Ping**. Just simply check whether can be pinged or not. ( Ping Probe Configuration )
* **Shell**. Run a Shell command and check the result. ( Shell Command Probe Configuration )
* **SSH**. Run a remote command via SSH and check the result. Support the bastion/jump server (SSH Command Probe Configuration)
* **TLS**. Ping the remote endpoint, can probe for revoked or expired certificates ( TLS Probe Configuration )
* **Host**. Run an SSH command on a remote host and check the CPU, Memory, and Disk usage. ( Host Load Probe )
*   **Client**. Currently, support the following native client. Support the mTLS. ( refer to: Native Client Probe Configuration )

    * **MySQL**. Connect to the MySQL server and run the `SHOW STATUS` SQL.
    * **Redis**. Connect to the Redis server and run the `PING` command.
    * **Memcache**. Connect to a Memcache server and run the `version` command or check based on key/value checks.
    * **MongoDB**. Connect to MongoDB server and just ping server.
    * **Kafka**. Connect to Kafka server and list all topics.
    * **PostgreSQL**. Connect to PostgreSQL server and run `SELECT 1` SQL.
    * **Zookeeper**. Connect to Zookeeper server and run `get /` command.

    Most of the clients support the additional validity check of data pulled from the service (such as checking a redis or memcache key for specific values). Check the documentation of the corresponding client for details on how to enable.

## 1.2 Initial Fire Up

On application startup, the configured probes are scheduled for their initial fire up based on the following criteria:

* Less than or equal to 60 total probers exist: the delay between initial prober fire-up is `1 second`
* More than 60 total probers exist: the startup is scheduled based on the following equation `timeGap = DefaultProbeInterval / numProbes`

> **Note**:
>
> **If multiple probes using the same name then this could lead to corruption of the metrics data and/or the behavior of the application in non-deterministic way.**
