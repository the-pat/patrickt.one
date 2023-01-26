---
layout: post
title: "Building a Database Sandbox"
date: 2020-01-13 20:08 -0600
excerpt: Use docker as an alternative to the hassle of installing and configuring a database on your development machine.
---

This post is largely the result of:

1. **Jonathan Adams** ([@RebelActuary](https://twitter.com/RebelActuary)) and his wonderful [presentation over docker](https://github.com/PieceMaker/presentation-lsdg-docker)
2. **Alvise Susmel** ([@alvisesus](https://twitter.com/alvisesus)) and his blog post about using [Postgres and Docker](https://www.poeticoding.com/step-by-step-tutorial-to-build-a-phoenix-app-that-supports-user-uploads/#postgres-docker)

Thank you both.

## Database Sandbox

Rather than spending the time installing and configuring a database locally, start coding faster with _docker-compose_. Start a Postgres server with `docker-compose up -d`. Stop the server with `docker-compose down`.

```yml
# docker-compose.yml

version: "3"
services:
  db:
    image: postgres:11-alpine
    container_name: "postgres"
    ports:
      - "5432:5432"
    volumes:
      - postgres-dev:/var/lib/postgresql/data
    environment:
      - POSTGRES_PASSWORD=postgres
volumes:
  postgres-dev:
```

This file contains the settings outlined in the [Postgres and Docker](https://www.poeticoding.com/step-by-step-tutorial-to-build-a-phoenix-app-that-supports-user-uploads/#postgres-docker) post.

- **image**: this selects the version of Postgres to run,
- **container_name**: the name of the container,
- **ports**: the port mapping between the local machine and container,
- **volumes**: mounts the volume to the container to persist the data between runs,
- **environment**: sets the Postgres password as an environment variable

Hopefully this helps speed up your development speed!