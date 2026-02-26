# Clickhouse Exporter for Prometheus (old clickhouse-server versions)

This is a simple server that periodically scrapes [ClickHouse](https://clickhouse.com/) stats and exports them via HTTP for [Prometheus](https://prometheus.io/)
consumption.

Exporter could used only for old ClickHouse versions, modern versions have embedded prometheus endpoint.
Look details https://clickhouse.com/docs/en/operations/server-configuration-parameters/settings#server_configuration_parameters-prometheus

To run it:

```bash
./clickhouse_exporter [flags]
```

Help on flags:
```bash
./clickhouse_exporter --help

Usage of ./clickhouse_exporter:
  -clickhouse_only
    	Expose only Clickhouse metrics, not metrics from the exporter itself
  -insecure
    	Ignore server certificate if using https (default true)
  -scrape_uri string
    	URI to clickhouse http endpoint (default "http://localhost:8123/")
  -telemetry.address string
    	Address on which to expose metrics. (default ":9116")
  -telemetry.endpoint string
    	Path under which to expose metrics. (default "/metrics")
```

Credentials(if not default):

via environment variables
```
CLICKHOUSE_USER
CLICKHOUSE_PASSWORD
```

## Build Docker image
```
docker build . -t clickhouse-exporter
```

## Using Docker

```
docker run -d -p 9116:9116 clickhouse-exporter -scrape_uri=http://clickhouse-url:8123/
```
## Sample dashboard
Grafana dashboard could be a start for inspiration https://grafana.com/grafana/dashboards/882-clickhouse
