slide: https://projects.100xdevs.com/tracks/docker-2/docker-2-1

# Why do you need docker, what does it provide??
- when you want to build a full stack application where you have a lot of contributors, its always good to containerize it because whenever a new developer joins the team they can run the project in the single command.

# Containeraization
- if you have a big machine you can run mini containers inside the machine. Its not similar to vms (virtual machines)

- docker build cmd lets you create an image
- learn to write Dockerfile

- all docker images have alpine version which is a slightly thinner image
- node:22 is also fine but node:22-alpine is a slightly thinner version

- if I have node and golang project then start from golang base image and write the steps to install node and vice versa

# Layers in Docker

# Assignment
- optimize the dockerfile in such a way that when I change th source code and do docker run build somehow the npm install should be cached because package.json does not changed
- Solution: copy package.json then run npm install

# Network and Volumes
- if you want even if the container dies data should live - volumes is the solution

- docker volume create mongo_db_data
- docker run -p 27017:27017 -v mongo_db_data:/data/db mongo

- open compass and connect. add some data

- clone this repo (https://github.com/100xdevs-cohort-2/week-15-live-2.2.git)
- npm install
- npm run build
- node dist/index.js
- in db.ts change mongo to localhost
- (mongodb://mongo:27017/myDatabase) to (mongodb://localhost:27017/myDatabase)
- rebuild
- before starting the project run this cmd in terminal (docker run -p 27017:27017 -v mongo_db_data:/data/db mongo)
- node dist/index.js (it says "MongoDB connected")

- (containerzing node index.js)
- now let's built it using docker
- docker build -t users-app .
- docker run -p 3000:3000 users-app
- but mongodb not connected
- beacauuse mongdb is not running on this mini machine, it is running on different mini machine
- how can I talk to one docker container from another container (using networks)
- Networks is useful when we want multiple docker container talk to each other
- we'll connect both the container by the same network and will give a container name

# how to make containers talk to each other
- create a network
- docker network create node_app_network
- docker network ls
- now when I am starting mogodb, I'm connecting it to this network that we just made (node_app_network)
- docker run --name mongodbcontainer --network node_app_network -p 27017:27017 -v mongo_db_data:/data/db mongo
- now in te source code replace the name of the container to localhost
- mongodb://mongodbcontainer:27017/myDatabase
- now build
- docker build -t users-app .
- docker run --network node_app_network -p 3000:3000 users-app (if the port is already allocated kill the previous container)

- we didn't named node container because node needs to find mongodb, mongodb does not need to find node 

``` Dockerfile
FROM node:22-alpine

WORKDIR /app

COPY ./package.json ./package.json
COPY ./package-lock.json ./package-lock.json
RUN npm install

COPY . .

EXPOSE 3000

CMD ["node", "index.js"]
```