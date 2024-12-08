---
sidebar_position: 1
---

# Technology Stack

This page aims to introduce the technology stack used in Flower's backend.

## Current Implementation

The current implementation of Flower's backend is a monolithic application written in [Node.js](https://nodejs.org/en/) and [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript).

The technology stack is divided into two main parts:

1. Backend - The backend is developed using [Node.js](https://nodejs.org/en/) and [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript).
2. Database - The database selection is [PostgreSQL](https://www.postgresql.org/).

## Proposed Implementation

The proposed implementation of Flower's backend is a microservices architecture, with each service being responsible for a specific function.

The technology stack is divided into three main parts:

1. Backend - The backend is developed with a number of technologies, including:
   - [Node.js](https://nodejs.org/en/)
   - [TypeScript](https://www.typescriptlang.org/)
   - [Express](https://expressjs.com/)
   - [tRPC](https://trpc.io/)
   - [GraphQL](https://graphql.org/)
   - [Express Gateway](https://www.express-gateway.io/)
2. Database - The database selections include:
   - [PostgreSQL](https://www.postgresql.org/)
   - [MongoDB](https://www.mongodb.com/)
3. ORM/ODM - The object-relational mapping (ORM) and object-document mapping (ODM) libraries include:
   - [Prisma](https://www.prisma.io/)
   - [Mongoose](https://mongoosejs.com/)

## What's Next?

The architecture diagrams for the current and proposed implementations can be seen in the [next section](./architecure-diagram.md).
