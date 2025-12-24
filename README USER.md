# Documentation RESTful API System Booking Service Bike User

# Register
**Endpoint:** `/api/auth/register`  
**Method:** `POST`

### Request
```json
{
  "fullname": "Yanto Wardanto",
  "username": "Yanto",
  "phone": "08111111111",
  "email": "yanto@gmail.com",
  "password": "Yanto123",
  "confirmPassword": "Yanto123"
}
```
## Response Success — 201 Created
``` json 
{
  "status": "success",
  "message": "Registration successful, please login"
}
``` 
## Response Error — 400 Bad Request
``` json 
{
  "status": "error",
  "message": "Registration failed, username or password cannot be empty"
}
``` 

---


# Login
**Endpoint:** `/api/auth/login`  
**Method:** `POST`

### Request
```json
{
  "username": "Yanto",
  "password": "Yanto123"
}
```

## Response Success — 200 OK

``` json 
{
  "status": "success",
  "message": "Login successful",
  "data": {
    "token":"JWT_Token_User"
  }
}
``` 

## Response Error — 400 Bad Request

``` json 
{
  "status": "error",
  "message": "Invalid username or password"
}
``` 
---

# Get Data Booking User
**Endpoint:** `/api/user/bookings`  
**Method:** `GET`

### Header
Authorization: Bearer JWT_Token_User

## Response Success — 200 OK
```json
{
  "status": "success",
  "message": "Booking date retrieved successfully",
  "data": [
    {
      "bookingId": 10,
      "bookingDate": "2025-01-20",
      "status": "CONFIRMED",
      "service": {
        "id": 1,
        "serviceName": "Oil Change",
        "price": 50000,
        "duration": 30
      }
    }
  ]
}
```
## Response Error — 404 Not Found
```json
{
  "status": "error",
  "message": "Data not found, please contact admin"
}
```
---

# Update Data Booking User
**Endpoint:** `/api/user/bookings/{id}`  
**Method:** `PATCH`

### Header
Authorization: Bearer JWT_Token_User

## Request
```json
{
  "bookingDate": "2025-01-30"
}
```

## Response Success — 200 OK
```json
{
  "status": "success",
  "message": "Booking date update successfully",
  "data": {
    "bookingId": 10,
    "bookingDate": "2025-01-30",
    "status": "CONFIRMED",
    "service": {
      "id": 1,
      "serviceName": "Oil Change",
      "price": 50000,
      "duration": 30
    }
  }
}
```

## Response Error — 400 Bad Request
```json
{
  "status": "error",
  "message": "Invalid input"
}
```
## Response Error — 401 Unauthorized
```json
{
  "status": "error",
  "message": "Unauthorized"
}
```
## Response Error — 403 Forbidden
```json
{
  "status": "error",
  "message": "Anda tidak memiliki akses untuk mengubah data ini"
}
```
## Response Error — 404 Not Found
```json
{
  "status": "error",
  "message": "Data booking tidak ditemukan"
}
```
---
# Cancel Booking User
**Endpoint:** `/api/user/bookings/{id}/cancel`  
**Method:** `PATCH`

### Header
Authorization: Bearer JWT_Token_User

### Request
```json
{}
```
### Response Success - 200 OK
```json
{
  "status": "success",
  "message": "Booking canceled successfully",
  "data": {
    "bookingId": 10,
    "status": "CANCELED"
  }
}
```
## Response Error — 400 Bad Request
```json
{
  "status": "error",
  "message": "Booking cannot be canceled"
}
```
## Response Error — 401 Unauthorized
```json
{
  "status": "error",
  "message": "Unauthorized"
}
```
## Response Error — 403 Forbidden
```json
{
  "status": "error",
  "message": "You are not allowed to cancel this booking"
}
```
## Response Error — 404 Not Found
```json
{
  "status": "error",
  "message": "Booking not found"
}
```


---

# Logout User
**Endpoint:** `/api/auth/logout`  
**Method:** `POST`

### Header
Authorization: Bearer JWT_Token_User


### Request
```json
{}
```

## Response Success - 200 OK
```json
{
  "status": "success",
  "message": "Logout successful"
}
```

## Response Error - 401 Unauthorized
```json
{
  "status": "error",
  "message": "Unauthorized"
}
```
