# API Endpoints

This document outlines the available API endpoints.

## Authentication

All endpoints require authentication. See `authentication.md` for details.

---

## Users

### `POST /users`

-   **Description:** Creates a new user.
-   **Request Body:**
    ```json
    {
        "username": "string",
        "email": "string",
        "password": "string"
    }
    ```
-   **Response (201 Created):**
    ```json
    {
        "id": "integer",
        "username": "string",
        "email": "string",
        "created_at": "datetime"
    }
    ```

### `GET /users/{id}`

-   **Description:** Retrieves a user by their ID.
-   **Response (200 OK):**
    ```json
    {
        "id": "integer",
        "username": "string",
        "email": "string",
        "created_at": "datetime"
    }
    ```

---

## User Settings

### `GET /users/{userId}/settings`

-   **Description:** Retrieves the settings for a specific user.
-   **Response (200 OK):**
    ```json
    {
        "units": "string ('metric' or 'imperial')",
        "dark_mode_enabled": "boolean"
    }
    ```

### `PUT /users/{userId}/settings`

-   **Description:** Updates the settings for a specific user.
-   **Request Body:**
    ```json
    {
        "units": "string ('metric' or 'imperial')",
        "dark_mode_enabled": "boolean"
    }
    ```
-   **Response (200 OK):**
    ```json
    {
        "units": "string",
        "dark_mode_enabled": "boolean"
    }
    ```

---

## Favorite Locations

### `GET /users/{userId}/locations`

-   **Description:** Retrieves all favorite locations for a specific user.
-   **Response (200 OK):**
    ```json
    [
        {
            "id": "integer",
            "city_name": "string",
            "latitude": "float",
            "longitude": "float"
        }
    ]
    ```

### `POST /users/{userId}/locations`

-   **Description:** Adds a new favorite location for a user.
-   **Request Body:**
    ```json
    {
        "city_name": "string",
        "latitude": "float",
        "longitude": "float"
    }
    ```
-   **Response (201 Created):**
    ```json
    {
        "id": "integer",
        "city_name": "string",
        "latitude": "float",
        "longitude": "float"
    }
    ```

### `DELETE /users/{userId}/locations/{locationId}`

-   **Description:** Removes a favorite location for a user.
-   **Response (204 No Content):**
