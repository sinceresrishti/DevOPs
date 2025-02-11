# creating a monorepo
- npx create-turbo@latest (or)
- npx --yes create-turbo@latest
- Where would you like to create your Turborepo? (./my-turborepo) (bms, book my show)
- npm install -g pnpm (add sudo if not installing)
- pnpm is a package manager similar to npm (so as yarn, bun)
- open bms in vs code
- we have two nwxt apps (web and docs, I need only one so get rid of docs)
- add add http-server and ws-server (web socket)
- add prisma inside packages
- go to prisma and initialize package.json and tsconfig.json
- npm init -y (to add package.json) and make some changes, name: @repo/db
- npx tsc --init (add this to tsconfig.json) -> 
{
  "extend": "@repo/typescript-config/base.json"
}
- add devDependencies to package.json
"devDependencies": {
    "@repo/typescript-config": "workspace:*"
  },
- only * if using npm
- now we have to add prisma as a ependency in prisma folder
- pnpm add prisma
- npx prisma init (will create prisma folder and inside it schema.prisma)
- add User model to schema.prisma

- what are the next steps: migrating the database, generating the clients
- I need a database to connect to jaha pe mai ye users table banaungi
- you can get a fresh database from neon.tech
- named project as class-testing on neon.tech
- copy the database url and paste it in .env file

- npx prisma migrate dev (named new migration as create_users_table), added a migrations folder inside prisma

- npx prisma generate (to generate my prisma clients)

- we have to export so I'll create a src folder (in packages, in prisma) ans I'll create a index.ts file from where I'll export my prisma client that eill imported over http-server and ws-server

- a client is just a variable taht let's you connect to the database somehow (put things in the database in the easier fashion)

- add a exports section inn the package.json
"exports": {
    "./client": "./src/index.ts"
  },

- now we can import it in next app (in web, in app, in page.tsx)
- web kepackage.json me we'll introduce a new devDependecy ("@repo/db": "workspace:*",)
- now I can use@repo/db in my next.js application (web)

- we have to do a global pnpm install (go to the root folder (bms) and pnpm install)

- my next.js app can now use my prisma package or prisma module

- same thing we've to do with http-server and ws-server

# http-server
- npm init -y
- npx tsc --init
- create src folder

# ws-server
- npm init -y
- pnpm add ws @types/ws (error)


error was coming related to express and ws
- pnpm add -D @types/express
- pnpm add -D @types/ws -w


# tesst server
- npm run dev


# Deployment
- whenever you're working in a company, you'll not have just one main branch, you'll have 3 branches
- dev, staging and production

take examle of 100xdevs.com
- there are 2 branches (main and production)
- when someone pushes the code it merges with main branch and it deploys to staging.projects.100xdevs.com where there is no end user
- and the production branch is the one which deploys to projects.100xdevs.com which we use
- once a week they merge the main and production branch and production branch will deploy to projects.100xdevs.com
- why this done? because main branch pe evry hour someone is commiting and if there is any bug it'll be delpoyed to a closed url not on the production and after testing we can merge and production will auto deploy

* next steps:
- create 2 servers
- add node, nginx to both the servers
- clone the monorepo to both the servers
- start 3 processes (next, ws and http)
- Point our Domain names to the respective servers
    week-25-http.100xdevs.com
    week-25-ws.100xdevs.com
    week-25-fe.100xdevs.com

    staging.week-25-http.100xdevs.com
    staging.week-25-ws.100xdevs.com
    staging.week-25-fe.100xdevs.com
- refresh nginx config
- test that everything is working

# you should never deploy manually, you never ssh into your machine ever
- we are going to deploy it manually but this bad, you should never do this
- Noo developer should ever ssh into a machine even if something is wrong, you should have remote login and you see the log somewhere else, you should neve ssh into a machine but today we're doing this

# difference b/w dev, staging and prod
* dev: whatever is getting pushed to master is reaching dev
* staging: staging is for testers usually
* prod: real application that your users are using

