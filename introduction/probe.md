# Probe

EaseProbe supports a variety of methods to perform its probes such as:

* **HTTP**. Checking the HTTP status code, Support mTLS, HTTP Basic Auth, and can set the Request Header/Body. ( HTTP Probe Configuration )
* **TCP**. Check whether a TCP connection can be established or not. ( TCP Probe Configuration )
* **Shell**. Run a Shell command and check the result. ( Shell Command Probe Configuration )
* **SSH**. Run a remote command via SSH and check the result. Support the bastion/jump server (SSH Command Probe Configuration)
* **TLS**. Connect to a given port using TLS and (optionally) validate for revoked or expired certificates ( TLS Probe Configuration )
* **Host**. Run an SSH command on a remote host and check the CPU, Memory, and Disk usage. ( Host Load Probe )
* **Client**. The following native clients are supported. They all supports the mTLS and the data checking, please refer to Native Client Probe Configuration
  * **MySQL**. Connect to a MySQL server and run the `SHOW STATUS` SQL.
  * **Redis**. Connect to a Redis server and run the `PING` command.
  * **Memcache**. Connect to a Memcache server and run the `version` command or validate a given key/value pair.
  * **MongoDB**. Connect to a MongoDB server and perform a ping.
  * **Kafka**. Connect to a Kafka server and perform a list of all topics.
  * **PostgreSQL**. Connect to a PostgreSQL server and run `SELECT 1` SQL.
  * **Zookeeper**. Connect to a Zookeeper server and run `get /` command.
