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
    "role": "string",
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
    "role": "user",
    "created_at": "2023-03-01T00:00:00.000Z",
    "last_updated_at": "2023-03-01T00:00:00.000Z"
  },
  {
    "id": 2,
    "username": "user2",
    "role": "admin",
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
  "role": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "id": 1,
  "username": "user1",
  "role": "user",
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
  "password": "string",
  "role": "string, optional"
}
```

**Request Example**

```json
{
  "username": "user1",
  "password": "password1",
  "role": "user"
}
```

**Success Response Schema**

```json
{
  "id": "number",
  "username": "string",
  "role": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "id": 1,
  "username": "user1",
  "role": "user",
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
  "role": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "id": 1,
  "username": "user1",
  "role": "user",
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
  "password": "string, optional",
  "role": "string, optional"
}
```

**Success Response Schema**

```json
{
  "id": "number",
  "username": "string",
  "role": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "id": 1,
  "username": "user1",
  "role": "user",
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

## Projects

### `GET /projects`

Get all projects

This endpoint is only accessible to admins.

**Success Response Schema**

```json
[
  {
    "id": "number",
    "name": "string",
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
    "name": "project1",
    "created_at": "2023-03-01T00:00:00.000Z",
    "last_updated_at": "2023-03-01T00:00:00.000Z"
  },
  {
    "id": 2,
    "name": "project2",
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

### `GET /projects/:id`

Get a project by their ID

**Success Response Schema**

```json
{
  "id": "number",
  "name": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "id": 1,
  "name": "project1",
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
  "error": "Unauthorised"
}
```

### `POST /projects`

Create a project

**Request Schema**

```json
{
  "name": "string"
}
```

**Request Example**

```json
{
  "name": "project1"
}
```

**Success Response Schema**

```json
{
  "id": "number",
  "name": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "id": 1,
  "name": "project1",
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
  "error": "Unauthorised"
}
```

### `PUT /projects/:id`

Update a project by their ID

**Request Schema**

```json
{
  "name": "string, optional"
}
```

**Success Response Schema**

```json
{
  "id": "number",
  "name": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "id": 1,
  "name": "project1",
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
  "error": "Unauthorised"
}
```

### `DELETE /projects/:id`

Delete a project by their ID

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

### `GET /projects/:id/users`

Get all users assigned to a project

**Success Response Schema**

```json
[
  {
    "id": "number",
    "username": "string",
    "role": "string",
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
    "role": "user",
    "created_at": "2023-03-01T00:00:00.000Z",
    "last_updated_at": "2023-03-01T00:00:00.000Z"
  },
  {
    "id": 2,
    "username": "user2",
    "role": "admin",
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

### `PUT /projects/:projectId/users/:userId`

Assign a user to a project

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
  "error": "Unauthorised"
}
```

### `DELETE /projects/:projectId/users/:userId`

Unassign a user from a project

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

### `POST /projects/:id/todos`

Create a todo under a project

**Request Schema**

```json
{
  "title": "string",
  "description": "string",
  "assignee": "number (user_id), optional",
  "status": "string, optional"
}
```

**Request Example**

```json
{
  "title": "todo1",
  "description": "todo1 description",
  "assignee": 1,
  "status": "to_do"
}
```

**Success Response Schema**

```json
{
  "id": "number",
  "project": "number (project_id)",
  "title": "string",
  "description": "string",
  "assignee": "number (user_id)",
  "status": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "id": 1,
  "project": 1,
  "title": "todo1",
  "description": "todo1 description",
  "assignee": 1,
  "status": "to_do",
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

---

## Todos

### `GET /todos/:id`

Get a todo by its ID

**Success Response Schema**

```json
{
  "id": "number",
  "project": "number (project_id)",
  "title": "string",
  "description": "string",
  "assignee": "number (user_id)",
  "status": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "id": 1,
  "project": 1,
  "title": "todo1",
  "description": "todo1 description",
  "assignee": 1,
  "status": "to_do",
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

### `PUT /todos/:id`

Update a todo by its ID

**Request Schema**

```json
{
  "title": "string, optional",
  "description": "string, optional",
  "assignee": "number (user_id), optional",
  "status": "string, optional"
}
```

**Success Response Schema**

```json
{
  "id": "number",
  "project": "number (project_id)",
  "title": "string",
  "description": "string",
  "assignee": "number (user_id)",
  "status": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "id": 1,
  "project": 1,
  "title": "todo1",
  "description": "todo1 description",
  "assignee": 1,
  "status": "to_do",
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
  "error": "Unauthorised"
}
```

### `DELETE /todos/:id`

Delete a todo by its ID

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

### `POST /todos/:id/comments`

Create a comment under a todo

**Request Schema**

```json
{
  "content": "string",
  "author": "number (user_id)"
}
```

**Request Example**

```json
{
  "content": "todo1 comment",
  "author": 1
}
```

**Success Response Schema**

```json
{
  "id": "number",
  "todo": "number (todo_id)",
  "author": "number (user_id)",
  "content": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "id": 1,
  "todo": 1,
  "author": 1,
  "content": "todo1 comment",
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
  "error": "Unauthorised"
}
```

### `GET /todos/:id/comments`

Get all comments under a todo

**Success Response Schema**

```json
[
  {
    "id": "number",
    "todo": "number (todo_id)",
    "author": "number (user_id)",
    "content": "string",
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
    "todo": 1,
    "author": 1,
    "content": "todo1 comment",
    "created_at": "2023-03-01T00:00:00.000Z",
    "last_updated_at": "2023-03-01T00:00:00.000Z"
  },
  {
    "id": 2,
    "todo": 1,
    "author": 2,
    "content": "todo1 comment 2",
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

---

## Comments

### `PUT /comments/:id`

Update a comment by its ID

**Request Schema**

```json
{
  "content": "string, optional"
}
```

**Success Response Schema**

```json
{
  "id": "number",
  "todo": "number (todo_id)",
  "author": "number (user_id)",
  "content": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "id": 1,
  "todo": 1,
  "author": 1,
  "content": "todo1 comment",
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
  "error": "Unauthorised"
}
```

### `DELETE /comments/:id`

Delete a comment by its ID

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
