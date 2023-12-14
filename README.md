

# Project README: Prometheus and Grafana Monitoring Stack

## Overview
This project sets up a monitoring stack using Prometheus, Grafana, Node Exporter, and cAdvisor. It's designed to provide insights into your system's health and performance. Prometheus is used for metrics collection and alerting, Grafana for metrics visualization, Node Exporter for gathering system metrics, and cAdvisor for container metrics.

## Prerequisites
- Docker and Docker Compose
- Basic understanding of containerization

## Configuration Files
- `prometheus.yml`: Prometheus configuration file for defining scrape intervals and targets.

# monitoring with promitheus and visuals with grafana.

`prometheus.yml` should be put at `/etc/prometheus/prometheus.yml`. This can be done later

# use 
```bash
docker-compose up -d
```
to start the containers.

## Services

### Prometheus
- **Image**: prom/prometheus:latest
- **Container Name**: prometheus
- **Ports**: 9090
- **Volumes**: Configuration and data storage
- **Command**: Custom Prometheus config file path
- **Network**: monitoring

### Grafana
- **Image**: grafana/grafana:latest
- **Container Name**: grafana
- **Ports**: 4000 (mapped to 3000)
- **Volumes**: Data storage
- **Network**: monitoring

### Node Exporter
- **Image**: quay.io/prometheus/node-exporter:latest
- **Container Name**: node_exporter
- **Ports**: 9100
- **Command**: Root filesystem path
- **Network**: monitoring
- **Volumes**: Host system mount

### cAdvisor
- **Image**: google/cadvisor:latest
- **Container Name**: cadvisor
- **Ports**: 8080
- **Volumes**: Host system mounts
- **Privileged**: true
- **Devices**: /dev/kmsg
- **Network**: monitoring

## Networks
- **monitoring**: A dedicated network for all monitoring services.

## Deployment
Run `docker-compose up -d` to start all services in detached mode.

## Accessing the Services
- Prometheus: `http://<your-ip>:9090`
- Grafana: `http://<your-ip>:4000`
- Node Exporter: `http://<your-ip>:9100`
- cAdvisor: `http://<your-ip>:8080`

## Configuring Grafana
1. Access Grafana at `http://<your-ip>:4000`.
2. Log in with the default credentials (admin/admin).
3. Add Prometheus as a data source.
4. Import or create dashboards to visualize the metrics.

## Conclusion
This stack provides a robust solution for monitoring your systems and applications. For more advanced configurations and usage, refer to the official documentation of each tool.
"""
