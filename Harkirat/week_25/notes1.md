slide: https://sargam.notion.site/Intro-18d82f1740e4808c8572de2b8c36d60e

# Process management
- keeps a process running untill stopped explicitely
- if server stops, it automatically restart the server

(pem file is a key to your aws instance)

- even if I kill the app, by using pm2 app would still be running
- pm2 will take care of the instance and whatever is running will be running, if it crashes then you'll have to restart

(curl localhost:3000) -> run this after killing the process
- we kill the process using pid (process id)
- curl is like a postman but for our terminal
- lsof will show us what is running on what port (gives a pid for a particular port)

- pm2 starts the app and whenver the app crashes, it restarts

# CI/CD
- read about linting
- CD is deploying the code 

-echo means console.log only

- use cursor 
- check kirat's notion doc on ci/cd from project.100xdevs

- github actions is a way to write CI/CD pipelines (others are jenkins and azure pipelines)

*** yt video ***
- https://www.youtube.com/watch?v=G1u4WBdlWgU&t=61s
- CI/CD is a way to make software safer, faster and efficient by streamlining and automating process like building, testing and delivering of the software

- deployment without CI/CD:
1. development phase
2. Compilation phase: compile the code to create a build (a build is something which has code along with dependencies and libraries which runs the software, android code has .apk as a build, java has .jar)
3. Testing phase
4. Deployment phase