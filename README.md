
---

# Monitoring Stack: Prometheus, Grafana, cAdvisor, Node Exporter

This project provides a ready-to-use Docker Compose setup for system and container monitoring with **Prometheus**, **Grafana**, **cAdvisor**, and **Node Exporter**.

---

## Features

- **Prometheus**: Collects metrics and provides powerful query capabilities.
- **Grafana**: Creates customizable dashboards for data visualization.
- **cAdvisor**: Monitors container resource usage (CPU, memory, disk, and network).
- **Node Exporter**: Collects system-level metrics (CPU, memory, disk, and more).

---

## Setup Instructions

### Step 1: Clone the Repository
```bash
git clone https://github.com/username/monitoring-stack.git
cd monitoring-stack
```

### Step 2: Create Required Resources
```bash
docker volume create grafana-data
docker network create monitoring
```

### Step 3: Start the Stack
```bash
docker-compose up -d
```

### Step 4: Access the Services
- **Prometheus**: [http://localhost:9090](http://localhost:9090)
- **Grafana**: [http://localhost:3000](http://localhost:3000)  
  *(Default login: `admin` / `admin`)*
- **cAdvisor**: [http://localhost:8080](http://localhost:8080)
- **Node Exporter**: Metrics exposed at [http://localhost:9100/metrics](http://localhost:9100/metrics)

---

## Configuration Details

### Prometheus
- Edit the `prometheus.yml` file to customize scrape targets and alert rules.

### Grafana
- Persistent data is stored in the `grafana-data` Docker volume.

### cAdvisor
- Accessible on port `8080` for monitoring container-level metrics.

### Node Exporter
- Exposes metrics on port `9100` for monitoring system-level metrics.

---

## Managing the Stack

### Stop and Remove Services
To stop and remove all services, use:
```bash
docker-compose down
```

---

## Setting Up Grafana with Prometheus

1. Access Grafana at [http://localhost:3000](http://localhost:3000).
2. Log in with default credentials:
   - Username: `admin`
   - Password: `admin`  
     *(You will be prompted to change the password after the first login.)*
3. Navigate to **Configuration** > **Data Sources** from the left menu.
4. Click **Add data source** and choose **Prometheus**.
5. Set the **URL** to `http://prometheus:9090` in the **HTTP** section.
6. Click **Save & Test**.  
   You should see a success message: *"Data source is working."*

---

## Importing Dashboards into Grafana

Grafana offers a wide range of prebuilt dashboards for system and container monitoring.

### Option 1: Use a Prebuilt Dashboard from Grafana's Library
1. Visit the [Grafana Dashboard Library](https://grafana.com/grafana/dashboards).
2. Search for a relevant dashboard:
   - **Docker and System Monitoring** (ID: `12280`)
   - **Node Exporter Full** (ID: `1860`)
3. Note the dashboard ID of your choice.

### Option 2: Import a Dashboard into Grafana
1. In Grafana, go to **Create** > **Import**.
2. Enter the dashboard ID in the **Import via grafana.com** field and click **Load**.
3. Choose your **Prometheus** data source and click **Import**.

---

## Customizing Dashboards

After importing, dashboards will display real-time metrics for your setup.  
If certain panels do not populate, review their query configurations to ensure they align with your setup.

---

## Troubleshooting

- Ensure Docker services are running.
- Verify that all services are reachable at their respective ports.
- Check log files for errors using:
  ```bash
  docker-compose logs
  ```

--- 
