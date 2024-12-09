---
sidebar_position: 2
---

# Proposed Implementation

This page outlines the proposed implementation of Flower's API endpoints.

Although the proposed implementation is a microservices architecture, the **gateway service** presents a single entry point for all incoming requests. Each request is routed to the appropriate microservice based on the request path.

## Health

### `GET /users/health`

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

### `GET /core/health`

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

### `GET /notifications/health`

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

## Gateway Service -> User Microservice

### `POST /users/signup`

Create a user

Clients can interact with the user service's `/users/signup` endpoint via the gateway service which uses REST.

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

The gateway service interacts with the user service's `/users/signup` endpoint via [tRPC](https://trpc.io/). The request and response schemas are the same as above.

### `POST /users/login`

Log in a user

Clients can interact with the user service's `/users/login` endpoint via the gateway service which uses REST.

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

The gateway service interacts with the user service's `/users/login` endpoint via tRPC. The request and response schemas are the same as above.

### `POST /users/logout`

Log out a user

Clients can interact with the user service's `/users/logout` endpoint via the gateway service which uses REST.

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
  "error": "Internal Server Error"
}
```

The gateway service interacts with the user service's `/users/logout` endpoint via tRPC. The request and response schemas are the same as above.

### `GET /users/:id`

Get a user by their ID

Clients can interact with the user service's `/users/:id` endpoint via the gateway service which uses REST.

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

The gateway service interacts with the user service's `/users/:id` endpoint via tRPC. The request and response schemas are the same as above.

### `PUT /users/:id`

Update a user by their ID

Clients can interact with the user service's `/users/:id` endpoint via the gateway service which uses REST.

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

The gateway service interacts with the user service's `/users/:id` endpoint via tRPC. The request and response schemas are the same as above.

### `DELETE /users/:id`

Delete a user by their ID

Clients can interact with the user service's `/users/:id` endpoint via the gateway service which uses REST.

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
