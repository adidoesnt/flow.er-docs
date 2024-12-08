---
sidebar_position: 2
---

# Architecture

This page contains the current architecture diagram of Flower's backend, as well as a diagram of a proposed future architecture.

## Current Implementation

The current implementation of Flower's backend is a monolithic application written in [Node.js](https://nodejs.org/en/) and [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript).

### Diagram

The following diagram shows the current architecture of Flower's backend:

![Flower's Architecture Diagram](./img/flower-arch-diagram-legacy.png)

### Explaining the Architecture

lorem ipsum

### Pros and Cons

The pros of the current implementation are:

- The architecture is simple and easy to understand, making it easy to onboard new developers.
- The architecture can be developed quickly by a solo developer or small team of developers.
- There are fewer technologies to learn, which is less overwhelming for new developers.

Due to the current implementation being monolithic, it has a few cons:

- Different areas of functionality are not independently scalable, which can lead to performance issues.
- The architecture is not modular, which can make it difficult to develop new features or fix bugs.
- Since the application is not modular, developers cannot specialise in certain areas of functionality, which can lead to duplication of effort.

## Proposed Implementation

The proposed implementation of Flower's backend is a microservices architecture, with each service being responsible for a specific function.

### Diagram

The following diagram shows the proposed architecture of Flower's backend:

![Flower's Architecture Diagram](./img/flower-arch-diagram.png)

### Explaining the Architecture

#### Microservices

The proposed architecture splits existing backend service into **three** separate microservices:

1. **User Service** - Purely responsible for authentication, authorisation, and role-based access control.
   - The user service integrates with a [MongoDB](https://www.mongodb.com/) database to store user information. No relational information is required, so the more lightweight [MongoDB](https://www.mongodb.com/) is a natural choice.
   - It interfaces with the database using [Mongoose](https://mongoosejs.com/), a popular ODM (Object Document Mapping) library for MongoDB.
2. **Core Service** - Responsible for handling core functionality, such as CRUD operations for projects, tasks, and other entities.
   - The core service interfaces with a [PostgreSQL](https://www.postgresql.org/) database to store project and task information. Realtional information between projects, tasks and other entities is required, so [PostgreSQL](https://www.postgresql.org/) is a natural choice.
   - It interfaces with the database using [Prisma](https://www.prisma.io/), a popular ORM (Object Relational Mapping) library for PostgreSQL.
3. **Notification Service** - Responsible for sending notifications to users.
   - The notification service interfaces with a [PostgreSQL](https://www.postgresql.org/) database to store notification information.
   - It interfaces with the database using [Prisma](https://www.prisma.io/), a popular ORM (Object Relational Mapping) library for PostgreSQL.

These microservices are all developed independently in TypeScript, and communicate with each other via [tRPC](https://trpc.io/). tRPC felt like a natural fit for the proposed architecture, as all services are TypeScript-based. Using tRPC:

- The services can communicate via type-safe API calls, which makes it easier to develop new features or fix bugs.
- Most popular client-side frameworks, such as React and Angular, have tRPC integrations, which:
  - Makes it easy to develop a user interface for the application.
  - Ensure end-to-end type-safety, which is important for large-scale applications.

tRPC does have one main drawback which is its complex configuration process. It requires setting up a [tRPC server](https://trpc.io/docs/server) and a [tRPC client](https://trpc.io/docs/client) for each service. This can be a bit of a hassle, especially for smaller teams or for teams that are not familiar with tRPC.

#### Gateway Service

The proposed architecture also includes a **gateway** service, which acts as a single entry point for all incoming requests. This service is responsible for routing requests to the appropriate microservice based on the request path.

The gateway service is to be developed using [Express Gateway](https://www.express-gateway.io/). This was chosen in lieu of alternatives such as the AWS API Gateway for a few reasons:

- Express Gateway is a lightweight, open-source solution that is easy to use and integrate with other frameworks.
- Express Gateway is designed to be used with Express, which is the web framework used in the current implementation.
- AWS API Gateway would result in vendor lock-in, as it is a product from Amazon Web Services (AWS).

Using a **gateway** service like this has the following benefits:

- The gateway service can act as an orchestrator for the microservices, which makes it easier to manage and scale the application.
- The gateway service can use different protocols to communicate with each microservice, while allowing clients to use a single protocol. For example, the proposed gateway service uses:
  - tRPC to communicate with the user and notification services, to fetch non-relational or simple relational data.
  - GraphQL to communicate with the core service, to prevent over-fetching of complex relational data.
  - REST for incoming requests from clients, abstracting away complexity of using the various protocols to communicate with the microservices.

Using a **gateway** service like this also has the following drawbacks:

- The gateway service acts as a single point of failure, which can be challenging to manage.
- Using a gateway in between the client and the microservices can result in additional latency and overhead.

### Pros and Cons

The pros of the proposed implementation are:

- The architecture is modular, which makes it easier to develop new features or fix bugs.
- The architecture is scalable, as each service can be developed independently and scaled as needed.
- The architecture is easier to deliver in an efficient manner, as each service can be developed by a small, specialised team of developers.

Due to the proposed implementation being microservices, it has a few cons:

- The architecture is more complex than the current implementation, which can make it harder to understand.
- The architecture is more difficult to develop quickly, as it requires more planning and coordination.
- There are more technologies to learn, which can be overwhelming for new developers.

#### ORM/ODM Selection

For non-relational data, such as the user credentials, the proposed architecture uses [Mongoose](https://mongoosejs.com/).

The benefits of using Mongoose are:

- It abstracts away the complexity of the native MongoDB driver.
- Using libraries like TypeGoose, it can generate TypeScript types for the MongoDB models and provide type-safety at the repository level.

The drawbacks of using Mongoose are:

- It is a third-party library, and not directly maintained by the creators of MongoDB. In rare cases, this may result in compatibility issues.
- TypeGoose is not as mature as some other libraries, resulting in less community support.

For relational data, such as the project, task, and notification data, the proposed architecture uses [Prisma](https://www.prisma.io/).

The benefits of using Prisma are:

- It abstracts away the complexity of the native PostgreSQL driver.
- It provides a more intuitive API for interacting with the database.
- It provides type-safety at the repository level.
- It is a widely used library, with a large community and a lot of documentation.

The drawbacks of using Prisma are:

- It is a third-party library, and not directly maintained by the creators of PostgreSQL. In rare cases, this may result in compatibility issues.
- It stores generated types in the Node Modules directory, and can cause the directory to bliat significantly.

## Conclusion
