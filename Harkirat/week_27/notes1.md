run an image
- docker run image_name

what we'll learn today:
1. Docker Compose
2. create a monorepo and write a CI/CD pipeline to deploy

# Docker-Compose
- we rarely use this in deployment (we use it jab aap locally project bna rhe ho)
- docker-compose.yml file
- if yml file is hard to read, convert it to json
- whenever you're stating a db container, it is a good idea to mount it to volume so that jab db stop ja jaye still hamare pass data rhe db me

https://github.com/processing/p5.js-web-editor
- installation.md me sabhi cmds hai install karne ke (docker insalltion)
- docker-compose-development.yml (check this file in the above repo)

- docker-compose let us run multiple containers together

- if we define different services or containers they are autommatically connected to the same network using docker compose

- let's start with a simple backend project that connects postgress via prisma

# dockerCompose-week27
- dockerCompose-week27 (fresh folder)
- npm init -y (to create package.json)
- npm i typescript (to create tsconfig.json)
- npx tsc --init
- int tsconfig.json change the rootDir to "./src" and the outDir to "./dist"
- create a src folder, index.ts file
- this is a simple express project that connects to a prisma server
- npm install prisma express @types/express
write some code in index.ts file
- npx prisma init (initialize prisma folder and schema.prisma file)
- add a basic user model in schema.prisma
- docker run -e POSTGRES_PASSWORD=mysecretpassword -d -p 5432:5432 postgres
- change the credentials in .env file
- DATABASE_URL="postgresql://postgres:mysecretpassword@localhost:5432/postgres"
- and if all of this is complicated go to neon.tech, create a database url and paste it over here
- npx prisma migrate dev (migrations files gets generated)
- npx prisma generate (to generate the client)
- add code to index.ts
- forgot to add a build and start script in package.json
- contribute.md
- Dockerfile
- docker-compose.yml
- we have to add networks because we are starting postgres separately and image seperately
follow the steps of docker installation

*** start from 1:30 ***

# cloning the harkirat's repo
- week-27-docker-compose
