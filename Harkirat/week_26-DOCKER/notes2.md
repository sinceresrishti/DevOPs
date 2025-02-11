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