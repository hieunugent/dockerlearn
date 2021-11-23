# dockerlearn
## Get Start
- create a new file call Dockerfile
- we need a base image to run the app
- in this example using latest debian image
- or using node.js image
```docker:
 FROM node:latest
 
 RUN mkdir -p /app/src
 
 WORKDIR  /app/src 
 
 COPY package.json . or /app/src
 
 RUN npm install
 
 COPY . .  # is the current directory to destination current directory
 
 EXPOSE 3000 # in order to see app in browser
 
 CMD ["npm", "start"]
```
- this will build docker image
- using docker command to build docker image
```command
docker build . -t  nameofimageapp # build image
#  find image
docker images
3 run image
docker run 

```
- in VS CODE extension run it on click
