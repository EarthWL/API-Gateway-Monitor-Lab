
# Docker-Compose Project for Strapi, Kong, Konga, Prometheus, Grafana, and More

This repository contains a docker-compose setup for a full-fledged development and monitoring environment using several powerful tools. Below is a detailed description of each service configured in this project.

## Services Overview

1. **Strapi**
    - **Image**: `strapi/strapi:alpine`
    - **Ports**: `1338:1338`
    - **Description**: Strapi is an open-source headless CMS that provides a robust and customizable API.

2. **Kong**
    - **Image**: `kong`
    - **Ports**: `8000:8000`, `8443:8443`
    - **Description**: Kong is a scalable, open-source API layer (also known as an API gateway or API middleware).

3. **Kong Migrations**
    - **Image**: `kong`
    - **Description**: Runs the necessary migrations for Kong.

4. **Kong Database**
    - **Image**: `postgres:14.11-bullseye`
    - **Description**: PostgreSQL database used by Kong.

5. **Konga**
    - **Image**: `pantsel/konga`
    - **Ports**: `1337:1337`
    - **Description**: Konga is an open-source, customizable dashboard for managing Kong API Gateway.

6. **Konga Database**
    - **Image**: `postgres:9.6`
    - **Description**: PostgreSQL database used by Konga.

7. **Prometheus**
    - **Image**: `prom/prometheus:latest`
    - **Ports**: `9090:9090`
    - **Description**: Prometheus is an open-source systems monitoring and alerting toolkit.

8. **Grafana**
    - **Image**: `grafana/grafana:latest`
    - **Ports**: `3000:3000`
    - **Description**: Grafana is an open-source platform for monitoring and observability.

9. **Alertmanager**
    - **Image**: `prom/alertmanager`
    - **Ports**: `9093:9093`
    - **Description**: Alertmanager handles alerts sent by client applications such as the Prometheus server.

10. **cAdvisor**
    - **Image**: `google/cadvisor:latest`
    - **Ports**: `8080:8080`
    - **Description**: cAdvisor (Container Advisor) provides container users an understanding of the resource usage and performance characteristics of their running containers.

## Setup Instructions

1. **Clone the Repository**
   ```bash
   gh repo clone EarthWL/API-Gateway-Monitor-Lab
   cd API-Gateway-Monitor-Lab
   ```

2. **Start the Docker Containers**
   ```bash
   docker-compose up -d
   ```

3. **Access the Services**
    - Strapi: `http://localhost:1338`
    - Kong: `http://localhost:8000` (Proxy) and `http://localhost:8001` (Admin)
    - Konga: `http://localhost:1337`
    - Prometheus: `http://localhost:9090`
    - Grafana: `http://localhost:3000`
    - Alertmanager: `http://localhost:9093`
    - cAdvisor: `http://localhost:8080`

## Configuration Files

- `prometheus.yml`: Configuration for Prometheus.
- `alert.rules.yml`: Alert rules for Prometheus.
- `alertmanager.yml`: Configuration for Alertmanager.

## Notes

- Ensure that the volumes and ports configured in the `docker-compose.yml` file do not conflict with other services running on your machine.
- For persistent data, ensure that the specified volumes are correctly mounted to avoid data loss.
- The environment variables in the `docker-compose.yml` should be adjusted according to your setup.

---
