# Authentication

The API uses JSON Web Tokens (JWT) for authentication. Every request to a protected endpoint must include a `Authorization` header with a valid JWT.

## Token Generation

1.  The user authenticates via the `POST /login` endpoint (to be defined) by providing their email and password.
2.  If the credentials are valid, the server generates a JWT signed with a secret key.
3.  The token is returned to the client.

## Token Usage

The client must include the token in the `Authorization` header for all subsequent requests to protected endpoints:

```
Authorization: Bearer <token>
```

## Token Payload (Example)

```json
{
  "userId": 123,
  "username": "example_user",
  "iat": 1678886400,
  "exp": 1678890000
}
```
- `userId`: The user's unique identifier.
- `username`: The user's username.
- `iat`: (Issued At) The timestamp when the token was generated.
- `exp`: (Expiration Time) The timestamp when the token will expire.
