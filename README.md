# TO RUN

simple as `docker-compose up`

`docker build -f Dockerfile.dev .`

we can remove `node_modules` from our local bc docker is going to create an image with it (we don't need to duplica dependencies)

get the container id:
```
Step 6/6 : CMD [ "npm", "run", "start"]
 ---> Running in e15c8e3703cc
Removing intermediate container e15c8e3703cc
 ---> f02672a22632
Successfully built f02672a22632
```
`docker run -it -p 3000:3000 f02672a22632`

to run with a volume
`docker run -it -p 3000:3000 -v /app/node_modules -v $(pwd):/app <image_id>`
`docker run -it -p 3000:3000 -v /app/node_modules -v "/$(PWD)":/app 18bf2e115c87`<- This is the correct one
NO colon in one the volume you want to map the file in the container, with : we want to map files in the host to the container

or `docker-compose up`

to run tests:
`docker run -it ed52f509054a npm run test`

to run prod version
`docker build .`
`docker run -p 8080:80 b27bd8240601`