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