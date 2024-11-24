
# Web Service API Documentation

## Table of Contents
1. [Introduction](#introduction)
2. [Response Format](#response-format)
3. [Sample Responses](#sample-responses)
    - [Success Response](#1-success-response)
    - [Created Response](#2-created-response)
    - [Paginated Response](#3-paginated-response)
    - [Bad Request](#4-bad-request)
    - [Unauthorized](#5-unauthorized)
    - [Forbidden](#6-forbidden)
    - [Not Found](#7-not-found)
    - [Validation Error](#8-validation-error)
    - [Internal Server Error](#9-internal-server-error)
    - [Conflict](#10-conflict)
    - [Service Unavailable](#11-service-unavailable)

---

## Introduction
This document provides examples of the responses returned by the web service API. All responses follow a standard structure to ensure consistency and ease of integration.

---

## Response Format
Every API response includes:
- **`status`**: The HTTP status code of the response.
- **`message`**: A description of the response.
- **`data`** (if applicable): The content of the response, such as requested resources or additional details.
- **`error`** (if applicable): Information about an error if the request fails.

---

## Sample Responses

### **1. Success Response**
```json
{
  "status": 200,
  "message": "Request was successful.",
  "data": {
    "user_id": 12345,
    "name": "John Doe",
    "email": "johndoe@example.com",
    "created_at": "2023-01-15T12:34:56Z"
  }
}
```

---

### **2. Created Response**
```json
{
  "status": 201,
  "message": "Resource was successfully created.",
  "data": {
    "user_id": 12345,
    "name": "John Doe",
    "email": "johndoe@example.com"
  }
  "errors": {}
}
```

---

### **3. Paginated Response**
```json
{
  "status": 200,
  "message": "Data retrieved successfully.",
  "data": {
    "items": [
      {
        "id": 101,
        "name": "Product A",
        "description": "Description for Product A.",
        "price": 29.99
      },
      {
        "id": 102,
        "name": "Product B",
        "description": "Description for Product B.",
        "price": 49.99
      },
      {
        "id": 103,
        "name": "Product C",
        "description": "Description for Product C.",
        "price": 19.99
      }
    ],
    "pagination": {
      "current_page": 2,
      "per_page": 3,
      "total_pages": 5,
      "total_items": 15,
      "next_page": 3,
      "previous_page": 1
    }
  }
  "errors": {}
}
```

---

### **4. Bad Request**
```json
{
  "status": 400,
  "message": "Invalid request parameters. Please check the input.",
  "errors": {}
}
```

---

### **5. Unauthorized**
```json
{
  "status": 401,
  "message": "Authentication failed. Please provide valid credentials."
  "data": {}و
  "errors": {}
}
```

---

### **6. Forbidden**
```json
{
  "status": 403,
  "message": "You do not have permission to access this resource."
  "data": {}و
  "errors": {}
}
```

---

### **7. Not Found**
```json
{
  "status": 404,
  "message": "The requested resource was not found."
  "data": {}و
  "errors": {}
}
```

---

### **8. Validation Error**
```json
{
  "status": 422,
  "message": "Validation failed. Please correct the input and try again.",
  "errors": {
    "email": "The email field is required.",
    "password": "The password must be at least 8 characters."
  }
  "data": {}
}
```

---

### **9. Internal Server Error**
```json
{
  "status": 500,
  "message": "An unexpected error occurred. Please try again later."
  "data": {}
  "errors": {}
}
```

---

### **10. Conflict**
```json
{
  "status": 409,
  "message": "The request could not be completed due to a conflict. Resource already exists."
  "data": {}
}
```

---

### **11. Service Unavailable**
```json
{
  "status": 503,
  "message": "The server is currently unavailable. Please try again later."
  "data": {}
}
```

---

## Notes
- **Error Handling**: Always check for the `status` code to identify success or failure.
- **Pagination**: Ensure you use the `pagination` object to navigate through large datasets.

---
