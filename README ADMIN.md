# Documentation RESTful API System Booking Service Bike Admin

# Login
**Endpoint:** `/api/auth/login`  
**Method:** `POST`

### Request
```json
{
  "username": "admin",
  "password": "Admin123"
}
```

### Response Success - 200 OK
```json
{
  "status": "success",
  "message": "Login successful",
  "data": {
    "token": "JWT_Token_Admin"
  }
}
```
### Response Error - 400 Bad Request
```json
{
  "status": "error",
  "message": "Invalid username or password"
}
``` 
---
# Create Booking (Admin)
**Endpoint:** `/api/admin/bookings`  
**Method:** `POST`

### Header
Authorization: Bearer ADMIN_JWT_TOKEN


### Request
```json
{
  "userId": 5,
  "serviceId": 1,
  "bookingDate": "2025-01-20",
  "status": "CONFIRMED"
}
```
### Response Success - 201 Created
```json
{
  "status": "success",
  "message": "Booking created successfully",
  "data": {
    "bookingId": 10,
    "bookingDate": "2025-01-20",
    "status": "CONFIRMED",
    "service": {
      "id": 1,
      "serviceName": "Oil Change ",
      "price": 50000,
      "duration": 30
    }
  }
}
```

### Response Error - 400 Bad Request
```json
{
  "status": "error",
  "message": "Invalid booking data"
}
```
### Response Error - 401 Unauthorized
```json
{
  "status": "error",
  "message": "Unauthorized"
}
```
---
# Get All Booking (Admin)
**Endpoint:** `/api/admin/bookings`  
**Method:** `GET`

### Header
Authorization: Bearer ADMIN_JWT_TOKEN


### Response Success - 200 OK
```json
{
  "status": "success",
  "message": "Booking retrieved successfully",
  "data": [
    {
      "bookingId": 10,
      "bookingDate": "2025-01-20",
      "status": "CONFIRMED",
      "user": {
        "id": 5,
        "fullname": "Yanto Wardanto",
        "username": "Yanto"
      },
      "service": {
        "id": 1,
        "serviceName": "Ganti Oli",
        "price": 50000,
        "duration": 30
      }
    }
  ]
}
```

### Response Error - 401 Unauthorized
```json
{
  "status": "error",
  "message": "Unauthorized"
}
```

---
## Get Booking by ID (Admin)
**Endpoint:** `/api/admin/bookings/{bookingId}`  
**Method:** `GET`

### Header
Authorization: Bearer ADMIN_JWT_TOKEN

### Response Success - 200 OK
```json
{
  "status": "success",
  "message": "Booking retrieved successfully",
  "data": {
    "bookingId": 10,
    "bookingDate": "2025-01-20",
    "status": "CONFIRMED",
    "user": {
      "id": 5,
      "fullname": "Yanto Wardanto",
      "username": "Yanto",
      "email": "yanto@gmail.com"
    },
    "service": {
      "id": 1,
      "serviceName": "Ganti Oli",
      "price": 50000,
      "duration": 30
    }
  }
}
```
### Response Error - 404 Not Found
```json
{
  "status": "error",
  "message": "Booking not found"
}
```
---
# Get All Users (Admin)
**Endpoint:** `/api/admin/users`  
**Method:** `GET`

### Header
Authorization: Bearer ADMIN_JWT_TOKEN

### Response Success — 200 OK
```json
{
  "status": "success",
  "message": "Users retrieved successfully",
  "data": [
    {
      "id": 5,
      "fullname": "Yanto Wardanto",
      "username": "Yanto",
      "email": "yanto@gmail.com"
    }
  ]
}
```
---
## Update Booking Status to CANCELED (Admin)
**Endpoint:** `/api/admin/bookings/{bookingId}`  
**Method:** `PATCH`   
Allowed status values:
- CONFIRMED
- COMPLETED
- CANCELED


### Header
Authorization: Bearer ADMIN_JWT_TOKEN

### Request
```json
{
  "status": "CANCELED"
}
```

### Response Success - 200 OK
```json
{
  "status": "success",
  "message": "Booking has been canceled successfully",
  "data": {
    "bookingId": 10,
    "bookingDate": "2025-01-20",
    "status": "CANCELED"
  }
}
```

### Response Error - 400 Bad Request 
```json
{
  "status": "error",
  "message": "Invalid status transition"
}
```
### Response Error - 404 Not Found
```json
{
  "status": "error",
  "message": "Booking not found"
}
```
---
## Update Booking Status to COMPLETED (Admin)
**Endpoint:** `/api/admin/bookings/{bookingId}`  
**Method:** `PATCH`   

Allowed status values:
- CONFIRMED
- COMPLETED
- CANCELED

### Header
Authorization: Bearer ADMIN_JWT_TOKEN

### Request
```json
{
  "status": "COMPLETED"
}
```

### Response Success - 200 OK
```json
{
  "status": "success",
  "message": "Booking has been completed successfully",
  "data": {
    "bookingId": 10,
    "bookingDate": "2025-01-20",
    "status": "COMPLETED",
    "service": {
      "id": 1,
      "serviceName": "Oil Change",
      "price": 50000,
      "duration": 30
    }
  }
}
```

### Response Error - 400 Bad Request 
```json
{
  "status": "error",
  "message": "Invalid status transition"
}
```
### Response Error - 404 Not Found
```json
{
  "status": "error",
  "message": "Booking not found"
}
```

---
## Delete Booking (Admin)
**Endpoint:** `/api/admin/bookings/{bookingId}`  
**Method:** `DELETE`

### Header
Authorization: Bearer ADMIN_JWT_TOKEN

### Request
{}

---

### Response Success - 200 OK
```json
{
  "status": "success",
  "message": "Booking deleted successfully"
}
```

### Response Error - 400 Bad Request 
```json
{
  "status": "error",
  "message": "Booking cannot be deleted because it is already completed"
}
```
### Response Error - 401 Unauthorized 
```json
{
  "status": "error",
  "message": "Unauthorized"
}
```
### Response Error - 404 Not Found
```json
{
  "status": "error",
  "message": "Booking not found"
}
```
---
## Logout
**Endpoint:** `/api/auth/logout`  
**Method:** `POST`

### Header
Authorization: Bearer JWT_Token

### Request
```json
{}
```

### Response Success - 200 OK
```json
{
  "status": "success",
  "message": "Logout successful"
}
```

### Response Error - 401 Unauthorized
```json
{
  "status": "error",
  "message": "Unauthorized"
}
```






