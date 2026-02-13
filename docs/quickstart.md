# Quickstart Guide

This quickstart walks you through integrating with the CareFlow API in just a few minutes. By the end, you will authenticate, create a healthcare professional record, and retrieve it using command-line tools.

---

## Prerequisites

Before starting, ensure you have:

- A valid CareFlow API token
- `curl` installed on your system
- Internet access

All examples assume the base API endpoint:

```
https://api.careflow.dev/v1
```

---

## Step 1 — Set Your API Token

For convenience, store your API token in an environment variable.

### macOS / Linux

```bash
export CAREFLOW_TOKEN=YOUR_API_TOKEN
```

### Windows (PowerShell)

```powershell
setx CAREFLOW_TOKEN "YOUR_API_TOKEN"
```

Restart your terminal after setting the variable.

---

## Step 2 — Verify Authentication

Test that your token is valid by requesting the professionals list.

```bash
curl -X GET https://api.careflow.dev/v1/professionals \
  -H "Authorization: Bearer $CAREFLOW_TOKEN"
```

If authentication succeeds, you will receive either an empty array or existing records.

Example response:

```json
[]
```

If authentication fails:

```
401 Unauthorized
```

Verify your token and header format.

---

## Step 3 — Create a Healthcare Professional

Register a new professional in the system.

```bash
curl -X POST https://api.careflow.dev/v1/professionals \
  -H "Authorization: Bearer $CAREFLOW_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "fullName": "Dr. Emily Carter",
    "profession": "Physician",
    "licenseNumber": "MD-902134",
    "specialty": "Home Geriatric Care",
    "contact": {
      "email": "emily.carter@example.com",
      "phone": "+1-555-0198"
    },
    "location": {
      "city": "Boston",
      "state": "MA"
    },
    "availabilityStatus": "active"
  }'
```

Expected response:

```json
{
  "id": "prof_a17c29",
  "status": "created"
}
```

Save the returned `id` — you will use it next.

---

## Step 4 — Retrieve the Created Record

Replace the ID with the one returned above.

```bash
curl -X GET https://api.careflow.dev/v1/professionals/prof_a17c29 \
  -H "Authorization: Bearer $CAREFLOW_TOKEN"
```

Example response:

```json
{
  "id": "prof_a17c29",
  "fullName": "Dr. Emily Carter",
  "profession": "Physician",
  "specialty": "Home Geriatric Care",
  "availabilityStatus": "active"
}
```

---

## Step 5 — Update Availability

Modify an existing field.

```bash
curl -X PATCH https://api.careflow.dev/v1/professionals/prof_a17c29 \
  -H "Authorization: Bearer $CAREFLOW_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "availabilityStatus": "inactive"
  }'
```

---

## Step 6 — Clean Up (Optional)

Remove the record when testing is complete.

```bash
curl -X DELETE https://api.careflow.dev/v1/professionals/prof_a17c29 \
  -H "Authorization: Bearer $CAREFLOW_TOKEN"
```

Expected response:

```
204 No Content
```

---

## Next Steps

You are now successfully interacting with the CareFlow API. From here you can:

- Implement automated workflows
- Integrate with backend systems
- Build internal dashboards
- Extend professional management features

Refer to the full documentation for advanced usage, authentication details, and error handling.

---

You are ready to build with CareFlow.
