# Parking Management System

A full-stack loading area access and parking management system for exhibition setup and dismantling logistics.

## Planned architecture

The monorepo is organized around a Java/Spring Boot backend and three planned web interfaces:

- **Internal Management Portal** (`admin-web/`) for administrative users.
- **Parking Operations Web App** (`parking-ops-web/`) for on-site parking operations.
- **Public Loading Pass Page** (`public-pass-web/`) for public loading-pass access.

Supporting architecture notes live in `docs/`, while future database assets will live in `database/`.

## Current status

This repository currently contains foundation scaffolding only. The Spring Boot application can start and its application context is tested, but no business entities, authentication flows, APIs, frontend applications, migrations, containers, or business logic have been implemented.

## MVP phases

1. **Foundation:** establish the monorepo, backend build, configuration, and documentation.
2. **Backend domain and persistence:** define the approved domain model and PostgreSQL schema through Flyway.
3. **Backend application capabilities:** add security, services, and REST APIs.
4. **Web interfaces:** implement the internal, operations, and public experiences.
5. **Integration and delivery:** connect the interfaces to the backend and prepare deployment infrastructure.

## Backend development

The backend requires Java 21. Run its tests with:

```sh
cd backend
./mvnw test
```
