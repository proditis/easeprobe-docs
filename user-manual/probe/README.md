# Probe

EaseProbe supports the following probing methods: **HTTP**, **TCP**, **TLS**, **Shell Command**, **SSH Command**, **Host Resource Usage**, and **Native Client**.

Each probe is identified by the method it supports (eg `http`), a unique name (across all probes in the configuration file) and the method specific parameters.

All probes have the following default options:

* `timeout` - the maximum time to wait for the probe to complete. default: `30s`.
* `interval` - the interval time to run the probe. default: `1m`.
* `failure` - number of consecutive failed probes needed to determine the status down, default: `1`
* `success` - number of consecutive successful probes needed to determine the status up, default: `1`

## Initial Fire up

On application startup, the configured probes are scheduled for their initial fire up based on the following criteria:

* Less than or equal to 60 total probers exist: the delay between initial prober fire-up is `1 second`
* More than 60 total probers exist: the startup is scheduled based on the following equation `timeGap = DefaultProbeInterval / numProbes`

> **Note**:
>
> **If multiple probes using the same name then this could lead to corruption of the metrics data and/or affect the behavior of the application in non-deterministic way.**
