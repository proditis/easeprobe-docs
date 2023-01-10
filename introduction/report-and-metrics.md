# Report and Metrics

EaseProbe supports the following report and metrics:

* **SLA Report Notify:** EaseProbe will send a daily, weekly, or monthly SLA report using the defined **`notify:`** methods.
* **SLA Live HTML Report:** EaseProbe will listen (by default) on TCP port `8181` on any available interface for http requests. By accessing this service you will be provided with live SLA report either as HTML at `http://localhost:8181/`&#x20;
* **SLA Live JSON Report:** EaseProble also provides a JSON API end point for the SLA report data at `http://localhost:8181/api/v1/sla`
* **SLA Data Persistence**. The SLA data will persist under `$CWD/data/data.yaml` by default. You can configure this path by editing the `settings` section of your configuration file.
* **Prometheus Metrics:** EaseProbe proves a Prometheus metrics compatible end point at`http://easeprobe:8181/metrics`.

For more information, please check the Global Settings Configuration
