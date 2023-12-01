<h1 align="center"> Docker </h1>

# Content

1. [Chapter 1: Introducing to Docker](#chapter1)
    - [Chapter 1 - Part 1: What is Docker?](#chapter1part1)
2. [Chapter 2: Create a Container in Docker](#chapter2)
    - [Chapter 2 - Part 1: How to Create a Postgres Database in Docker?](#chapter2part1)

## <a name="chapter1"></a>Chapter 1: Introducing to Docker
  
#### <a name="chapter1part1"></a>Chapter 1 - Part 1: What is Docker?

Java Spring Framework (Spring Framework) is a popular, open source, enterprise-level framework for creating standalone, production-grade applications that run on the Java Virtual Machine (JVM).

## <a name="chapter1"></a>Chapter 2: Create a Container in Docker
  
#### <a name="chapter2part1"></a>Chapter 2 - Part 1: How to Create a Postgres Database in Docker?

To use docker, first you will need to install it.

In Windows, you could install [Docker Desktop](https://docs.docker.com/desktop/install/windows-install/).

**Create a Dockerfile**

First, to start a Postgres database in a docker container, we have to create a Dockerfile.

Create the Dockerfile in a directory

<br>

<div align="center"><img src="img/dockerfile-w668-h104.png" width=668 height=104><br><sub>Dockerfile - (<a href='https://github.com/vitorstabile'>Work by Vitor Garcia</a>) </sub></div>

<br>

```
FROM postgres:15.1-alpine

LABEL author="Your Name"
LABEL description="Postgres Image for demo"
LABEL version="1.0"

COPY *.sql /docker-entrypoint-initdb.d/
```

Note that the line ```COPY``` below will copy all the sql files in our source folder, where we have our Dockerfile, and add them in the ```/docker-entrypoint-initdb.d/```

This folder in your Postgres container is where you can add additional initialization scripts (creating the directory if necessary).
