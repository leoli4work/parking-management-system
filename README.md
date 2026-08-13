# Parking Management System

A full-stack loading area access and parking management system for exhibition setup and dismantling logistics.

## Planned architecture

The monorepo is organized around a Java/Spring Boot backend and three planned web interfaces:

- **Internal Management Portal** (`admin-web/`) for administrative users.
- **Parking Operations Web App** (`parking-ops-web/`) for on-site parking operations.
- **Public Loading Pass Page** (`public-pass-web/`) for public loading-pass access.

Supporting architecture notes live in `docs/`, while future database assets will live in `database/`.

## Current status

This repository currently contains foundation scaffolding and a local PostgreSQL development environment. The Spring Boot application can start and its application context is tested, but no business entities, authentication flows, APIs, frontend applications, migrations, or business logic have been implemented.

## MVP phases

1. **Foundation:** establish the monorepo, backend build, configuration, and documentation.
2. **Backend domain and persistence:** define the approved domain model and PostgreSQL schema through Flyway.
3. **Backend application capabilities:** add security, services, and REST APIs.
4. **Web interfaces:** implement the internal, operations, and public experiences.
5. **Integration and delivery:** connect the interfaces to the backend and prepare deployment infrastructure.

## Local development

### Prerequisites

- Java 21
- Docker with Docker Compose
- A POSIX-compatible shell (the repository includes the Maven Wrapper, so a separate Maven installation is not required)

### Configure the environment

From the repository root, copy the safe example configuration to the ignored local environment file:

```sh
cp .env.example .env
```

The defaults are intended only for local development. If you change the PostgreSQL database, user, password, or published port, keep the corresponding `DATABASE_*` values in `.env` in sync. Never commit `.env` or real credentials.

### Start PostgreSQL

Docker Compose automatically reads the root `.env` file:

```sh
docker compose up -d postgres
docker compose ps
```

Wait until `docker compose ps` reports the `postgres` service as `healthy`. Its persistent development data is stored in the Compose-managed `postgres-data` volume.

### Run the backend

Export the same root environment file before starting Spring Boot:

```sh
cd backend
set -a
. ../.env
set +a
./mvnw spring-boot:run
```

The backend connects to PostgreSQL with the `DATABASE_URL`, `DATABASE_USERNAME`, and `DATABASE_PASSWORD` variables. Flyway runs during application startup and verifies database connectivity; this repository does not contain any migrations or domain tables yet.

Stop the backend with <kbd>Ctrl</kbd>+<kbd>C</kbd>.

### Stop PostgreSQL

From the repository root, stop and remove the development container while retaining its database volume:

```sh
docker compose down
```

To also delete all locally persisted database data, run `docker compose down --volumes` instead.

## Backend tests

The test profile continues to use an in-memory H2 database, so Docker is not required to run the automated tests:

```sh
cd backend
./mvnw test
```
