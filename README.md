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

## Adding Prometheus as a Data Source in Grafana

1. Open your browser and go to [http://localhost:3000](http://localhost:3000).
2. Log in with the default credentials:
   - Username: `admin`
   - Password: `admin`  
   (You will be prompted to change the password on first login.)
3. In the left menu, go to **Configuration** > **Data Sources**.
4. Click **Add data source** and select **Prometheus** from the list.
5. Under the **HTTP** section, set the **URL** to `http://prometheus:9090`.
6. Click **Save & Test**. You should see a "Data source is working" message.

---

## Importing a Dashboard into Grafana

Grafana provides a wide variety of dashboards for visualizing metrics. You can either create a custom dashboard or import a prebuilt one from the Grafana dashboard library.

### Option 1: Explore and Import a Prebuilt Dashboard

1. Visit the [Grafana Dashboard Library](https://grafana.com/grafana/dashboards).
2. Search for a dashboard that suits your needs. For example:
   - **Docker and System Monitoring** (ID: `12280`)
   - **Node Exporter Full** (ID: `1860`)
3. Note the dashboard ID of your choice.

### Option 2: Import the Dashboard into Grafana

1. In Grafana, navigate to **Create** > **Import** from the left menu.
2. Enter the dashboard ID from Grafana's library into the **Import via grafana.com** field and click **Load**.
3. Select your **Prometheus** data source and click **Import**.

---

## Customizing the Dashboard

Once imported, the dashboard will display real-time metrics for your system and containers. If some panels do not show data, check and update their queries to match your setup.
---
