# Authentication

The CareFlow API uses token-based authentication to secure access to protected resources. Every request to a protected endpoint must include a valid access token in the HTTP Authorization header.

Requests without authentication — or with an invalid token — will be rejected.

---

## Authentication Method

CareFlow uses **Bearer token authentication** over HTTPS.

### Header format

Authorization: Bearer <access_token>

---

## Example Request

```http
GET /professionals HTTP/1.1
Host: api.careflow.dev
Authorization: Bearer cf_live_9f3a7b21c4e8d12a
Content-Type: application/json
```

---

## Token Lifecycle

Access tokens are issued by the CareFlow platform and are tied to a specific organization.

Tokens should be:

- Stored securely
- Never exposed in client-side code
- Rotated periodically

If a token is compromised, it should be revoked immediately.

---

## Authentication Errors

The API returns standard HTTP status codes for authentication failures.

### Unauthorized Request

**Status:** 401 Unauthorized

```json
{
  "error": "authentication_required",
  "message": "A valid access token must be provided."
}
```

### Invalid Token

**Status:** 403 Forbidden

```json
{
  "error": "invalid_token",
  "message": "The provided token is invalid or expired."
}
```

---

## Security Best Practices

- Always use HTTPS when making API requests
- Store tokens in secure server-side environments
- Avoid logging tokens in plaintext
- Rotate credentials regularly

Failure to follow security best practices may expose sensitive data.
