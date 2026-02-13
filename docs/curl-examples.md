# cURL Examples

This section demonstrates how to interact with the CareFlow API using `curl`. These examples simulate real-world usage scenarios, including authentication, creating records, and retrieving data.

All examples assume:

- Base URL: `https://api.careflow.dev/v1`
- A valid Bearer token is available

Replace `YOUR_API_TOKEN` with your actual token before running the commands.

---

## Authentication Header Template

All protected endpoints require an Authorization header:

```bash
-H "Authorization: Bearer YOUR_API_TOKEN"
```

---

## Create a Healthcare Professional

Registers a new healthcare professional.

```bash
curl -X POST https://api.careflow.dev/v1/professionals \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "fullName": "Dr. Sarah Mitchell",
    "profession": "Physician",
    "licenseNumber": "MD-458721",
    "specialty": "Geriatric Care",
    "contact": {
      "email": "sarah.mitchell@example.com",
      "phone": "+1-555-0142"
    },
    "location": {
      "city": "Chicago",
      "state": "IL"
    },
    "availabilityStatus": "active"
  }'
```

Expected response:

```json
{
  "id": "prof_8f29a1",
  "status": "created"
}
```

---

## List Healthcare Professionals

Retrieves all registered professionals.

```bash
curl -X GET https://api.careflow.dev/v1/professionals \
  -H "Authorization: Bearer YOUR_API_TOKEN"
```

Example response:

```json
[
  {
    "id": "prof_8f29a1",
    "fullName": "Dr. Sarah Mitchell",
    "profession": "Physician",
    "specialty": "Geriatric Care",
    "location": {
      "city": "Chicago",
      "state": "IL"
    }
  }
]
```

---

## Filter Professionals by Specialty

Query professionals by specialty.

```bash
curl -X GET "https://api.careflow.dev/v1/professionals?specialty=Geriatric%20Care" \
  -H "Authorization: Bearer YOUR_API_TOKEN"
```

---

## Retrieve a Single Professional

Fetch detailed information about one professional.

```bash
curl -X GET https://api.careflow.dev/v1/professionals/prof_8f29a1 \
  -H "Authorization: Bearer YOUR_API_TOKEN"
```

---

## Update Professional Information

Modify an existing record.

```bash
curl -X PATCH https://api.careflow.dev/v1/professionals/prof_8f29a1 \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "availabilityStatus": "inactive"
  }'
```

---

## Delete a Professional Record

Remove a professional from the system.

```bash
curl -X DELETE https://api.careflow.dev/v1/professionals/prof_8f29a1 \
  -H "Authorization: Bearer YOUR_API_TOKEN"
```

Expected response:

```
204 No Content
```

---

## Troubleshooting

If authentication fails:

```
401 Unauthorized
```

Verify:

- Authorization header format
- Token validity
- Token expiration

---

## Best Practices

- Always send JSON payloads with `Content-Type: application/json`.
- Protect API tokens — never commit them to version control.
- Test endpoints incrementally when debugging requests.

---

These examples provide a practical starting point for integrating with the CareFlow API using command-line tools.
