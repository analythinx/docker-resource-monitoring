---

# Monitoring Stack: Prometheus, Grafana, cAdvisor, Node Exporter

This project provides a simple Docker Compose setup for system and container monitoring using Prometheus, Grafana, cAdvisor, and Node Exporter.

---

## Features

- **Prometheus**: Collects metrics and triggers alerts.
- **Grafana**: Visualizes metrics with dashboards.
- **cAdvisor**: Tracks container resource usage.
- **Node Exporter**: Gathers system-level metrics.

---

## Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/username/monitoring-stack.git
   cd monitoring-stack
   ```

2. Create required resources:
   ```bash
   docker volume create grafana-data
   docker network create monitoring
   ```

3. Start the stack:
   ```bash
   docker-compose up -d
   ```

4. Access the services:
   - **Prometheus**: [http://localhost:9090](http://localhost:9090)
   - **Grafana**: [http://localhost:3000](http://localhost:3000) (Default login: `admin` / `admin`)
   - **cAdvisor**: [http://localhost:8080](http://localhost:8080)

---

## Configuration

- **Prometheus**: Modify `prometheus.yml` to add or update targets.
- **Grafana**: Data is stored in the `grafana-data` volume.
- **cAdvisor**: Exposes metrics on port `8080`.
- **Node Exporter**: Exposes system metrics on port `9100`.

---

## Stopping the Stack

To stop and remove all services:
```bash
docker-compose down
```
