### DOCKER
slide: https://projects.100xdevs.com/tracks/docker-2/docker-2-1

- npm is a registry to push node.js code

- install docker
- docker run mongo

- run this cmd to make docker run locally
- docker run -p 27017:27017 mongo (port mapping)
- open compass and you can connect to the database

- docker images
- docker rmi mongo --force (remove mongo)

Image: everything needed to run that software
- when I run is when I start a container
- when I start the image then I start a container (but even when I'm not running it, I still have the images)
- docker ps (containers)

- images is like cloning the codebase and containers is like running the codebase

- image: complete package of a software
- container: when you're running that software locally

PORT MAPPING

- docker run -p 5432:5432 postgres
- secong thing depends on the image container, first thing depends on you which port of your machine do you want to expose it on

- docker exec -it container_id sh (run shell inside the container)

# How to containerize a node.js
- node-js-project-container (folder name)
- create a Dockerfile
- we can only have one CMD

- docker build -t hello-world-app .
- docker run -p 3000:3000 hello-world-app
to stop, kill it

- if you get error (permission denied) run following cmds
- sudo usermod -aG docker $USER
- newgrp docker

- passing env variable
console.log("ENV VARIABLE")
console.log(process.env.DATABASE_URL)

# Pushing to dockerhub
- docker tag hello-world-app <your-dockerhub-username>/hello-world-app:latest
- docker push <your-dockerhub-username>/hello-world-app:latest

```Dockerfile

FROM node:22-alpine

WORKDIR /app

COPY . .

RUN npm install

EXPOSE 3000

CMD ["node", "index.js"]

```
