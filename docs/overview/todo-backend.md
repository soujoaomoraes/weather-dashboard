# Backend Development - To-Do List (NestJS)

## Phase 1: Project Setup & Configuration

- [x] Set up monorepo structure with a `backend` directory.
- [x] Initialize NestJS project.
- [x] Install core dependencies.
- [ ] **[Current]** Install additional dependencies for database and authentication: `@nestjs/typeorm`, `typeorm`, `pg`, `redis`, `@nestjs/jwt`, `@nestjs/passport`, `passport`, `passport-jwt`, `bcrypt`.
- [ ] Configure environment variables (`.env` file).
- [ ] Set up TypeORM configuration for PostgreSQL.
- [ ] Set up Redis module for caching.

## Phase 2: Core Feature Implementation (NestJS Resources)

- [ ] Generate `users` resource (`nest g resource users`).
- [ ] Implement `User` entity (TypeORM model).
- [ ] Implement `UsersService` with CRUD operations (Create, Read).
- [ ] Implement `UsersController` with API endpoints (`POST /users`, `GET /users/:id`).
- [ ] Generate `auth` module (`nest g module auth`).
- [ ] Implement `AuthService` with JWT generation and user validation.
- [ ] Implement `JwtStrategy` for Passport.
- [ ] Secure endpoints using `AuthGuard`.

## Phase 3: User-Related Features

- [ ] Generate `user-settings` resource (`nest g resource user-settings`).
- [ ] Implement `UserSettings` entity and link to `User` (One-to-One).
- [ ] Implement `UserSettingsService` and `UserSettingsController` (CRUD).
- [ ] Generate `favorite-locations` resource (`nest g resource favorite-locations`).
- [ ] Implement `FavoriteLocation` entity and link to `User` (Many-to-One).
- [ ] Implement `FavoriteLocationsService` and `FavoriteLocationsController` (CRUD).

## Phase 4: External Service Integration

- [ ] Create a `Weather` module (`nest g module weather`).
- [ ] Implement `WeatherService` to fetch data from external APIs.
- [ ] Implement caching for weather data using the Redis module.
- [ ] Create `WeatherController` with an endpoint to get weather by location (e.g., `GET /weather?lat=...&lon=...`).

## Phase 5: Quality & Deployment

- [ ] Write unit tests for all services and controllers.
- [ ] Write E2E (end-to-end) tests for the main API flows.
- [ ] Configure structured logging (e.g., using `pino`).
- [ ] Create `Dockerfile` inside the `backend` directory.
- [ ] Update `docs/process/DEPLOYMENT.md` with NestJS-specific instructions.
