# Three-Interface Architecture

The planned system has a shared backend and three distinct web interfaces. Keeping these interfaces separate allows each one to serve its intended audience without combining internal, operational, and public concerns.

## Internal Management Portal

The Internal Management Portal will be the administrative interface for managing exhibition setup and dismantling logistics.

## Parking Operations Web App

The Parking Operations Web App will support on-site staff handling loading-area access and parking operations.

## Public Loading Pass Page

The Public Loading Pass Page will provide the public-facing loading-pass experience.

All three interfaces are planned to communicate with the shared Spring Boot backend. Their detailed workflows and implementation choices are outside the current foundation phase.
