srish11@fedora:~/Downloads$ chmod 700 srishti.pem
srish11@fedora:~/Downloads$ ssh -i srishti.pem ubuntu@54.234.216.194

slide: https://projects.100xdevs.com/tracks/g0AcDSPl74nk45ZZjRdU/aws-1

# vim cmd (to edit)
vi index.js
exit without saving -> esc :q! and then enter
exit with saving -> esc :wq! and then enter

# how to deploy a backend project

- node does not come by default in ubuntu
- git come by default in ubuntu
which is why git clone I am able to do but npm install I am not able to do

- follow the blog post to install node on the ubuntu machine (or follow the following cmd)
- curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash (this cmd will get those content and bash will pipe it into my terminal)
- source ~/.bashrc

or go over this url copy the whole thing and paste it into your terminal
- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh

- nvm install --lts (but it's good to not install lts because there might be some bugs)

- vi index.js
- if I got to end this is running on port 8080 but hamne to port 3000 khola tha

- click on instance, go to security tab, open the security grp, change the inbound rule, edit the inbound rule, or add another rule
- port 8080 should be accessible from anywhere IPv4 and it's a good idea that it should be accessible from anywhere IPv6 as well (not needed though), save rules

- now we can go to the ip (public) and our express server is running (start the server from terminal only then it will work, index.js)
- http://54.234.216.194:8080/todos

- can you send it to your friend, can you start marketting it?
- No, we have to attach a domain name to it (but internet pe deploy ho gayi haiif you go over here you will see it (internet facing application))

# how to deploy a frontend project
- clone a react project
- npm run build
- npm run start


# nginx 
- pronounce engine-x
- why are we introducing nginx
    - because there is ugly port (google.com does not has a port, our website have aport)
    - google.com uses port 443 but I don't have to speciy it because it is using https (shuru me https hai mtlb, end me 443 hai, dalne ki zarurat nhi hai)
    - our website is hosted on http (port 80)
    - if I run my application on pport 80 then I don't have to specify port 80  (http://ec2-54-234-216-194.compute-1.amazonaws.com/todos)
    - rather than starting the project on port 3000 or 8080 or .... start it on port 80

- port 80, 443, 20, telnet(13) -> the os prevents anyone from starting anything over there
- you can't run node index.js on port 80
- if you give node some very heavy access then it'll be able to start something on port 80  par abhi to nhi chal rha hai

- even if you deploy it on port 80 somehow, there is another problem
-multiple process can not run on the same port (eg. sellclothes.com and sellshoes.com can't run on port 80 together)

# VPN kya karta hai
- me in India can connect  to vpn in japan and then all I see is blur videos
- you select what location I want to go to or proxy through so that mit.com thinks that the request is coming from japan
- if you ever stated a vpn and visited yt aapko vha ki ads aane lag jayengi because yt thinks  request is coming from US
- this is forward proxy
- state.com is a good example, go to state.com nhi khulega, start a vpn, vpn from US, state.com khul jayega (because state.com will think ki US se request aa rhi hai butu actual me request is coming from India)

# Reverse Proxy
- eg. sellclothes.com is hosted on port 3000 and sellshoes.com is hosted on port 30001
- now nginx will say say I am hosted on port 80 and I will send the request to 3000 or 3001 based on user's request
- this reverse proxy
- port 80 pe the process i.e running is forwarding the request either over 3000 or 3001 (to a diff. process based on url kya hai)
- what is reverse proxy, incoming request aayi based on the url either it went here or here
- I don't have money to buy multiple servers to ek bada server kharid liya

- nginx is a reverse proxy

ugly looking url ko pretty banane ke liye we were hosting it on port 80 but we can't do that
- so I'll start nginx on port 80
- a very popoular reverse proxy on port 80

# cmds to start nginx
- sudo apt update
- sudo apt install nginx

- if you run these cmds nginx server will start running on port 80

- sudo nginx -s reload (just to confirm)

- nginx has started running but since I haven't open port 80 I'm not able to send request there (so open port 80)

- http://ec2-54-234-216-194.compute-1.amazonaws.com/  (kuch to chal gya, Welcome to nginx)

- user should not be able to hit 8000, user should not be able to hit 8001, user should only be able to hit 80

- you need to have domain name
- and the configure nginx

- certificate management -> move from http to https

## ASSIGNMENTS ##
- get a gcp account and do this there
- replace nginx with traefic/HAproxy/Apache (some other reverse proxies)
- try deploying a react app
- get a domain name (namecheap)
- try ASGs
- try to do cert management yourself
- create a CI/CD pipeline to auto deploy to your server from GH
- read about forever or pm2 (process management)
(these are heavy assignments)

- load balancer
- rolling update