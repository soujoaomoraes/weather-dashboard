# Gemini Workspace Context: weather-dashboard

## Project Overview

This project is a backend for a weather dashboard application. The goal is to create a high-performance, reliable, and scalable backend that consumes data from public weather APIs (like OpenWeatherMap and WeatherAPI) and serves optimized data to a frontend.

The core technologies are **Node.js/TypeScript** and **Python (FastAPI)** for the backend, with **PostgreSQL** for the database and **Redis** for caching. The architecture is based on microservices.

Key features include:
*   An API Gateway with rate limiting.
*   An intelligent caching system.
*   Weather data processing.
*   User query history.
*   An alert/notification system.
*   Geolocation and city search.
*   Structured logging and monitoring.

The project has a strong emphasis on quality, with a target of <100ms response time for each endpoint, 99.9% uptime, and >85% test coverage.

## Building and Running

**TODO:** No build or run commands were found in the project files. This section should be updated with instructions on how to build and run the project.

## Development Conventions

The project follows a strict documentation structure, which is detailed in `prompts/Backend Developer Agent.md`. All documentation must adhere to this structure.

The development process is as follows:
1.  Analyze requirements and design the architecture.
2.  Define API contracts (OpenAPI spec).
3.  Implement services with robust error handling.
4.  Configure cache strategies.
5.  Implement unit and integration tests.
6.  Document endpoints and prepare for deployment.

## Key Files

*   `prompts/Backend Developer Agent.md`: This file contains the complete persona and instructions for the backend developer agent, including technical requirements, the development process, and the mandatory documentation structure.
*   `docs/overview/effort-estimation.md`: This file provides a detailed effort estimation for the backend development, broken down by feature. The total estimated effort is between 23 and 33 days.
*   `README.md`: A brief, high-level description of the project.
