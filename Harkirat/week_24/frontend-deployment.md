- open aws account and search for S3 then cloudfront
- quickly creating a react project (create a folder name react-deployment and project name is react-app (react-app2))
- npm install
- npm run dev
- npm run build (to convert to html, css, js)
- even if you delete everything except dist, this is enough (dist is what you need to distribute over internet)
- npm install -g serve
- cd dist (go to dist folder)
- serve (serve is used to preview the production build of a React app. It runs a simple web server for static files in the dist/ folder. Use serve -s . to ensure React routes work correctly.)

# start deploying
- create a bucket in s3
- open dist folder and drag and drop (xdg-open)
- or manually upload the files inside dist folder
- our bucket is blocked by default (it should always be blocked), cannot be opened via public

- you dont't want data to be distributed via s3, its very expensive, its very slow because every request is going directly to the s3
- you want to distribute this via cloudfront

- go to cloudfront and create a new distribution
- in origin access select recommended one (create a fresh OAC)
- enable security protections
- default root object (index.html)

- copy the policy to permissions (bucket policy)

- got this url after deployment
- https://d3s4oc1i3hvajh.cloudfront.net/

- have to make it look better 
- go to alternate domain names and edit
- add item (week24react.lostpika.online)

- if you want your website to be hosted on https. Create a custom SSL certificate 
- click on request certificate
- ACM creates the certifiacte (AWS Certificate Manager, its a service )

- now verify that you own this domain name
- go to the website from where you have bought the domain name 
- go to dns
- manage custom records
- add a new record
- add cname, cvalue, type

- after successfully generating SSL certificate when I go to http://week24react.lostpika.online/ it says week24react.lostpika.online’s DNS address could not be found. Diagnosing the problem.
DNS_PROBE_POSSIBLE

- because I have not yet pointed week24react.lostpika.online to the cloudfront url (https://d3s4oc1i3hvajh.cloudfront.net/)

- add a dns record (cname record)

- add a error page from cloudfront
- create invalidation (/*) (to clear cache)

- (added CAA records and allowed amazon to issue certificates)

# trying to deploy it for the second time
- bucket name: react-srish
- https://d36uiqw5xao2w3.cloudfront.net/