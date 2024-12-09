---
sidebar_position: 1
---

# Databases

## Current Implementation

The current implementation of Flower uses a single PostgreSQL database to store all data.

## Proposed Implementation

The proposed implementation uses separate databases for the separate microservices:

### User Service

The user service was designed to independently deployable and decoupled from other services, so that it can be easily reused in other projects for authentication and authorisation.

It has two standalone tables: Users and Tokens (JWTs).

Since the token table is primarily a token blacklist where the tokens are stored until they expire, a lightweight in-memory [Redis](https://redis.io/) cache is used to store the tokens. Redis also make it easy to set expiry times on the tokens.

The user table is a standalone table that stores user details. Since no relational data is stored in this table, it is not necessary to use a relational database. Thus, the user table can be stored in a NoSQL database such as [MongoDB](https://www.mongodb.com/).

### Core Service

The core service handles the platform's core functionality, such as CRUD operations for projects, tasks, and other entities.

It has a number of tables, with each related to another in some way. Due to the relational nature of the data, a relational database (in this case, [PostgreSQL](https://www.postgresql.org/)) is used to store the data.

### Notification Service

The notification service handles sending notifications to users when certain events occur. Like the user service, it is designed to be independently deployable and decoupled from other services. For this reason, the data is stored in a separate database.

It has two tables, one for notifications and notification read statuses. Since the tables are related, a relational database (in this case, [PostgreSQL](https://www.postgresql.org/)) is used to store the data.

## What's next?

In the next section, we will look at diagrams that detail the database structure for both the current and proposed implementations of Flower.
