## 🔐 Authentication

### Register Doctor

```http
POST /auth/register/doctor
```

**Request Body**

```json
{
  "username": "string",
  "password": "string",
  "specialization": "string"
}
```

**Response Body**

```json
{
  "message": "Register doctor Successfully"
}
```

### Register User

```http
POST /auth/register/user
```

**Request Body**

```json
{
  "username": "string",
  "password": "string"
}
```

**Response Body**

```json
{
  "message": "Register user Successfully"
}
```

### Login (Doctor/User)

```http
POST /auth/login
```

**Request Body**

```json
{
  "username": "string",
  "password": "string",
  "role": "doctor" | "user"
}
```

**Response Body**

```json
{
    "id" : 1,
    "username" : "username",
    "role" : "doctor" | "user",
    "accessToken" : "token"

}
```

## 👤 User Management

### Get User Profile

```http
GET /users/me
```

**Response**

```json
{
  "id": "number",
  "username": "string"
}
```

### Update User Profile

```http
PATCH /users/me
```

**Request Body**

```json
{
  "username": "string",
  "password": "string"
}
```

**Response Body**

```json
{
    "id" : 1,
    "username" : "username",
    "role" : "doctor"| "user"
}
```

## 👨‍⚕️ Doctor Management

### Get Doctor Profile

```http
GET /doctors/me
```

**Response**

```json
{
  "id": "number",
  "username": "string",
  "specialization": "string"
}
```

```http
PATCH /doctors/me
```

**Request Body**

```json
{
  "username": "string",
  "password": "string"
}
```

**Response Body**

```json
{
    "id" : 1,
    "username" : "username",
    "role" : "doctor"| "user"
}
```

## 📊 Health Records

### Create Health Record

```http
POST /health-records
```

**Request Body**

```json
{
  "type": "string",
  "value": "string"
}
```

**Response Body**

```json
{
  "message": "create health record successfully"
}
```

### Get User's Health Records

```http
GET /health-records
```

**Query Parameters**

- `type`: กรองตามประเภท
- `from`: วันที่เริ่มต้น (YYYY-MM-DD)
- `to`: วันที่สิ้นสุด (YYYY-MM-DD)

**Response Body**

```json
[
  {
    "id": 1,
    "userId": 1,
    "type": "type",
    "value": "value",
    "date": "date"
  }
]
```

```http
GET /health-records/:id
```

**Query Parameters**

- `type`: กรองตามประเภท
- `from`: วันที่เริ่มต้น (YYYY-MM-DD)
- `to`: วันที่สิ้นสุด (YYYY-MM-DD)

**Response Body**

```json
{
  "id": 1,
  "userId": 1,
  "type": "type",
  "value": "value",
  "date": "date"
}
```

```http
PATCH /health-records/:id
```

**Request Body**

```json
{
  "type": "type",
  "value": "value"
}
```

**Response Body**

```json
{
  "id": 1,
  "userId": 1,
  "type": "type",
  "value": "value",
  "date": "date"
}
```

```http
DELETE /health-records/:id
```

**Response Body**

```json
{}
```

## 📝 Doctor Notes

### Create Note

```http
POST /doctor-notes
```

**Request Body**

```json
{
  "userId": "number",
  "note": "string"
}
```

**Response Body**

```json
{
  "message": "create doctor notes successfully"
}
```

### Get Notes (Doctor)

```http
GET /doctor-notes/my-notes
```

**Response Body**

```json
[
  {
    "id": 1,
    "doctorId": 1,
    "userId": 1,
    "Note": "Note",
    "createdAt": "date time"
  }
]
```

### Get Notes For Patient (Doctor)

```http
GET /doctor-notes/user/:userId
```

**Response Body**

```json
[
  {
    "id": 1,
    "doctorId": 1,
    "userId": 1,
    "Note": "Note",
    "createdAt": "date time"
  }
]
```

### Get Received Notes (User)

```http
GET /doctor-notes/received
```

**Response Body**

```json
[
  {
    "id": 1,
    "doctorId": 1,
    "userId": 1,
    "Note": "Note",
    "createdAt": "date time"
  }
]
```

```http
PATCH /doctor-notes/:id
```

**Request Body**

```json
{
  "note": "note"
}
```

**Response Body**

```json
{
  "id": 1,
  "doctorId": 1,
  "userId": 1,
  "note": "note",
  "createdAt": "Date Time"
}
```

```http
DELETE /doctor-notes/:id
```

**Response Body**

```json
{}
```

## ⚠️ Error Responses

### 401 Unauthorized

```json
{
  "error": "Authentication required"
}
```

### 403 Forbidden

```json
{
  "error": "You don't have permission to perform this action"
}
```

### 404 Not Found

```json
{
  "error": "Resource not found"
}
```
