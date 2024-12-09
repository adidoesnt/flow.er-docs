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
  "_id": "ObjectId",
  "username": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "_id": "00000020f51bb4362eee2a4d",
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
  "_id": "ObjectId",
  "username": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "_id": "00000020f51bb4362eee2a4d",
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
  "id": "ObjectId",
  "username": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "_id": "00000020f51bb4362eee2a4d",
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
  "_id": "ObjectId",
  "username": "string",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "_id": "00000020f51bb4362eee2a4d",
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

---

## Gateway Service -> Core Microservice

### `GET /projects`

Get all projects the user is onboarded to

Clients can interact with the core service's `/projects` endpoint via the gateway service which uses REST.

**Success Response Schema**

```json
[
  {
    "id": "number",
    "name": "string",
    "created_by": "ObjectId",
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
    "created_by": "00000020f51bb4362eee2a4d",
    "created_at": "2023-03-01T00:00:00.000Z",
    "last_updated_at": "2023-03-01T00:00:00.000Z"
  },
  {
    "id": 2,
    "name": "project2",
    "created_by": "00000020f51bb4362eee2a4d",
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

The gateway service interacts with the core service's `/projects` endpoint via tRPC. The request and response schemas are the same as above.

### `POST /projects`

Create a project

Clients can interact with the core service's `/projects` endpoint via the gateway service which uses REST.

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
  "created_by": "ObjectId",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "id": 1,
  "name": "project1",
  "created_by": "00000020f51bb4362eee2a4d",
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

The gateway service interacts with the core service's `/projects` endpoint via tRPC. The request and response schemas are the same as above.

### `PUT /projects/:id`

Update a project by its ID

Clients can interact with the core service's `/projects/:id` endpoint via the gateway service which uses REST.

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
  "created_by": "ObjectId",
  "created_at": "timestamp",
  "last_updated_at": "timestamp"
}
```

**Success Response Example**

```json
{
  "id": 1,
  "name": "project1",
  "created_by": "00000020f51bb4362eee2a4d",
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

The gateway service interacts with the core service's `/projects/:id` endpoint via graphQL.

### `DELETE /projects/:id`

Delete a project by its ID

Clients can interact with the core service's `/projects/:id` endpoint via the gateway service which uses REST.

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

The gateway service interacts with the core service's `/projects/:id` endpoint via graphQL.

### `GET /projects/:id/users`

Get all users assigned to a project

Clients can interact with the core service's `/projects/:id/users` endpoint via the gateway service which uses REST.

The gateway service fetches the `onboardings` that reference the project's `id` from the core service, and then fetches the `user` that the `onboardings` reference from the user service.

**Success Response Schema**

```json
[
  {
    "_id": "ObjectId",
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
    "_id": "00000020f51bb4362eee2a4d",
    "username": "user1",
    "role": "user",
    "created_at": "2023-03-01T00:00:00.000Z",
    "last_updated_at": "2023-03-01T00:00:00.000Z"
  },
  {
    "_id": "00000020f51bb4362eee2a4e",
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

The gateway service interacts with the core service's `/projects/:id/users` endpoint via graphQL.

### `PUT /projects/:projectId/users/:userId`

Assign a user to a project

Clients can interact with the core service's `/projects/:projectId/users/:userId` endpoint via the gateway service which uses REST.

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

The gateway service interacts with the core service's `/projects/:projectId/users/:userId` endpoint via graphQL.

### `DELETE /projects/:projectId/users/:userId`

Unassign a user from a project

Clients can interact with the core service's `/projects/:projectId/users/:userId` endpoint via the gateway service which uses REST.

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

The gateway service interacts with the core service's `/projects/:projectId/users/:userId` endpoint via graphQL.

### `POST /projects/:id/todos`

Create a todo under a project

Clients can interact with the core service's `/projects/:id/todos` endpoint via the gateway service which uses REST.

**Request Schema**

```json
{
  "title": "string",
  "description": "string",
  "status": "string, optional"
}
```

**Request Example**

```json
{
  "title": "todo1",
  "description": "todo1 description",
  "status": "to_do"
}
```

**Success Response Schema**

```json
{
  "id": "number",
  "project": "number (project_id)",
  "created_by": "ObjectId",
  "title": "string",
  "description": "string",
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
  "created_by": "00000020f51bb4362eee2a4d",
  "title": "todo1",
  "description": "todo1 description",
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

The gateway service interacts with the core service's `/projects/:id/todos` endpoint via graphQL.

### `GET /projects/:id/todos`

Get all todos under a project

Clients can interact with the core service's `/projects/:id/todos` endpoint via the gateway service which uses REST.

**Success Response Schema**

```json
[
  {
    "id": "number",
    "project": "number (project_id)",
    "created_by": "ObjectId",
    "title": "string",
    "description": "string",
    "status": "string",
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
    "project": 1,
    "created_by": "00000020f51bb4362eee2a4d",
    "title": "todo1",
    "description": "todo1 description",
    "status": "to_do",
    "created_at": "2023-03-01T00:00:00.000Z",
    "last_updated_at": "2023-03-01T00:00:00.000Z"
  },
  {
    "id": 2,
    "project": 1,
    "created_by": "00000020f51bb4362eee2a4d",
    "title": "todo2",
    "description": "todo2 description",
    "status": "to_do",
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

The gateway service interacts with the core service's `/projects/:id/todos` endpoint via graphQL.

### `GET /todos/:id`

Get a todo by its ID

Clients can interact with the core service's `/todos/:id` endpoint via the gateway service which uses REST.

**Success Response Schema**

```json
{
  "id": "number",
  "project": "number (project_id)",
  "created_by": "ObjectId",
  "title": "string",
  "description": "string",
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
  "created_by": "00000020f51bb4362eee2a4d",
  "title": "todo1",
  "description": "todo1 description",
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

The gateway service interacts with the core service's `/todos/:id` endpoint via graphQL.

### `PUT /todos/:id`

Update a todo by its ID

Clients can interact with the core service's `/todos/:id` endpoint via the gateway service which uses REST.

**Request Schema**

```json
{
  "title": "string, optional",
  "description": "string, optional",
  "status": "string, optional"
}
```

**Success Response Schema**

```json
{
  "id": "number",
  "project": "number (project_id)",
  "created_by": "ObjectId",
  "title": "string",
  "description": "string",
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
  "created_by": "00000020f51bb4362eee2a4d",
  "title": "todo1",
  "description": "todo1 description",
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

The gateway service interacts with the core service's `/todos/:id` endpoint via graphQL.

### `DELETE /todos/:id`

Delete a todo by its ID

Clients can interact with the core service's `/todos/:id` endpoint via the gateway service which uses REST.

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

The gateway service interacts with the core service's `/todos/:id` endpoint via graphQL.

### `PUT /todos/:id/users/:userId`

Assign a user to a todo

Clients can interact with the core service's `/todos/:id/users/:userId` endpoint via the gateway service which uses REST.

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

The gateway service interacts with the core service's `/todos/:id/users/:userId` endpoint via graphQL.

### `DELETE /todos/:id/users/:userId`

Unassign a user from a todo

Clients can interact with the core service's `/todos/:id/users/:userId` endpoint via the gateway service which uses REST.

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

The gateway service interacts with the core service's `/todos/:id/users/:userId` endpoint via graphQL.

### `GET /todos/:id/users`

Get all users assigned to a todo

Clients can interact with the core service's `/todos/:id/users` endpoint via the gateway service which uses REST.

The gateway service fetches the `onboardings` that reference the todo's `id` from the core service, and then fetches the `user` that the `onboardings` reference from the user service.

**Success Response Schema**

```json
[
  {
    "_id": "ObjectId",
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
    "_id": "00000020f51bb4362eee2a4d",
    "username": "user1",
    "role": "user",
    "created_at": "2023-03-01T00:00:00.000Z",
    "last_updated_at": "2023-03-01T00:00:00.000Z"
  },
  {
    "_id": "00000020f51bb4362eee2a4e",
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

The gateway service interacts with the core service's `/projects/:id/users` endpoint via graphQL.

### `GET /todos/:id/comments`

Get all comments under a todo

Clients can interact with the core service's `/todos/:id/comments` endpoint via the gateway service which uses REST.

**Success Response Schema**

```json
[
  {
    "id": "number",
    "todo": "number (todo_id)",
    "author": "ObjectId",
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
    "author": "00000020f51bb4362eee2a4d",
    "content": "todo1 comment",
    "created_at": "2023-03-01T00:00:00.000Z",
    "last_updated_at": "2023-03-01T00:00:00.000Z"
  },
  {
    "id": 2,
    "todo": 1,
    "author": "00000020f51bb4362eee2a4e",
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

The gateway service interacts with the core service's `/todos/:id/comments` endpoint via graphQL.

### `PUT /comments/:id`

Update a comment by its ID

Clients can interact with the core service's `/comments/:id` endpoint via the gateway service which uses REST.

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
  "author": "ObjectId",
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
  "author": "00000020f51bb4362eee2a4d",
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

The gateway service interacts with the core service's `/comments/:id` endpoint via graphQL.

### `DELETE /comments/:id`

Delete a comment by its ID

Clients can interact with the core service's `/comments/:id` endpoint via the gateway service which uses REST.

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

The gateway service interacts with the core service's `/comments/:id` endpoint via graphQL.

## Gateway Service -> Notifications Microservice

### `POST /notifications`

Create a new notification.

**Request Schema**

```json
{
  "title": "string",
  "content": "string",
  "href": "string",
}
```

**Request Example**

```json
{
  "title": "New comment",
  "content": "This is a new comment",
  "href": "https://www.google.com",
}
```

**Response Schema**

```json
{
  "id": "string",
  "title": "string",
  "content": "string",
  "href": "string",
  "createdAt": "string",
  "updatedAt": "string",
}
```

**Response Example**

```json
{
  "id": "1",
  "title": "New comment",
  "content": "This is a new comment",
  "href": "https://www.google.com",
  "createdAt": "2023-01-01T00:00:00.000Z",
  "updatedAt": "2023-01-01T00:00:00.000Z",
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

The gateway service interacts with the core service's `/notifications` endpoint via tRPC.

### `GET /notifications`

Get all notifications for a user.

**Response Schema**

```json
[
  {
    "id": "string",
    "title": "string",
    "content": "string",
    "href": "string",
    "createdAt": "string",
    "updatedAt": "string",
  }
]
```
