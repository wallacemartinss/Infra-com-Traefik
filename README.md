<p align="center">
    <h2 align="center"> 
        Minimal VPS Infrastructure with Traefik, Monitoring, and Databases with Docker
    </h2>
</p>


## 🚀 About this Project

This project is a plug-and-play infrastructure setup designed for any VPS. It combines the power of **Traefik** for reverse proxy and SSL, a complete **monitoring stack** (Prometheus + Grafana), and **containerized databases** — all wired together with Docker.

Whether you're spinning up a dev environment or preparing for production, this setup helps you launch fast, stay secure, and keep everything under control.

---

## ✨ Features

- 🔐 **Automatic HTTPS** with Let's Encrypt via Traefik  
- 🔁 **Dynamic reverse proxy** for your services, with zero-downtime reloads  
- 📊 **Built-in monitoring stack** with Prometheus, Grafana, and exporters  
- 🛢️ **Containerized databases** like PostgreSQL and MySQL, ready to use  
- 🐳 **Fully Docker-based**, easy to deploy and manage  
- ⚙️ **Scalable foundation** for microservices or monoliths  
- 🧩 **Plug-and-play architecture** — just configure your `.env` and run  

---

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
     | production   |         |  production     |         |  production     |
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

- **`production`** — for core infrastructure services like Traefik, Grafana, Prometheus, and Portainer  
- **`databases`** — for database containers such as PostgreSQL, MySQL, Redis  
- **`application`** — for your actual app containers (API, frontend, workers, etc.)

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
---
