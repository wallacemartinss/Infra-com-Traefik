<p align="center">
    <h2 align="center"> 
        Minimal VPS Infrastructure with Traefik, Monitoring, and Databases with Docker
    </h2>
</p>

---

## 🚀 About this Project

This project is a plug-and-play infrastructure setup designed for any VPS. It combines the power of **Traefik** for reverse proxy and SSL, a complete **monitoring stack** (Prometheus + Grafana), and **containerized databases** — all wired together with Docker.

Whether you're spinning up a dev environment or preparing for production, this setup helps you launch fast, stay secure, and keep everything under control.

---
## ❤️ Support This Project

**If you find this project useful, please consider [sponsoring me on GitHub](https://github.com/sponsors/wallacemartinss)! on GitHub! — it helps keep the project active and maintained!**

Your sponsorship helps me dedicate more time to adding features, fixing bugs, and building open source tools for the community. Thank you for your support! 🙏

---

## ✨ Features

- 🔐 **Automatic HTTPS** with Let's Encrypt via Traefik with Dns Challenge (CloudFlare)
- 🔁 **Dynamic reverse proxy** for your services, with zero-downtime reloads  
- 📊 **Built-in monitoring stack** with Prometheus, Grafana, and exporters  
- 🛢️ **Containerized databases** like PostgreSQL, Redis and MySQL, ready to use  
- 🐳 **Fully Docker-based**, easy to deploy and manage  
- ⚙️ **Scalable foundation** for microservices or monoliths  


## 🧱 Architecture Diagram

Below is a simplified overview of the infrastructure:

                             +--------------------------+
                             |        INTERNET          |
                             +--------------------------+
                                         |
                                         ▼
                                +----------------+
                                |     Traefik     |
                                |  (production)   |
                                +----------------+
                                         |
             +---------------------------+---------------------------+
             |                           |                           |
             ▼                           ▼                           ▼
     +--------------+         +-----------------+         +-----------------+
     |   Grafana    |         |   Prometheus    |         |   Portainer     |
     | Monitoring   |         |  production     |         |  production     |
     +--------------+         +-----------------+         +-----------------+

                   (All services above are reverse proxied by Traefik)

                        +-----------------------------------+
                        |        Application Layer          |
                        |        (application network)      |
                        +-----------------------------------+
                        |        Your custom services       |
                        |    (API, WebApp, Workers, etc.)   |
                        +-----------------------------------+

                        +-----------------------------------+
                        |            Databases              |
                        |         (databases network)       |
                        +-----------------------------------+
                        |      PostgreSQL / MySQL/ Redis    |
                        +-----------------------------------+


---

## 🕸️ Docker Network Design

This project uses **three isolated Docker networks** to provide clean architecture and enhance security:

- **`production`** — for core infrastructure services like Traefik, Prometheus, and Portainer  
- **`databases`** — for database containers such as PostgreSQL, MySQL, Redis  
- **`application`** — for your actual app containers (API, frontend, workers, etc.)
- **`Monitoring`** — for the Exporter's and Grafana

Each container is connected only to the networks it needs — reducing attack surfaces and keeping your infrastructure modular and maintainable.


---

## 🛠️ Useful Commands

A collection of handy commands to help you manage your infrastructure and server setup.

---

## 🔐 SSH Key Management

**Generate a new SSH key (no passphrase):**
```bash

ssh-keygen -t ed25519 -C "your-email@example.com" -f ~/.ssh/id_ed25519_ci -N ""

```

**View the private key:**
```bash

cat ~/.ssh/id_ed25519_ci

```

**View the public key:**
```bash

cat ~/.ssh/id_ed25519_ci.pub

```

**Add the public key to the server (as root):**
Append the .pub content to:
```bash

/root/.ssh/authorized_keys

```

**Set correct permissions on the server:**
```bash

chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys

```
---

## 🧪 Generate Basic Auth Password for Traefik Dashboard

**Use the command below to create a hashed password for use with basic auth in Traefik:**
```bash

htpasswd -nbB yourusername yourpassword

```
Example output: admin:$2y$05$abc123...longhash...

Use this in your Traefik middleware config for securing the dashboard.


---

### 🔗 Docker Networks

**Create a Docker network:**
```bash

docker network create <network-name>

```

**List all Docker networks:**
```bash

docker network ls

```

---

### 📄 Traefik Logs


**Follow Traefik logs:**
```bash

docker logs -f traefik

```

**Filter Traefik logs for certificate activity:**
```bash

docker logs -f traefik | grep certificate

```

### 🔧 Node exporter

**Install and configure Prometheus Node Exporter to monitor system metrics (CPU, memory, disk, etc).**

📥 **1. Download Node Exporter**
```bash
cd /opt
curl -LO https://github.com/prometheus/node_exporter/releases/download/v1.9.0/node_exporter-1.9.0.linux-amd64.tar.gz

```

📦 **2. Extract and move binary**
```bash
tar xvf node_exporter-1.9.0.linux-amd64.tar.gz
mv node_exporter-1.9.0.linux-amd64/node_exporter /usr/local/bin/
rm -rf node_exporter-1.9.0.linux-amd64*
```

👤 **3. Create a system user**

```bash
sudo useradd --no-create-home --shell /usr/sbin/nologin node_exporter
```

🔥 **4. Open port 9100**
```bash
ufw allow 9100/tcp
```

🚀 **5. Start and enable the service**

```bash
systemctl daemon-reload
systemctl start node_exporter
systemctl enable node_exporter
```

---

### 📊 1. Importing Dashboards in Grafana

✔️ Traefik - Dashboard ID: 4475

✔️ PostgreSQL - Dashboard ID: 9628

✔️ MySQL - Dashboard ID: 7362

✔️ Redis - Dashboard ID: 11835

✔️ Node Exporter (server metrics)- Dashboard ID: 1860

To browse ready-to-use community dashboards: 🔗 https://grafana.com/grafana/dashboards

---

## 🐳 Docker & Compose Commands

Essential Docker commands to help you manage containers, images, volumes, and services with ease.

---

### 📦 Container Management

**List running containers:**
```bash

docker ps

```

**List all containers (including stopped ones):**
```bash

docker ps -a

```

**Start a container:**
```bash

docker start <container_name>

```

**Stop a container:**
```bash

docker stop <container_name>

```

**Restart a container:**
```bash

docker restart <container_name>

```

**Restart a container:**
```bash

docker restart <container_name>

```

**Restart a container:**
```bash

docker rm <container_name>

```

---
### 🧰 Docker Compose

**Start all services in the background:**

```bash

docker compose up -d

```

**Start services with rebuild (no cache):**

```bash

docker compose up -d --build --no-cache

```
**Stop all running services:**

```bash

docker compose down

```

**Stop all running services and remove volumes:**

```bash

docker compose down -v

```

**Rebuild services:**

```bash

docker compose build

```

**View logs for all services:**

```bash

docker compose logs -f

```

**View logs for a specific service:**

```bash

docker compose logs -f <service_name>

```

**Restart a specific service:**

```bash

docker compose restart <service_name>

```

---

### 🧱 Image Management

**List local Docker images:**
```bash

docker images

```

**Build an image (from Dockerfile):**
```bash

docker build -t <image_name> .

```

**Build an image (from Dockerfile):**
```bash

docker rmi <image_name>

```

---

### 🧹 Cleanup Commands

**Remove all stopped containers:**
```bash

docker container prune

```

**Remove unused images:**
```bash

docker image prune

```

**Remove all unused volumes:**
```bash

docker volume prune

```