## Monitoring Overview

Effective monitoring is essential for identifying issues, analyzing performance, and maintaining the overall health of our application. Prometheus and Grafana work together to provide a comprehensive monitoring solution.

## Prometheus

### What is Prometheus?

[Prometheus](https://prometheus.io/) is an open-source monitoring and alerting toolkit designed for reliability and scalability. It is particularly well-suited for dynamic environments like cloud infrastructure.

### How Prometheus Works

Prometheus follows a pull-based model, where it scrapes metrics from various targets at regular intervals. These targets could be your application instances, databases, or any other services. Prometheus stores these metrics in a time-series database, allowing for querying and analysis.

### Prometheus Configuration

The configuration of Prometheus is defined in a YAML file (`prometheus.yml`). This file specifies the targets to scrape, the intervals, and other settings.

Our `prometheus.yml` configuration:

```
global:
  scrape_interval: 15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
  evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
  # scrape_timeout is set to the global default (10s).

# Alertmanager configuration
alerting:
  alertmanagers:
    - static_configs:
        - targets:
          # - alertmanager:9093

# Load rules once and periodically evaluate them according to the global 'evaluation_interval'.
rule_files:
  # - "first_rules.yml"
  # - "second_rules.yml"

# A scrape configuration containing exactly one endpoint to scrape:
# Here it's Prometheus itself.
scrape_configs:
  # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
  - job_name: "com619-devops"

    # metrics_path defaults to '/metrics'
    # scheme defaults to 'http'.

    static_configs:
            - targets: ["127.0.0.1:8080"]

    metrics_path: /metrics/prometheus

  - job_name: 'Sever stats'
    static_configs:
             - targets: ['127.0.0.1:9100']
```

## Grafana

### What is Grafana?

[Grafana](https://grafana.com/) is an open-source platform for monitoring and observability. It provides a customizable and feature-rich interface for visualizing metrics from various data sources, including Prometheus.

### Setting Up Grafana

To set up Grafana:

1. Install Grafana on a server.

```
server {
    listen 80;
    server_name com619-devops.uksouth.cloudapp.azure.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

Grafana is accessible on: https://com619-devops.uksouth.cloudapp.azure.com/grafana.
Authentification has been set up with username and password to access to Grafana.

2. Add Prometheus as a data source in Grafana.
   ![image](https://github.com/jrykns-org/not-a-virus-map/assets/91504148/b8eaf7d4-b32f-4f50-a60f-7719d742eb82)

3. Create dashboards to visualize key metrics.

![image](https://github.com/jrykns-org/not-a-virus-map/assets/91504148/6adba52c-9daf-4474-bc4e-c285a887ca85)

### Grafana Dashboards

Our Grafana dashboards are tailored to provide insights into critical metrics, including response times, error rates, and resource utilization.
