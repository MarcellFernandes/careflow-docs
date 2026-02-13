# Professionals

The Professionals resource represents licensed healthcare providers registered within the CareFlow platform. Organizations use this resource to manage professional records, credentials, and availability.

All professional data must comply with internal validation and healthcare data integrity rules.

---

## Create Professional

Creates a new healthcare professional record.

### Endpoint

POST /professionals

---

### Request Body

```json
{
  "fullName": "Dr. Maria Santos",
  "licenseNumber": "NY-458921",
  "profession": "Physician",
  "specialty": "Geriatrics",
  "contact": {
    "email": "maria.santos@example.com",
    "phone": "+1-212-555-0198"
  },
  "location": {
    "city": "New York",
    "state": "NY"
  },
  "availabilityStatus": "active"
}
```

---

### Field Descriptions

| Field              | Type   | Description                                         |
| ------------------ | ------ | --------------------------------------------------- |
| fullName           | string | Legal name of the professional                      |
| licenseNumber      | string | Government-issued professional license              |
| profession         | string | Healthcare role (e.g., Physician, Nurse, Therapist) |
| specialty          | string | Area of clinical specialization                     |
| contact.email      | string | Primary professional email                          |
| contact.phone      | string | Professional phone number                           |
| location.city      | string | Service city                                        |
| location.state     | string | Service state                                       |
| availabilityStatus | string | active, inactive, or suspended                      |

---

### Validation Rules

- License number must be unique
- Email must follow RFC format
- Required fields cannot be empty
- Availability status must be a valid enum value

---

### Success Response

**201 — Created**

```json
{
  "id": "prof_839201",
  "status": "created"
}
```

---

### Possible Errors

- 400 — Invalid input data
- 409 — Duplicate license number
- 401 — Unauthorized

---

## Retrieve Professional

Fetches a single professional record.

### Endpoint

GET /professionals/{id}

---

### Success Response

**200 — OK**

```json
{
  "id": "prof_839201",
  "fullName": "Dr. Maria Santos",
  "licenseNumber": "NY-458921",
  "profession": "Physician",
  "specialty": "Geriatrics",
  "contact": {
    "email": "maria.santos@example.com",
    "phone": "+1-212-555-0198"
  },
  "location": {
    "city": "New York",
    "state": "NY"
  },
  "availabilityStatus": "active"
}
```

---

## List Professionals

Returns a paginated list of professionals.

### Endpoint

GET /professionals

---

### Query Parameters

| Parameter          | Type    | Description                |
| ------------------ | ------- | -------------------------- |
| profession         | string  | Filter by healthcare role  |
| specialty          | string  | Filter by specialty        |
| city               | string  | Filter by service location |
| availabilityStatus | string  | Availability filter        |
| page               | integer | Pagination index           |
| limit              | integer | Results per page           |

---

### Example Request

```
GET /professionals?profession=Physician&city=New York&page=1&limit=20
```

---

### Success Response

**200 — OK**

```json
{
  "page": 1,
  "limit": 20,
  "total": 142,
  "data": [
    {
      "id": "prof_839201",
      "fullName": "Dr. Maria Santos",
      "profession": "Physician",
      "specialty": "Geriatrics",
      "location": {
        "city": "New York",
        "state": "NY"
      },
      "availabilityStatus": "active"
    }
  ]
}
```

---

## Update Professional

Updates an existing professional record.

### Endpoint

PATCH /professionals/{id}

---

### Example Request

```json
{
  "availabilityStatus": "inactive"
}
```

---

### Success Response

**200 — OK**

```json
{
  "id": "prof_839201",
  "status": "updated"
}
```

---

## Delete Professional

Removes a professional record.

### Endpoint

DELETE /professionals/{id}

---

### Success Response

**204 — No Content**

No response body returned.

---

## Best Practices

- Validate licensing information before submission
- Use pagination when listing large datasets
- Handle duplicate records gracefully
- Cache read operations when appropriate

Proper management of professional data ensures reliable healthcare workflows within the CareFlow ecosystem.
