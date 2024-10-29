# Keycloak Development Environment

A Docker Compose setup for Keycloak with PostgreSQL database for development purposes.

## Prerequisites

- Docker
- Docker Compose

## Quick Start

1. Create a new directory and copy the `docker-compose.yml` file into it.

2. Start the services:
```bash
docker-compose up -d
```

3. Access Keycloak:
- Main URL: http://localhost:8080
- Admin Console: http://localhost:8080/admin

## Default Credentials

### Admin Console
- Username: `admin`
- Password: `admin`

### PostgreSQL
- Database: `keycloak`
- Username: `keycloak`
- Password: `keycloak_password`

## Basic Commands

```bash
# Start services
docker-compose up -d

# Stop services
docker-compose down

# View logs
docker-compose logs

# Remove everything including volumes
docker-compose down -v
```

## Important Notes

- This is a development setup - not for production use
- Data is persisted in a Docker volume named `postgres_data`
