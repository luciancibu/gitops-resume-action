# Dockerized Flask + Nginx + MariaDB

In this repository each service runs in its own Docker container and communicates over a Docker network.

## Architecture

Browser
  |
  v
Nginx (static site + reverse proxy)
  |
  v
Flask API
  |
  v
MariaDB

All services are orchestrated using Docker Compose.

## Services

- **Nginx**
  - Serves static HTML/CSS
  - Reverse-proxy for Flask API endpoints
- **Flask**
  - Simple API exposing `/view`
  - Increments and reads a counter from MariaDB
- **MariaDB**
  - Stores a persistent counter
  - Initialized automatically using SQL scripts

## Project Structure

```
.
├── docker-compose.yml
├── nginx/
│   ├── Dockerfile
│   ├── default.conf
│   └── html/
│       └── index.html
├── flask/
│   ├── Dockerfile
│   └── app.py
└── mariadb/
    └── init.sql
```

## How to Run

```bash
docker compose up -d --build
```

## Notes

- Services communicate using Docker service names.
- Only Nginx exposes a public port.