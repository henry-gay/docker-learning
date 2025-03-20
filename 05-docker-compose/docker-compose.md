# Docker Compose Guide

## Introduction

Docker Compose allows you to define and manage multi-container applications using a YAML configuration file called `docker-compose.yml`. This guide covers the basics of setting up a multi-container application using Docker Compose.

## Why Use Docker Compose?

Using `docker run` commands to set up multiple containers can be complex and hard to maintain. Docker Compose simplifies this by storing configuration details in a YAML file, making deployment and management easier.

## Example: Voting Application

A sample voting application consists of:

- **Voting App** (Python) – Web interface for voting.
- **Redis** – In-memory database for temporary vote storage.
- **Worker** (.NET) – Processes votes and updates the database.
- **PostgreSQL** – Stores vote counts.
- **Result App** (Node.js) – Displays voting results.

## Setting Up Services with Docker Compose

A typical `docker-compose.yml` file for this application looks like this:

```yaml
version: '3'

services:
  redis:
    image: redis:latest
    container_name: redis

  db:
    image: postgres:latest
    container_name: db

  vote:
    image: voting-app
    container_name: vote
    ports:
      - "5000:80"
    depends_on:
      - redis

  result:
    image: results-app
    container_name: result
    ports:
      - "5001:80"
    depends_on:
      - db

  worker:
    image: worker-app
    container_name: worker
    depends_on:
      - redis
      - db
```

## Running the Application

To start the entire application stack:

```sh
docker-compose up -d
```

This command runs all services in detached mode.

To stop the application:

```sh
docker-compose down
```

## Building Custom Images

If some services need to be built locally, use the `build` directive:

```yaml
vote:
  build: ./vote
```

Docker Compose will build the image from the `Dockerfile` inside the `vote` directory before starting the container.

## Networking in Docker Compose

You can define networks to separate different parts of your application:

```yaml
networks:
  frontend:
  backend:
```

Assign networks to services:

```yaml
services:
  vote:
    networks:
      - frontend
      - backend
  redis:
    networks:
      - backend
```

## **Installation**

1. Clone the repository:
```
git clone https://github.com/dockersamples/example-voting-app
cd example-voting-app
```

## Conclusion

Docker Compose simplifies multi-container application management by defining configurations in a single file. By using networks, dependencies, and build instructions, you can efficiently deploy and maintain complex applications.

