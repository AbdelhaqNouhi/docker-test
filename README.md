## Docker

package software so it can run on any hardware


in order to understand how that process works there are three things
that you absolutely must  know 


**docker file:**  is a blueprint for building a docker image 

**image:**  is a template for running the docker container

**container:**  is a running process


## How to build a project 

*Create a docker file*

```bash
  mkdir Dockerfile
```

*Here's an example of a simple Dockerfile*


```bash
FROM node:16.16.0

WORKDIR /src

COPY package*.json ./
RUN npm install
COPY .  .

ENV PORT=3000
EXPOSE 3000
CMD ["npm", "start"]
```

**build a docker image and give the name of the image**

```bash
  docker build -t docker-image-express .
```

**run a docker image by running**

```bash
docker run -p 8000:3000 --name docker-express docker-image-express
```









## volumes 
is a dedicated folder on the host machine and insured 
this folder a container can create files that can be remounted into
future containers or multiple containers at the same time

## docker-compose
is a tool for running multiple docker containers 
at the same time 

*Create a docker-compose*

```bash
  mkdir docker-compose.yml
```

*Here's an example of a simple docker-compose*


```bash
version: '3'
services:
  web:
    build: .
    ports:
      - "3000:3000"
    depends_on:
      - db
  db:
    image: mongo
    environment:
      MONGO_USER: mongo
      MONGO_PASSWORD: password
```

**and now you can run this command**

```bash
  docker-compose up
```
#### now all the containers run together


*enjoy*