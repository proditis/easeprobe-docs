# 6. Prometheus Metrics Exporter

EaseProbe supports Prometheus metrics exporter. The Prometheus endpoint is `http://localhost:8181/metrics` by default.

Currently, All of the Probers support the following metrics:

* `total`: the total number of probes
* `duration`: Probe duration in milliseconds
* `status`: Probe status
* `SLA`: Probe SLA percentage

And for the different Probers, the following metrics are available:

* HTTP Probe
  * `status_code`: HTTP status code
  * `content_len`: HTTP content length
  * `dns_duration`: DNS duration in milliseconds
  * `connect_duration`: TCP connection duration in milliseconds
  * `tls_duration`: TLS handshake duration in milliseconds
  * `send_duration`: HTTP send duration in milliseconds
  * `wait_duration`: HTTP wait duration in milliseconds
  * `transfer_duration`: HTTP transfer duration in milliseconds
  * `total_duration`: HTTP total duration in milliseconds
* Ping Probe
  * `sent`: Number of sent packets
  * `recv`: Number of received packets
  * `loss`: Packet loss percentage
  * `min_rtt`: Minimum round-trip time in milliseconds
  * `max_rtt`: Maximum round-trip time in milliseconds
  * `avg_rtt`: Average round-trip time in milliseconds
  * `stddev_rtt`: Standard deviation of round-trip time in milliseconds
  * `privileged`: Whether to use ICMP (`true`) or UDP (`false`) based ping probes, default `false`.

Please note that `privileged: true` requires administrative privileges such as `root` (for more details see https://github.com/go-ping/ping#supported-operating-systems)

* TLS Probe
  * `earliest_cert_expiry`: last TLS chain expiry in timestamp seconds
  * `last_chain_expiry_timestamp_seconds`: earliest TLS cert expiry in Unix time
* Shell & SSH Probe
  * `exit_code`: exit code of the command
  * `output_len`: length of the output
* Host Probe
  * `cpu`: CPU usage in percentage
  * `memory`: memory usage in percentage
  * `disk`: disk usage in percentage

The following snapshot is the Grafana panel for host CPU metrics

Refer to the Global Setting Configuration for further details on how to configure the HTTP server.
