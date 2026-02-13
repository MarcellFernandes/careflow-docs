# Error Handling

The CareFlow API uses conventional HTTP status codes to indicate the success or failure of a request. When an error occurs, the API returns a structured JSON response describing what went wrong.

Clients should always inspect both the HTTP status code and the response body to properly handle failures.

---

## Error Response Format

All errors follow a consistent structure:

```json
{
  "error": "error_code",
  "message": "Human-readable description of the error."
}
```

- **error** — machine-readable identifier
- **message** — explanation intended for developers

---

## HTTP Status Codes

### 400 — Bad Request

The request is malformed or contains invalid parameters.

```json
{
  "error": "invalid_request",
  "message": "One or more request parameters are invalid."
}
```

---

### 401 — Unauthorized

Authentication credentials are missing.

```json
{
  "error": "authentication_required",
  "message": "A valid access token must be provided."
}
```

---

### 403 — Forbidden

Authentication succeeded, but the token lacks permission.

```json
{
  "error": "insufficient_permissions",
  "message": "You do not have access to this resource."
}
```

---

### 404 — Not Found

The requested resource does not exist.

```json
{
  "error": "resource_not_found",
  "message": "The requested professional could not be found."
}
```

---

### 409 — Conflict

The request conflicts with the current state of the resource.

```json
{
  "error": "resource_conflict",
  "message": "A professional with this identifier already exists."
}
```

---

### 429 — Too Many Requests

Rate limits have been exceeded.

```json
{
  "error": "rate_limit_exceeded",
  "message": "Too many requests. Please try again later."
}
```

---

### 500 — Internal Server Error

An unexpected error occurred on the server.

```json
{
  "error": "internal_error",
  "message": "An unexpected error occurred. Please try again."
}
```

---

## Best Practices for Error Handling

- Always check the HTTP status code
- Parse the error object for actionable information
- Implement retries for transient failures
- Respect rate limit responses

Proper error handling improves system reliability and user experience.
