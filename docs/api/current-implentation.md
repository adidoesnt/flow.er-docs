---
sidebar_position: 1
---

# Current Implementation

This page outlines the current implementation of Flower's API endpoints.

# Endpoints

## Health

### `GET /health`

Health check endpoint

    **Success Response Schema**
    ```json
    {
      "status": "string"
    }
    ```

    **Success Response Example**
    ```json
    {
      "status": "OK"
    }
    ```

    **Error Response Schema**
    ```json
    {
      "error": "string"
    }
    ```

    **Error Response Example**
    ```json
    {
      "error": "Internal Server Error"
    }
    ```

---

## Users

### `GET /users`

Get all users

    **Success Response Schema**
    ```json
    [
      {
        "id": "number",
        "username": "string",
        "created_at": "timestamp",
        "last_updated_at": "timestamp"
      }
    ]
    ```

    **Success Response Example**
    ```json
    [
      {
        "id": 1,
        "username": "user1",
        "created_at": "2023-03-01T00:00:00.000Z",
        "last_updated_at": "2023-03-01T00:00:00.000Z"
      },
      {
        "id": 2,
        "username": "user2",
        "created_at": "2023-03-01T00:00:00.000Z",
        "last_updated_at": "2023-03-01T00:00:00.000Z"
      }
    ]
    ```

    **Error Response Schema**
    ```json
    {
      "error": "string"
    }
    ```

    **Error Response Example**
    ```json
    {
      "error": "Unauthorised"
    }
    ```

### `GET /users/:id`

Get a user by their ID

    **Success Response Schema**
    ```json
    {
      "id": "number",
      "username": "string",
      "created_at": "timestamp",
      "last_updated_at": "timestamp"
    }
    ```

    **Success Response Example**
    ```json
    {
      "id": 1,
      "username": "user1",
      "created_at": "2023-03-01T00:00:00.000Z",
      "last_updated_at": "2023-03-01T00:00:00.000Z"
    }
    ```

    **Error Response Schema**
    ```json
    {
      "error": "string"
    }
    ```

    **Error Response Example**
    ```json
    {
      "error": "Internal Server Error"
    }
    ```

### `POST /users/signup`

Create a user

    **Request Schema**
    ```json
    {
      "username": "string",
      "password": "string"
    }
    ```

    **Request Example**
    ```json
    {
        "username": "user1",
        "password": "password1"
    }
    ```

    **Success Response Schema**
    ```json
    {
      "id": "number",
      "username": "string",
      "created_at": "timestamp",
      "last_updated_at": "timestamp"
    }
    ```

    **Success Response Example**
    ```json
    {
      "id": 1,
      "username": "user1",
      "created_at": "2023-03-01T00:00:00.000Z",
      "last_updated_at": "2023-03-01T00:00:00.000Z"
    }
    ```

    **Error Response Schema**
    ```json
    {
      "error": "string"
    }
    ```

    **Error Response Example**
    ```json
    {
      "error": "Internal Server Error"
    }
    ```

### `POST /users/login`

Log in a user

    **Request Schema**
    ```json
    {
      "username": "string",
      "password": "string"
    }
    ```

    **Request Example**
    ```json
    {
        "username": "user1",
        "password": "password1"
    }
    ```

    **Success Response Schema**
    ```json
    {
      "id": "number",
      "username": "string",
      "created_at": "timestamp",
      "last_updated_at": "timestamp"
    }
    ```

    **Success Response Example**
    ```json
    {
      "id": 1,
      "username": "user1",
      "created_at": "2023-03-01T00:00:00.000Z",
      "last_updated_at": "2023-03-01T00:00:00.000Z"
    }
    ```

    **Error Response Schema**
    ```json
    {
      "error": "string"
    }
    ```

    **Error Response Example**
    ```json
    {
      "error": "Incorrect password!"
    }
    ```
### `POST /users/logout`

Log out a user

    **Response Schema**
    ```json
    {
      "status": "string"
    }
    ```

    **Success Response Example**
    ```json
    {
      "status": "OK"
    }
    ```

    **Error Response Schema**
    ```json
    {
      "error": "string"
    }
    ```

    **Error Response Example**
    ```json
    {
      "error": "Unauthorised"
    }
    ```

### `PUT /users/:id`

Update a user by their ID

    **Request Schema**
    ```json
    {
      "username": "string, optional",
      "password": "string, optional"
    }
    ```

    **Success Response Schema**
    ```json
    {
      "id": "number",
      "username": "string",
      "created_at": "timestamp",
      "last_updated_at": "timestamp"
    }
    ```

    **Error Response Schema**
    ```json
    {
      "error": "string"
    }
    ```

    **Error Response Example**
    ```json
    {
      "error": "Unauthorised"
    }
    ```

### `DELETE /users/:id`

Delete a user by their ID

    **Response Schema**
    ```json
    {
      "status": "string"
    }
    ```

    **Success Response Example**
    ```json
    {
      "status": "OK"
    }
    ```

    **Error Response Schema**
    ```json
    {
      "error": "string"
    }
    ```

    **Error Response Example**
    ```json
    {
      "error": "Unauthorised"
    }
    ```

---
