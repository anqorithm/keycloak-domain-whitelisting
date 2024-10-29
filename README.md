# Keycloak Development Environment with Email Domain Validation

A Docker Compose setup for Keycloak with PostgreSQL database and email domain validation for development purposes.

## Prerequisites

- Docker
- Docker Compose

## Quick Start

1. Create a new directory and copy the `docker-compose.yml` file into it.

2. Create a `providers` directory and download the latest keycloak-mail-whitelisting jar:
```bash
mkdir providers
curl -o providers/keycloak-mail-whitelisting-2.0.jar https://repo1.maven.org/maven2/net/micedre/keycloak/keycloak-mail-whitelisting/2.0/keycloak-mail-whitelisting-2.0.jar
```

3. Start the services:
```bash
docker-compose up -d
```

4. Access Keycloak:
- Main URL: http://localhost:8080
- Admin Console: http://localhost:8080/admin

## Configure Email Domain Validation

1. Log in to the admin console
2. Go to Authentication menu
3. Copy the registration flow
4. Add a new execution below "Profile Validation"
5. Choose either:
   - "Profile Validation With Email Domain Check" (whitelist)
   - "Profile Validation with domain block" (blacklist)
6. Set the execution to "Required"
7. Configure the allowed/blocked domains
8. Change the registration binding to this new flow
9. Enable realm registration and email verification

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
- The email domain validation extension is mounted in the providers directory
- The extension provides `authorizedMailDomains` and `unauthorizedMailDomains` attributes for the registration page

## References

- [Keycloak Mail Whitelisting Extension](https://github.com/micedre/keycloak-mail-whitelisting)
- [Maven Repository](https://repo1.maven.org/maven2/net/micedre/keycloak/keycloak-mail-whitelisting/)
