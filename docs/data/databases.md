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

### Notification Service
