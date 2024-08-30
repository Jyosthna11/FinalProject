# Authentication API Documentation

## Base URL
`http://localhost:5454/auth`

## 1. Sign Up (User Registration)

### Endpoint
**`POST /signup`**

### Description
This endpoint allows a new user to register by providing their first name, last name, email, password, and other details. On successful registration, it returns an authentication token (JWT).

### Request Headers
- `Content-Type: application/json`

### Request Body (JSON)
```json
{
"firstName": "John",
"lastName": "Doe",
"email": "john.doe@example.com",
"password": "securepassword",
"role": "ROLE_USER",
"mobile": "1234567890"
}
```

### Required Fields

    firstName: String (Required)
    lastName: String (Required)
    email: String (Required, must be a valid email)
    password: String (Required, must be at least 8 characters)
    role: Enum/UserRole (Optional, e.g., ROLE_USER)
    mobile: String (Optional)

### Response
    Success (200 OK):
```json
{
    "jwt": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "status": true
}
```

### Error Responses:

    400 Bad Request: If any required field is missing or invalid.
    409 Conflict: If the email is already in use.

## 2. Sign In (User Login)
### Endpoint

**`POST /signin`**

### Description
This endpoint allows a registered user to sign in using their email and password. On successful login, it returns an authentication token (JWT).

### Request Headers
    Content-Type: application/json

### Request Body (JSON)
```json
{
    "email": "john.doe@example.com",
    "password": "securepassword"
}
```

### Required Fields
    email: String (Required, must be a valid email)
    password: String (Required, must be at least 8 characters)

### Response
    Success (200 OK):
```json
{
    "jwt": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "status": true
}
```

### Error Responses:
    400 Bad Request: If any required field is missing or invalid.
    401 Unauthorized: If the email or password is incorrect.
